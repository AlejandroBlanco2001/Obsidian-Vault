Tags #javascript #design 

## Context and History

Processing started as an open source programming language by itself (based on Java) to help electronic arts and virtual design to learn computer programming in a visual context.

This gain advantage because of the simplicity provided, rely on just two methods:

- `setup()` for initializing all the required values and variables 
- `draw()` for doing all the actions for rendering

*Processing.js* is the sister project of this programming language, which was made to bring to the web this 2D or 3D models render without the use of Java or his extra plugins. This was all design with the methodology ***your code should just work***.

- Relies on the web brand new HTML5 `<canvas>` tag


## How it work?

>[!NOTE]
>A fun fact is that Processing.js is just one file, that holds ***ALL*** the library information 

With every release the code was cleaned and re-organize around the same object. And his functionality is pretty simple and straightforward.

> It rewrites Processing source code into pure JavaScript, and every Processing API function call is mapped to a corresponding function in the Javascript Processing object

### Unifying Java and JavaScript

If the assumption of transpilation code from Processing to JavaScript was done correct, you can run this on the web browser without any issue. ***But*** the issue is Processing is on Java and the other is on JavaScript.

Initially they approach the problem taking into account that we can treat the Java source-code as long string, and a native replacement was made, it means that we look for a particular function in Java, and replace with the JS equivalent (ctrl+f apporach)

