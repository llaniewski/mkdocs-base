# ESYS-Particle

!!! warning
	All these features related to particles are supported only in the
	[particle](https://github.com/llaniewski/TCLB/tree/particles) branch

ESYS-Particle is a Discrete Element Method (DEM) code, which can be used to
simulate particle dynamics. It can be coupled with TCLB with the use od
Remote Force Interface (RFI).

## Getting ESYS-Particle

The best way to install the ESYS-Particle version that supports RFI it to
download the source code and compile it. The ESYS code is stored kept in a
Bazaar repository (similar to git), on launchpad. You can clone the
apropriate branch using:

```bash
bzr clone lp:~llaniewski/esys-particle/remote-force
```

The main branch is at `lp:esys-particle` but it doesn't support RFI yet.
After you cloned the repository, you can configure, compile and install the
solver.

## Configuration and installation

First we need to generate the `configure` script:

```bash
./autogen.sh
```

As in most cases we will want to install the code without root privilages,
we need to specify the installation directory somewhere in our home
directory (`$HOME/esys_inst/`):

```bash
./configure --prefix=$HOME/esys_inst/ CC=mpicc CXX=mpic++
```

After configuration, we can compile and install:
```
make -j 4
make install
```

## Running ESYS

To be able to run ESYS from our special installation directory, we need to
set apropriate envirnment variables:

```bash
ESPATH=$HOME/esys_inst
export PATH=$ESPATH/bin:$PATH
export LD_LIBRARY_PATH=$ESPATH/lib:$LD_LIBRARY_PATH
export PYTHONPATH=$ESPATH/lib/python2.7/site-packages:$PYTHONPATH
```

This can be placed in `.bashrc` file if we want it to persist. We can check in the right version of ESYS is executed with `which
esysparticle` or `ls -l $(which esysparticle)`.

The simulations can be executed with:
```bash
mpirun -np 2 esysparticle script.py 
```

!!! note "Simulation setup"
	To learn ESYS-Particle, we recommend their [tutorial](https://launchpadlibrarian.net/187793286/ESyS-Particle_Tutorial.pdf)
!!! note "Post-Processing"
	To learn how to post-process results from ESYS-Particle please refer
	to [another section of this manual](/4.-Post-processing/particles/)
