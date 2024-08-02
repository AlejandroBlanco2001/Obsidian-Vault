Lecture link: [here](https://aosabook.org/en/v1/packaging.html)

In terms of installing the applications, there is two main approaches: 
1. Microsoft and Mac OS X
	- All the app must be self-contained, all the libraries should be in the app distribution
	- In this way, the OS shouldn't worry about the installation and removal of the software
2. Linux
	- Each part of the software is a small self-contained pieces called *packages* 
	- Libraries are bundled into packages
	- The dependencies are fetched from a central repository

One of the major drawbacks of the second approach, is that they don't have full control over the dependencies of the program, and we can avoid ***dependency hell***

Python currently follow the Linux approach

> [!NOTE] *Package* refers to a directory with Python files, and those Python files are called *modules*
## The Burden of the Python Developer

When you make a specific release of your Python application can have the following errors:
- Packagers for every target system will be able to repackage your work,
- The dependencies you have will themselves be repackaged in every target system
- System dependencies will be clearly described.

If one of the three requirements isn't satisfied, you must make a portable application with all the dependencies. Basically a ***binary*** 

>[!NOTE] You can achieve this using `zc.buildout`. A binary refers to an already compiled application, ready to use. 

This can cause a lot of troubles if someone was to repack your application, *Can Python have a packaging system that can be automatically translated into other packaging systems*?

- What if someone puts their cat name as one version 
- What if you put files that need to be there

So the new question is, *is it possible to have a packaging system in Python that can provide all the information needed to repackage an application with any third-party packaging system out there without having to read the code, and make everyone happy?*

## The Current Architecture

First they `Distutils`, then `Setuptools` was born with more advance tools (Based on `Distutils`), and finally `Pip` born (Based on `Setutools`), but they all had the same problems, because they were made in top of `Distutils`

>[!NOTE] Rebuild `Distutils` was almost an impossible task, therefore, they started to create `Distutils2`!

### Distutils in deep

This contains commands, each of which contain a 'run' method that can be run with a lot of options.

To use it, you only need to create a `setup.py` file (convention!) with the use to the setup method inside the library.

```python
from distutils.core import setup

setup(name='MyProject', version='1.0', py_modules=['mycode.py'])
```

This module can then be used to run `Distutils` commands like `sdist`, which creates a source distribution in an archive and places it in a `dist` directory:

```bash
$ python setup.py sdist
```

Using the same script, you can install the project using the `install` command:

```bash
$ python setup.py install
```

![[Pasted image 20240623071645.png]]

`Distutils` provides other commands such as:

- `upload` to upload a distribution into an online repository.
- `register` to register the metadata of a project in an online repository without necessary uploading a distribution,
- `bdist` to creates a binary distribution, and
- `bdist_msi` to create a `.msi` file for Windows.

If you think about, the main issue is that, ***one module do to many things***

### Metadata and PyPI

>[!NOTE] PyPI, stands for 'Python Package Index', is one of the central repositories mentioned in the begging of the notes 

When making a distribution, this generates the following metadata for PyPI:

- `Name`: The name of the project.
- `Version`: The version of the release.
- `Summary`: A one-line description.
- `Description`: A detailed description.
- `Home-Page`: The URL of the project.
- `Author`: The author name.
- `Classifiers`: Classifiers for the project. Python provides a list of classifiers for the license, the maturity of the release (beta, alpha, final), etc.
- `Requires`, `Provides`, and `Obsoletes`: Used to define dependencies with modules.

>[!NOTE] Fun fact, the `requires` parameters, is just for metadata, doesn't do anything

### Architecture of a Python Installation

If you install a Python project with the `setup.py`, the following is going to happen:

- _Python packages_ and modules will land in the Python directory that is loaded when the interpreter starts: under the latest Ubuntu they will wind up in `/usr/local/lib/python2.6/dist-packages/` and under Fedora in `/usr/local/lib/python2.6/sites-packages/`.
- _Data files_ defined in a project can land anywhere on the system.
- The _executable script_ will land in a `bin` directory on the system. Depending on the platform, this could be `/usr/local/bin` or in a bin directory specific to the Python installation.

We need to know that every file copied is not recorded, therefore, you can't remove those files. ***BUT***, if the package has marked the option `record` this will be store on a text file.

>[!NOTE] That options is barely used nor mentioned.

## Setuptools, PIP and others

### Dependencies issue (Setuptools)

PyPI alowed developers to publish Python projects that could include several modules organized into Python Packages. But at the same time, projects could define module-level dependencies via ***Require***. Both are nice, at the same time, don't

But, what this do? People rarely (we can say never) did use module-level dependencies, and the new feature (project-level dependencies) was just used by `Setuptools`, therefore, they create their own standard on top of a bad design.

>[!NOTE]  `easy_install` is a script used to automatically fetch and install dependencies by looking for them on PyPI

This result that the **easy_install** tool worked very odd, causing to construct the dependency tree, bit by bit.

But this was having the same issues

- If a dependency install fails, there is no rollback and the system can end up in a broken state.
- The dependency graph is built on the fly during installation, so if a dependency conflict is encountered the system can end up in a broken state as well.

### Uninstall? (Pip)

Any of the previous tools provide a record of the moved/copied files into the system, making the uninstall process really hard (almost impossible to be performed). 

By other hand, ***Pip*** provide a text file with all the files copied, but because this was based on the previous tools you would have *FOUR* different metadata files.

- `Distutils`' `egg-info`, which is a single metadata file.
- `Setuptools`' `egg-info`, which is a directory containing the metadata and extra `Setuptools` specific options.
- `Pip`'s `egg-info`, which is an extended version of the previous.
- Whatever the hosting packaging system creates.

### What about the Data Files?

You can have files outside of the Python distribution or inside of them, the ones that are outside of them, can be set to specific locations (Bad news for the OS)

- Data files are not in the metadata, so the packagers need to read `setup.py` and sometimes go to the actual code
- The developer should not be the one deciding where data files should land on a target system.
- There are no categories for these data files: images, man pages, and everything else are all treated the same way.

These issue was an assumption for both new tools, making the use of these data files, a complete mess for the users, that would need to patch the actual package to use them.

## The new raise and improvements

### Metadata

To fix them, we make the following changes:

- A saner way to define versions 
- Project level dependencies
- Static way to define platform specific values

>[!IMPORTANT] I should read the [PEP 345](https://peps.python.org/pep-0345/) to have more context, and maybe write some notes to have more idea

#### Versions

They made a ensure consistent versioning standard for projects, so they all follow the same schema

```
N.N[.N]+[{a|b|c|rc}N[.N]+][.postN][.devN]
```

Now, every project that don't follow these standard is rejected from PyPI

### Dependencies 

Now, the `Requires`, `Provides`, and `Obsoletes` were replaced with `Requires-Dist`, `Provides-Dist`, and `Obsoletes-Dist`

The first one, contains the name of other `Distutils` package (even the version)

```shell
Requires-Dist: pkginfo
Requires-Dist: PasteDeploy
Requires-Dist: zope.interface (>3.5.0)
```

`Provides-Dist` is used to define extra names contained in the project. It's useful when a project wants to merge with another project. For example the ZODB project can include the `transaction` project and state:

```shell
Provides-Dist: transaction
```

`Obsoletes-Dist` is useful to mark another project as an obsolete version:

```shell
Obsoletes-Dist: OldName
```

#### Environment Markers

An environment marker is a marker that can be added at the end of a field after a semicolon to add a condition about the execution environment. Some examples are:

```shell
Requires-Dist: pywin32 (>1.0); sys.platform == 'win32'
Obsoletes-Dist: pywin31; sys.platform == 'win32'
Requires-Dist: foo (1,!=1.3); platform.machine == 'i386'
Requires-Dist: bar; python_version == '2.4' or python_version == '2.5'
Requires-External: libxslt; 'linux' in sys.platform
```

## So... what's installed?

You ***MUST*** have one installation format among all Python tools. If we want that Installer A to detect that Installer B has previously installed project *Foo*, they both need to share and update the same database of installed projects.

This small thing, can cause a lot of troubles across multiples systems:

- What if the RPM has another package for another program with the same name?
- What if the OS changes the name of the package?

>[!NOTE] One way to avoid that is to isolate the Python global installation tools like `virtualenv`

So even with that approach, we need to generate the following metadata to be able to inform the RPM 

- `METADATA`: the metadata, as described in PEP 345, PEP 314 and PEP 241.
- `RECORD`: the list of installed files in a csv-like format.
- `INSTALLER`: the name of the tool used to install the project.
- `REQUESTED`: the presence of this file indicates that the project installation was explicitly requested (i.e., not installed as a dependency).

### Architecture of Data Files

We use a new architecture for using this

```python
import os
import pkgutil

# Open the file located in config/mopy.cfg in the MPTools project
cfg = pkgutil.open('MPTools', 'config/mopy.cfg')
```

`pkgutil.open` looks for the project metadata and see if it contains a `RESOURCES` file. This is a simple map of files to locations that the system may contain:

```python
config/mopy.cfg {confdir}/{distribution.name}
```

![[Pasted image 20240623222947.png]]

#### How to declare those

In practice, a project can define where data files should land by defining a mapper in their `setup.cfg` file.

```python
[files]
resources =
        config/mopy.cfg {confdir}/{application.name}/
        images/*.jpg    {datadir}/{application.name}/
```

![[Pasted image 20240623223304.png]]*How it works the mapping*

### PyPI Improvements

The way that PyPI was created, we had a single point of failure, if this get's down, all failed. So after PEP 380, they implemented a mirror.

![[Pasted image 20240623223518.png]]

#### How to synch?

The main purpose of the mirrors is to reduce the amount of data transferred between the central server and the mirror. To achieve this, they *must* use the changelog *PyPI XML-RPC* call, and only re-fetch the packages that have been changed since the last time.

#### Statistic Propagation

When you download a release from any of the mirrors, the protocol ensures that the download hit is transmitted to the master PyPI server, to get an actual count. This is done with a weekly CSV and daily CSV.

## Implementation Details, the born of Distutils 2

With this new thing, `setup.py` is being deprecated, this not longer exists. This is being replaced with the `setup.cfg`.

```
[metadata]
name = MPTools
version = 0.1
author = Tarek Ziade
author-email = tarek@mozilla.com
summary = Set of tools to build Mozilla Services apps
description-file = README
home-page = http://bitbucket.org/tarek/pypi2rpm
project-url: Repository, http://hg.mozilla.org/services/server-devtools
classifier = Development Status :: 3 - Alpha
    License :: OSI Approved :: Mozilla Public License 1.1 (MPL 1.1)

[files]
packages =
        mopytools
        mopytools.tests

extra_files =
        setup.py
        README
        build.py
        _build.py

resources =
    etc/mopytools.cfg {confdir}/mopytools
```

With this new approach, we can have two big problems solved:

- Installer/uninstaller 
- Dependency graph view of installed projects

## What we have learned?

### It's all about the PEP's 

- Python is complex, the architecture is complex, so instead of making changes to solve an issue, we should always take care of the PEP's and propose things to the community.

- All innovations should impact a PEP, and rise a new concern across the whole community.

### A Package that Enters the Standard Library Has One Foot in the Grave

- When a package is in the standard library, to remove it's very complex 
- So if you need to make major changes, you need to publish a new package 

### Backward Compatibility

- The packaging system is always open to change, therefore, we always should make the process open for backward compatibility

## Important things learned 

- We should always have standards, avoid doing things the way that ***WE*** want. Ask the others, to avoid having multiple ways to do the same thing

-  Having a clear map, will avoid extra efforts

- If is all bad, is better to start from scratch. Not to re-build the damage thing 

- Is not always look how to implement new things, we should always look how to bring back the old things to the be compatible.