>[!NOTE]
> You can find an initial example of this [here](https://github.com/jeresig/processing-js/blob/51d280c516c0530cd9e63531076dfa147406e6b2/processing.js)
> 

This code was fine for small set of instructions and code, but, what if the code was huge, so, to fix that they built an AST ([[Abstract Syntax Tree]]), first breaking the Java source code into functional blocks, and then mapping each ofthose blocks to their correspoding JavaScript syntax.

>[!IMPORTANT]
>They basically built a trans-compiler, and you can have Java-to-JavaScript code on the go.

This is great, but comes with this trade-off: 

1. Java programs are isolated entities. JavaScript programs share the world with a web page.
2. Java is strongly typed. JavaScript is not.
3. Java is a class/instance based object-oriented language. JavaScript is not.
4. Java has distinct variables and methods. JavaScript does not.
5. Java allows method overloading. JavaScript does not.
6. Java allows importing compiled code. JavaScript has no idea what that even means.

### Significant differences 

#### Java programs have their own threads, JavaScript can lock up your browser.

Java programs are isolated entites, running in their own thread in the greater pool of applications on your system. JavaScript, in the other hand, can just live in your browser.

This means that for normal (or traditional applications), this is ok. But for this use case, we don't hava a way to put JavaScript in some IDLE state, because we don't have threads here.

Thus, they start to have a creative way of thinking, for example, for some things we decided to force synchronous waiting anyway. Loading a file with strings, for instance, a synchronous `XMLHTTPRequest`, and will halt execution of the page unit the data is available.

For many other things, they had to get more creative. Loading images, uses the browser's built-in mechanism for loading images; they build a new `Image` in JavaScript, set its `src` attribute to the image `URL`, and the browser does the rest, and then notify us with an `onload`

You can also know which images you need always, so, they make a directive to preload things.

```javascript
    /* @pjs preload="./worldmap.jpg"; */

    PImage img;

    void setup() {
      size(640,480);
      noLoop();
      img = loadImage("worldmap.jpg"); }

    void draw() {
      image(img,0,0); }
```

To ensure accurate font loading in web pages, the process involves several steps due to the lack of reliable JavaScript events for font load completion. Here’s a summary of the approach described:

1. **Font Loading Challenge**: Unlike images, fonts don’t have robust browser events to indicate when they are fully loaded and ready to use, which can lead to incorrect font rendering.
    
2. **Current Solution**: To address this, a tiny TrueType font containing just the letter "A" with minimal size is embedded in the page using a data URI. This ensures that the font is available almost instantly.
    
3. **Detection Method**: A hidden `<div>` is used to measure the text metrics. Initially, this `<div>` is styled with the desired font and falls back to the tiny font. By comparing the text metrics in the `<div>` with those of the tiny font, the system can determine when the desired font has loaded and is being used correctly.
    
4. **Polling**: The system polls at regular intervals until the desired font metrics are detected, ensuring proper font rendering.

### Java is strongly typed, JavaScript is not.

Nothing to explain, `2` and `2.0` are not the same in Java, but in JavaScript they are, so this can arise fun bugs. And the thing is, they didn't solved because an issue never was raised regarding this problem.
### Java is OOP, with packages, namespaces, JavaScript is not

JavaScript is `prototype` based, it means that all in the end is just a big object with key-value pairs to primitives, functions or other objects. Therefore, they don't have concepts as `superclass` or `sublcass`.\

The approach was to implement old classical Java inheritance on JavaScript and most important, should be fast. Also, you should have into account don't override things that have the same name, for example, `Object.line = "some value"` and `Object.line = function(x1, y1, x2, y2)`

For the second case, it was too complex, therefore, they suggest to don't do this.

> [!IMPORTANT]
> If we suggest a way to write code, and  that's the proper one, some issues would never happen

Other reason, was to not break the way JavaScript work.

### Java allows method overloading, JavaScript does not 

Java allows to perform overloading in the methods, such as 

```java
public int add(int a, int b) {}

public int add(int a, int b, int c) {}

public float add(float a, float b, float c) {}

```

And when you call them, he will know by the number of parameters used (and their type), which one it should use.

This is because in JavaScript, each function is a property, therefore, you can deference it. If you define a function `add(x, y)` and then call it as `add(1, 2, 3, 4, 5, 6)`. JavaScript is okay with that, he will say `x=1` and `y=2` and ignore the rest of the world. So, this will happen

```javascript
function add(a,b)

function add$2(a, b, c) {}
```

For other special cases, they check the `instanceof` and the `typeof` to solve the issue with same number and different types.

### Java allows importing compiled code

Plain Processing code is not always enough, in Java you can use pre-compiled Java code in the form of a `.jarchieve`

Java compiled code is Java byte code, so the question is, ***how do we support library imports without writing a Java byte code de-compiler?***

The decided, to just enable the same API for Web devs, so the quick answers, it was, they just allow to build your library on JavaScript and call it with the `import` keyword.


## Why JavaScript, if I can do Java?

You need to install Java, their plugins and dependencies, while, JavaScript comes with every web browser in the world. Is already there

JavaScript ***can do everything*** that Java does, but with the cost of *speed*

>[!IMPORTANT]
>This is because the JavaScript programming language is a [[Turing-complete language]]

For example, why not to make a proper parser and compiler to do this? And why he used a regular expression match and replace?

The answer was

> It was important to him that people be able to mix Processing syntax (Java) and JavaScript without having to choose between them.

If you don't need it, don't do it.

Has become an exceptionally versatile library for web-based data visualization, media presentation, and even games. It supports:

1. **Cross-Platform Flexibility**: It works with both native Processing sketches and those that mix Java and JavaScript, or use pure JavaScript, effectively functioning as an advanced canvas drawing framework.
    
2. **Broad Adoption**: The library's ability to integrate with JavaScript has led to wide adoption by major companies like IBM and Google for various web projects.
    
3. **Innovative Usage**: Its design allows it to be combined with other JavaScript-based tools, like CoffeeScript, enabling developers to create interesting and unique results.
    
4. **Widespread Impact**: By converting Processing's Java syntax to JavaScript rather than interpreting Java directly, Processing.js has expanded Processing's reach on the web, demonstrating its broad utility and adaptability in the web development community

## Components

Inside the one large file, there are 3 components:

1. Launcher
2. Static functionality
3. Sketch functionality 

### Launcher

This one does this three things:

- Code pre-processing
- Code conversion
- Sketch execution

#### Code pre-processing

They separate the code from the directives, and they then run all the directives.

#### Code conversion

The source code is turn into an [[Abstract Syntax Tree]] nodes, such as statements, expressions... This [[Abstract Syntax Tree]] then is expanded to JavaScript source code that build a sketch-equivalent program when executed.

#### Sketch execution

This final step consist of determine whether or not all pre-loading has finished. After this is finished, the `setup` and `draw` method are called\

### Static Library

- - **Global Constants and Functions**: Defined once in the `Processing` object for efficiency, including constants like key codes and color mappings.
    - **Complex Data Types**: Includes custom objects like `PShape` for shapes, `PShapeSVG` for SVG handling, `XMLElement` for XML, `PMatrix2D` and `PMatrix3D` for matrix operations, `PImage` for image resources, and `PFont` for font resources.
    - **Drawing Functions**: Organized into `DrawingShared`, `Drawing2D`, and `Drawing3D` to optimize performance by binding relevant graphics functions based on the mode (2D or 3D).
- **Custom Implementations**:
    
    - **SVG and XML**: Custom parsers are used for `PShapeSVG` and `XMLElement` to avoid unused code and optimize performance.
    - **Fonts**: `PFont` loads and caches font metrics from the browser, managing memory by clearing caches when needed.
- **Data Structures**:
    
    - **ArrayList and HashMap**: Implementations that emulate Java's data structures. Custom "virtual equals" and "virtual hashCode" functions are used to handle JavaScript object comparisons and hashing, replicating Java’s behavior.
- **Administration**:

    - **Sketch Management**: Maintains a list of active sketches on the page, allowing users to interact with specific sketches using their canvas IDs.

### Sketch functionality

In Processing.js, instance code is written as `p.functor = function(arg, ...)` for API functions and `p.constant = ...` for sketch state variables, where `p` refers to the specific sketch instance. This code is organized by function type, with related operations placed near their relevant objects like `PShape` or within `Drawing2D` and `Drawing3D`.

To enhance performance, some functions that could be static are implemented as instance functions. For example, `lerpColor(c1, c2, ratio)` is defined as an instance function rather than as a static wrapper. This approach reduces execution time at the cost of increased memory usage, as the functions are optimized for speed by being directly associated with the instance.


## Human approach to Processing.js development

### Make It Work

> Make it work, and when you're done, prove it.

To have a fast pace development, and moving things without breaking anything else, you must have tests all over the place.

Every ticket, that creates new code or modify old code, must have test associated to them, once the test are done, the development is done.

The test should cover, all the cases, when it works and when it fails. They also have reference test (automated test basically) for drawing and checking the visuals of the application. 

### Make it Fast

> If you can't measure it, you can't improve it

They have performance test all across the code-base, they just run the code:

- Without checking the output
- Several hundred of times in a row
- Run against a special performance page

In this way, they measure how well (or not) was Processing.js was doing with every change in all the browsers that support `<canvas>`

Is not just make the code faster, is also take advantage of the tools that the browser expose to use to make it faster.
### Make it small

There are two ways of making the code smaller:

- Write compact code
	- If you manipulate a thing multiple times, do it once (if possible)
	- If you access an object value multiple times, cache it
	- Return things once you have all the information
This 
```java
if ((result = functionresult)!==null) {
  var = result;
} else {
  var = default;
}
```

turns into

```javascript
var = functionresult || default
```

- Runtime optimization
- Minification

###  If everything fails, tell People

There are things that sometimes the environment don't allow us, for example, in the browser world we have Security rules to avoid use a USB or serial port as I/O, saving files to hard disk, and we also have limitations of the language such as float math in JavaScript.

> [!NOTE]
>  All the tickets that have a 'wont fix', have a a documentation inside the code the give context, if anyone ask again why.

## Key points

- When porting something, we don't have to worry about to make it look exactly as the port, just to work like the port.

- You only need to worry about how to exploit your environment and the language you use.

- Return fast, when you have all that you need, return it

- Testing is crucial, testing is the bedrock of agile development, this ensure the following:
	- Write code against the tests
	- Create tests before writing code
	- Start creating the test based on the functionality, instead of what we see

- Agile development also applies to hot-fixes.
	- Present fixes early
	- Update often
	- Work feedback

