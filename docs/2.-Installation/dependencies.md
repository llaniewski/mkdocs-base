# Dependencies

## nVidia CUDA

If you want to use GPU you have to install [nVidia CUDA](https://developer.nvidia.com/cuda-zone).

## Message Passing Interface (MPI)

[MPI](https://en.wikipedia.org/wiki/Message_Passing_Interface) library is
required for communication between processes in TCLB. TCLB cannot be runned
without it, even if you run only a single process. You for instance use
[OpenMPI](http://www.open-mpi.org) (`sudo tools/install.sh openmpi`)

## R

[R](https://www.r-project.org/) is a scripting language mainly used for data
analysis. In TCLB is using TCLB for many things, including source
generation. You can install R using eg. `sudo tools/install.sh r`.

### Packages

For many important parts of TCLB you need to install several packages (you
can use `tools/install.sh rdep`):

* [optparse](https://cran.r-project.org/package=optparse)
* [numbers](https://cran.r-project.org/package=numbers)
* [rtemplate](https://github.com/llaniewski/rtemplate)
* [gvector](https://github.com/llaniewski/gvector)
* [polyAlgebra](https://github.com/llaniewski/polyAlgebra)

If you want to use R during your simulation with `<RunR>` element (`tools/install.sh rinside`):

* [polyAlgebra](https://github.com/eddelbuettel/rinside)

If you want to use python in source generation, please install (`tools/install.sh
rpython`):

* [rPython](https://cran.r-project.org/package=rPython) (if you want to develop a model using python in place or R)

## Python

[Python](https://www.python.org/) can be used for source generation in
models, and it can be used in execution. With python you will need in most
cases (`sudo tools/install.sh python-dev`):

* [numpy](http://www.numpy.org/)
* [sympy](http://www.sympy.org/) 

