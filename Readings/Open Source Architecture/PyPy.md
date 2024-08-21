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

![[Pasted image 20240821155543.png]]