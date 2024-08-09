Keywords: #OOP #C #design 
Lecture available: [here](https://aosabook.org/en/v1/cmake.html)

## Before CMake

- When a desktop app was developed we need to generate two things:
	- Makefiles* for Unix
	- Visual Studio for Windows

>[!NOTE] A Makefile is a set of rules to determine which parts of a program need to be recompile, and issues command to recompile them.

- Just before the CMake, there was two alternatives:
	- VTK (1999)
		- Configuration script for Unix and executable file called ***pcmaker*** for Windows, this was a C program that read in Unix Makefiles and created NMake files for Windows
		- The binary executable for ***pcmaker*** was checked into the VTK CVS system repository.
	- gmake (NS)
		- This was a variation of Makefiles for TargettJr.
		- This need a LOT of environment variables to be set prior to running gmake
		- Hard to debug once failed.
- Both shared a few issues that can be crucial:
	- Windows developers were forced to use the command line
	- Windows developers prefer IDEs
		- This will encourage Windows developers to create IDE files, causing the double system problem, again...

>[!NOTE] TargetJr was a C++ computer vision environment originally developed on Sun workstations.
### Rules for CMake

After a long discussion, the developers set a basic set of constraints of the new build system:

- Depend only on a C++ compiler being installed on the system.
- It must be able to generate Visual Studio IDE input files.
- It must be easy to create the basic build system targets, including static libraries, shared libraries, executables, and plugins.
- It must be able to run build time code generators.
- It must support separate build trees from the source tree.
- It must be able to perform system introspection, i.e., be able to determine automatically what the target system could and could not do.
- It must do dependency scanning of C/C++ header files automatically.
- All features would need to work consistently and equally well on all supported platforms.

The only restriction was that we need the C++ compiler (which we can safely assume we have if we're building C++ code...)

The ability to generate IDE project files is a strong selling point for CMake, but it also limits CMake for providing only the features that the IDE can support natively.
- This take the best advantage of their most important resource: the developer.

CMake allowed the user to not focus on the building blocks of the software (Executable, static libraries, shared libraries, and plugins), instead with one command you can get all of them for Windows, Unix and Mac

>[!IMPORTANT] This ability allows developers to focus on the project rather than on the details of how to build a shared library.

CMake was made for cross-platform development, therefore, they must give the developer the tools to perform an introspection around the system. The developer is focused just in the canonical system rather than the specific system.

For example, code like this:

```cmake
#ifdef linux
// do some linux stuff
#endif
```
Is more brittle than code like this:
```cMake
#ifdef HAS_FEATURE
// do something with a feature
#endif
```

## How CMake is implemented?

### Process
We can say that CMake has two steps:
1. Configure: Process all the input given to it and creates an internal representation of the build to be performed 
2. Generate: The build the files are created
#### Environment Variables (or Not)
It's a common practice (even nowadays) to have environment variables used for building a project.

>[!NOTE] Commonly the projects have a PROJECT_ROOT environment variable that points to the location of the root of the source tree

The major issues is that those variables need to be set each time a build is performed.

To solve this problem CMake made an cache file for the build with those variables, called ***CMakeCache.txt*** which stores all the persistent variables. And this will be store in the the build tree, therefore, available for CMake each run.

#### Configure step
1. Search for ***CMakeCache,.txt***
2. It then reads the file ***CMakeLists.txt***, and parse that with the CMake language parser.
	1. Then executes the command in that file (with the use of the [Command pattern](https://refactoring.guru/design-patterns/command)object (Read more about this pattern in [[Command pattern]] )
	2. Extra files like this can be parsed during this step by the `include` and `add_subdirectory` CMake commands.
	
>[!IMPORTANT]  CMake has a C++ object for each of the commands that can be used in the CMake language. Some examples of commands are `add_library`, `if`, `add_executable`, `add_subdirectory`, and `include`. In effect, the entire language of CMake is implemented as calls to commands. The parser simply converts the CMake input files into command calls and lists of strings that are arguments to commands.

The configuration step is basically running the user CMake code, after all this is done, CMake has an in-memory representation of the project to be built.  

>[!IMPORTANT]  This will include all of the libraries, executables, custom commands, and all other information required to create the final build files for the selected generator

#### Generation step
This step just create the build files for the target specified by the user. The previous internal representation must be generic as possible, to be able to shared between different built tools. 

![[Pasted image 20240701184627.png]]

### The actual CMake code

CMake is an object-oriented system using inheritance, design patterns and encapsulation. 

![[Pasted image 20240701184727.png]]

The results of parsing each `CMakeLists.txt` file are stored in the `cmMakefile` object. In addition to storing the information about a directory, the `cmMakefile` object controls the parsing of the `CMakeLists.txt` file. The parsing function calls an object that uses a lex/yacc-based parser for the CMake language. Since the CMake language syntax changes very infrequently, and lex and yacc are not always available on systems where CMake is being built, the lex and yacc output files are processed and stored in the `Source` directory under version control with all of the other handwritten files.

Another important class in CMake is `cmCommand`. This is the base class for the implementation of all commands in the CMake language. Each subclass not only provides the implementation for the command, but also its documentation. As an example, see the documentation methods on the `cmUnsetCommand` class:

```C++
virtual const char* GetTerseDocumentation()
{
    return "Unset a variable, cache variable, or environment variable.";
}

/**
 * More documentation.
 */

virtual const char* GetFullDocumentation()
{
    return
      "  unset(<variable> [CACHE])\n"
      "Removes the specified variable causing it to become undefined.  "
      "If CACHE is present then the variable is removed from the cache "
      "instead of the current scope.\n"
      "<variable> can be an environment variable such as:\n"
      "  unset(ENV{LD_LIBRARY_PATH})\n"
      "in which case the variable will be removed from the current "
      "environment.";
}
```

#### Dependency Analysis

CMake has strong tools to analyze dependencies in Fortran, C, and C++ source files. However, when using an Integrated Development Environment (IDE), CMake skips this step because IDEs already manage file dependencies. Instead, CMake generates a file that the IDE can understand and use, allowing the IDE to handle file dependencies. CMake also converts the project's dependency information into a format that the IDE can use.

For Makefile-based builds, CMake is in-charge of all the dirty work for dependency.

Even though the end-user don't need to know how this is handle by CMake, you can take a look into this files:

- `depend.make`:  stores the dependency information for all the object files in the directory
- `flags.make`: contains the compile flags used for the source files of this target. If they change then the files will be recompiled
- `build.make` : If a dependency for a target is out of date then the depend information for that target will be recomputed, keeping the dependency information current
- `DependInfo.cmake`:  is used to keep the dependency information up-to-date and contains information about what files are part of the project and what languages they are in


### Evolution of the CMake tooling

They built a few more tools in the future to allow the developers to have more robust tooling for they software, for example:

- CTest: Is used to run regression tests
- CPack: Is used to create installers for project
- CDash: Is to visualize important information about the application on a web browser for developers (build errors, compiler warning)

But this is a set of separate tools, but not for basic building

A project can easily create tests for CTest to run with the `add_test` command. The tests can be run with CTest, which can also be used to send testing results to the CDash application for viewing on the web. CTest and CDash together are similar to the Hudson testing tool. 

- They do differ in one major area: CTest is designed to allow a much more distributed testing environment. Clients can be setup to pull source from version control system, run tests, and send the results to CDash. 
- With Hudson, client machines must give Hudson ssh access to the machine so tests can be run.

CPack works much like the build part of CMake: it interfaces with other packaging tools. For example, on Windows the NSIS packaging tool is used to create executable installers from a project. CPack runs the install rules of a project to create the install tree, which is then given to a an installer program like NSIS. CPack also supports creating RPM, Debian `.deb` files, `.tar`, `.tar.gz` and self-extracting tar files.

 This process is known as continuous integration testing. It ensures that every time new code is added to the CMake repository, it is automatically tested on all platforms supported by CMake. Since CMake supports many different compilers and platforms, this testing system is crucial to maintain a stable build system.

For instance, if a new developer wants to add support for a new platform, they are first asked if they can provide a nightly testing setup for that system. Regular testing is essential to ensure new systems continue to work properly over time.

### Things to keep in mind

#### Backwards compatibility

With the upcoming upgrades to CMake due to new requirements, they need to take care of the older builds, therefore, they need to always update their tool taking into account first the older versions.

Each `CMakeLists.txt` file is required to specify which version of CMake they are expecting to use. Newer versions of CMake might warn, but will still build the project as older versions did.

#### Language, Language, Language

- The CMake language is designed to be simple, but this simplicity can be an obstacle for new projects adopting it.
- Due to its organic growth, the language has quirks and inconsistencies.
- The initial parser was very basic, not using standard tools like lex/yacc.
- In hindsight, the author believes that using an existing language, such as Lua, would have been beneficial.
- Lua is noted for being small, clean, and a good fit for embedding.
- More consideration to the language design from the start would have been preferable.

#### Plugins did not work

- CMake includes a plugin class to allow projects to create new CMake commands in C.
- Initially, this seemed advantageous, allowing for compiler flexibility.
- However, maintaining compatibility across different systems (32/64 bit Windows and Linux) proved challenging.
- Extending CMake with its own language, while less powerful, is more stable.
- This approach avoids issues with plugins failing to build or load, preventing CMake crashes and build failures.

#### Reduce Exposed API's

- You don't have to worry about backward compatibility if there is nothing to expose (Big brain moment)
- A lot of people asked this to be a library
	- This would cause a lot of ways to make the same thing
	- Broke the CMake community
- If we keep less things public, the less we have to worry