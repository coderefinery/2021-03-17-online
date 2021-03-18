+++
title = "Prerequisites and software requirements"
+++

## Prerequisites

- If you will attend the Hackathon, you are expected to bring a code
  project to the event in which you want to implement testing
  functionality. It does not need to be a large complicated codebase,
  just something you use or intend to use in your research. If it's
  not your own code, make sure that it has a license which allows you
  to modify it.
- You may need to install some software - see the Software
  Requirements section on below.
- It is somewhat important that you have a basic idea of how Git
  works. Please go through [this Git-refresher
  material](https://coderefinery.github.io/git-refresher/) for a basic
  overview and important configuration steps.

## Software requirements

You are assumed to have everything installed that you need for running
code in your preferred programming language, e.g. Python, Matlab or R
interpreters, or compilers for C/C++, Fortran, Julia, Rust, Go etc.

You also need to have a testing framework available for your preferred
language. Some languages need a package installation while others have
a framework built into their standard libraries. A list of recommended
tools and frameworks will be published here soon.

Other requirements:

- [Bash](https://coderefinery.github.io/installation/bash/)
- [Editor](https://coderefinery.github.io/installation/editors/)
- [Git](https://coderefinery.github.io/installation/git/)
- [Zoom](https://coderefinery.github.io/installation/zoom/)
- [Python and pytest](https://coderefinery.github.io/installation/python-testing/)
- [GitHub](https://github.com/) or [GitLab](https://gitlab.com/) account. 

Optional requirements depending on which language you will be using:

- C++ users will need [CMake](https://cmake.org/) and 
  [Catch2](https://github.com/catchorg/Catch2). Both can be installed through conda, 
  which you should have set up by following the "Python and pytest" installation 
  instructions above. In a terminal, run:  
  `conda install -c conda-forge cmake`  
  `conda install -c conda-forge catch2`  

- Fortran users will need to install [pFUnit](https://github.com/Goddard-Fortran-Ecosystem/pFUnit).
  pFUnit is supported on Linux and MacOS and is available on Windows through Cygwin. 
  Install pFUnit by following the 
  [official instructions](https://github.com/Goddard-Fortran-Ecosystem/pFUnit).

- R users will need [testthat](https://testthat.r-lib.org/). Follow the 
  instructions on the [official page](https://testthat.r-lib.org/).



