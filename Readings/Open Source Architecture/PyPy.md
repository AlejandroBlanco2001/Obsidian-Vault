Tags #python #compilers #design 

## Context and history

> Python is a high-level, dynamic programming language

Initially started as a traditional bytecode interpreter written in C, this is known nowadays as ***CPython***. 

>[!IMPORTANT]
>There is more than one variation of this, such as JPython (Java), IronPython (C#) and PyPy

### Overview

This variations is written in Python, this only have two major components:

- Python interpreter (Written in RPython)
- RPython translation toolchain

>[!NOTE]
>RPython means Restricted Python

His abstracted nature allows us to have more than *200 possibles configurations!!*

## The Python interpreter

If we remember, RPython is just a small strict subset of Python, therefore, we can use this code in any Python implementation. The major trade-off is that is extremely slow.

This provide us a way to ensure that untranslated and translated code works the same, in both cases.

CPython and PyPy have a lot alike:

- Data structures
- Bytecode structure

The main difference is the abstraction called ***object spaces*** (objspaces). This object holds all the needed information to represent and manipulate data types

This Python objects become black boxes for the interpreter, and calls objspaces methods wherever it needs to manipulate them

```python
def BINARY_ADD(space, frame):
    object1 = frame.pop() # pop left operand off stack
    object2 = frame.pop() # pop right operand off stack
    result = space.add(object1, object2) # perform operation
    frame.push(result) # record result on stack
```

This is a huge advantage, because allows us to play with them (swap, delete, move) without worrying if the interpreter knows how to handle them. 

>[!IMPORTANT]
>Thunk is not to calculate a thing directly, but instead create a function with zero arguments that will calculate our value. And  tainting is the process of validate something through asserts

The vanilla PyPy interpreter objects are called std objspaces (stndard objectspace), this provides a new thing: ***A single data type may have multiple implementations***

For example, we can swap long numbers and int numbers, without any issue, making a small int from that long value.

The interpreter knows how to distinguish between interpreter level (interp level) and application level (app-level) code. The first one must be written in RPython and it's translated.

The other one is run by the PyPy bytecode interpreter, but you can use this one in the other level.

## The RPython Translator

Is a set of steps that translate our RPython code to another language, usually C. This is written in normal Python.

![[Pasted image 20240821154726.png]]

The first step is load  the RPython program into its process. A few of the restricions of are:

- Functions cannot be be created at runtime 
- Single variables cannot have the possibility of holding incompatible types

Even though the at first the code is loaded as Python, the PyPy interpreter, a huge RPython program, makes heavy use of this feature for meta programming.
- Generates code for standard objects multi method dispatch

The translator start building flow graphs through a process called ***abstract interpretation***, This reuses the PyPy Python interpreter to interpret RPython programs with a special objspace called the *flow objspace*.

This one only have two objects: variables and constants. Variables represent values not know during translation, and constants the known values.

```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)
```

![[Pasted image 20240821155543.png]]This flow graph then is ***annotated***, to assign a type to to the results and arguments of each operation.

After that, the ***RTyping*** phase starts. this use the information provided by the previous step to expand each high level flow graph operation into low level ones. The backend matters, for now, we have two types:

- A low level typesystem for backends like C
- A high level typesystem with classes.

Python code typically has frequent dynamic memory allocations. RPython, being a Python derivative, inherits this allocation intensive pattern. In many cases, though, allocations are temporary and local to a function. _Malloc removal_ is an optimization that addresses these cases. Malloc removal removes these allocations by "flattening" the previously dynamically allocated object into component scalars when possible.

```python
def distance(x1, y1, x2, y2):
    p1 = (x1, y1)
    p2 = (x2, y2)
    return math.hypot(p1[0] - p2[0], p1[1] - p2[1])
```
After being RTyped
```python
v60 = malloc((GcStruct tuple2))
v61 = setfield(v60, ('item0'), x1_1)
v62 = setfield(v60, ('item1'), y1_1)
v63 = malloc((GcStruct tuple2))
v64 = setfield(v63, ('item0'), x2_1)
v65 = setfield(v63, ('item1'), y2_1)
v66 = getfield(v60, ('item0'))
v67 = getfield(v63, ('item0'))
v68 = int_sub(v66, v67)
v69 = getfield(v60, ('item1'))
v70 = getfield(v63, ('item1'))
v71 = int_sub(v69, v70)
v72 = cast_int_to_float(v68)
v73 = cast_int_to_float(v71)
v74 = direct_call(math_hypot, v72, v73)
```

This code is suboptimal in several ways. Two tuples that never escape the function are allocated. Additionally, there is unnecessary indirection accessing the tuple fields.

```python
v53 = int_sub(x1_0, x2_0)
v56 = int_sub(y1_0, y2_0)
v57 = cast_int_to_float(v53)
v58 = cast_int_to_float(v56)
v59 = direct_call(math_hypot, v57, v58)
```

## JIT

>[!IMPORTANT]
>The flexibility is a trade off with the interpretation, PyPy vanilla compiler is 4 times slower than CPython

PyPy has a JIT (Just-in-time) compiler to be faster. This is a ***tracing JIT***, this means, it detects "hot" loops to optmize by compiling to assembly. When the JIT has decided it is going to compile a loop, it records operations in one iteration of the loop, a process called ***tracing***.

The JIT generator requires only two hints in the interpreter to generate a JIT:

- `can_enter_jit`: Tells the JIT where in the interpreter a loop starts
	- JUMP_ABSOLUTE bytecode reached
- `merge_point`: Tells the JIT where it is safe to return the interpreter from the JIT.

This step is called after the ***RTyping phase***, in this step we check the flow-graphs of low-level operations looking for the *hints*, then we serialize this steps of the flow graph as *jitcodes*, and this ones are saved in the final binary for use at runtime.

At runtime, JIT keeps a counter for every for-loop that is executed, when that threshold is passed, the JIT is invoked and tracing begins. This is done by the meta-interpreter, who execute the *jitcodes*.

The meta-interpreter in a JIT (Just-In-Time) compiler specializes in tracing loop iterations by making decisions based on runtime information. It records "guards," which are assumptions about the program's state, ensuring the generated assembly code runs only in the correct context. The tracing ends when the same `can_enter_jit` operation is encountered, and the trace is then optimized.

Two key optimizations in the JIT are **virtuals** and **virtualizables**. **Virtuals** are objects that stay within the trace, allowing their data to be stored in registers or on the stack, avoiding memory allocation. **Virtualizables** are similar but can escape the trace, requiring special handling to ensure external functions interact correctly with them.

After optimization, the trace is converted into assembly code. This process is relatively straightforward due to the low-level nature of the JIT IR, although challenges like garbage collector (GC) integration and guard recovery complicate it. Guard recovery involves reconstructing the interpreter state when a guard fails, using a "blackhole interpreter" to handle the complex transitions.

This process ensures that the JIT can efficiently execute dynamic languages like Python while maintaining correctness through guard mechanisms and recovery strategies.

![[Pasted image 20240825195556.png]]

## Design drawbacks

RPython is ***hard*** and would beat C any day, but is almost impossible to write things on it. 

There are also practical problems such as, making a small change in the translated code requires retranslating the entire interpreter (40 minutes on a fast system)

The abstractions is good and the theory is good, but in practice somethings with the JIT don't work, and they required more hints.

The many layers of abstraction, make the bugs really really hard to track. Sometimes we need to read unreadable C code and compile it in GDB to track things.

The only things that is harder to do is, using RPython (a subset restricted Python) to translate to C. This makes the translator to have a lot of cross-dependencies 

## Agile 

To manage its complexity, PyPy adopts agile development methodologies, with **test-driven development** being the most significant. All new features and bug fixes require tests, and PyPy's interpreter is regularly tested against CPython's regression test suite. PyPy uses its test driver, **py.test**, and runs continuous integration, including daily platform builds and benchmark tests, ensuring stability across its complex architecture.

PyPy promotes a strong culture of **experimentation**, encouraging developers to work on branches in its Mercurial repository. Many ideas are refined this way, though some branches are abandoned. Notably, the current PyPy JIT is the result of several iterations, demonstrating the developers' perseverance.

Additionally, PyPy prides itself on its **visualization tools**, such as flow-graph charts, garbage collector invocation tracking, and parse tree viewers. Of particular interest is **jitviewer**, a tool that visualizes the different layers of jitted functions, helping developers better understand the interactions within PyPy's architecture.

![[Pasted image 20240825200558.png]]

## Key points

- Refactoring and refactoring and more refactoring is essential
- Abstraction is powerful but comes with mental costs
	- They need to be in the right spot
	- + abstractions = slow program
	- Bugs can be clouded by abstractions
	- Abstraction leaking (We need to break the abstraction to prevent things
- RPython as a implementation languages, makes playing with Python really fun. Give yourself room to experiment