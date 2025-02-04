# slsqp

[![GitHub release](https://img.shields.io/github/release/jacobwilliams/slsqp.svg?style=plastic)](https://github.com/jacobwilliams/slsqp/releases/latest)

Modern Fortran Edition of the SLSQP Optimizer

### Status

![Build Status](https://github.com/jacobwilliams/slsqp/actions/workflows/CI.yml/badge.svg)

### Description

This is an updated version of the SLSQP nonlinear constrained optimization code. It can be used to solve nonlinear programming problems that seek to minimize a scalar performance index subject to nonlinear equality and inequality constraints as well as bounds on the variables.

Updates to the original code include:

* It has been translated into free-form source.
* It is now thread safe. The original version was not thread safe due to the use of saved variables in one of the subroutines.
* It no longer uses obsolescent and non-standard Fortran features. It should now be 100% standard compliant (Fortran 2008).
* It now has an easy-to-use object-oriented interface. The `slsqp_class` is used for all interactions with the solver. Methods include `initialize()`, `optimize()`, and `destroy()`.
* It includes updated versions of some of the third-party routines used in the original code (BLAS, LINPACK, and NNLS).
* Some new features were added to support printing error  messages and reporting iterations to the user.
* The user can now specify the max and min `alpha` to use during the line search.
* The user can supply a routine to compute the gradients of the objective function and constriants, or allow the code to estimate them using finite differences (backward, forward, or central).
* The documentation strings in the code have been converted to [FORD](https://github.com/cmacmackin/ford) format, allowing for [nicely formatted documentation](http://jacobwilliams.github.io/slsqp/) to be auto-generated.
* A couple of bug fixes noted elsewhere have been applied.

### License

  * The original sourcecode and the modifications are released under a [permissive BSD-style license](https://github.com/jacobwilliams/slsqp/blob/master/LICENSE).

### Building SLSQP

A [FoBiS](https://github.com/szaghi/FoBiS) configuration file (`slsqp.fobis`) is also provided that can also build the library and examples. Use the `mode` flag to indicate what to build. For example:

  * To build all the examples using gfortran: `FoBiS.py build -f slsqp.fobis -mode tests-gnu`
  * To build all the examples using ifort: `FoBiS.py build -f slsqp.fobis -mode tests-intel`
  * To build a static library using gfortran: `FoBiS.py build -f slsqp.fobis -mode static-gnu`
  * To build a static library using ifort: `FoBiS.py build -f slsqp.fobis -mode static-intel`

  The full set of modes are: `static-gnu`, `static-gnu-debug`, `static-intel`, `static-intel-debug`, `shared-gnu`, `shared-gnu-debug`, `shared-intel`, `shared-intel-debug`, `tests-gnu`, `tests-gnu-debug`, `tests-intel`, `tests-intel-debug`

  To generate the documentation using [ford](https://github.com/cmacmackin/ford), run: ```FoBis.py rule --execute makedoc -f slsqp.fobis```

  To run the test programs, run: ```FoBis.py rule --execute tests -f slsqp.fobis```

### Development

  * Development continues on [GitHub](https://github.com/jacobwilliams/slsqp).

### Documentation

  The latest API documentation can be found [here](http://jacobwilliams.github.io/slsqp/). This was generated from the source code using [FORD](https://github.com/cmacmackin/ford) (note that the included `build.sh` script will also generate these files).

### References

* [Original sourcecode at NETLIB](http://www.netlib.org/toms/733)
* D. Kraft, "[A software package for sequential quadratic programming](http://degenerateconic.com/wp-content/uploads/2018/03/DFVLR_FB_88_28.pdf)",
  Technical Report DFVLR-FB 88-28, Institut für Dynamik der Flugsysteme,
  Oberpfaffenhofen, July 1988.
* D. Kraft, "[Algorithm 733: TOMP--Fortran modules for optimal control calculations](http://dl.acm.org/citation.cfm?id=192124),"
  ACM Transactions on Mathematical Software, Vol. 20, No. 3, p. 262-281 (1994).
