# Geometry

We will use the OpenSCAD software to create the geometry. It will consist of
four balls connected by a narrowing channel.

## OpenSCAD

You can install OpenSCAD with:
```bash
sudo apt install openscad
```

The OpenSCAD allow us to create geometries with a script.

```scad
R=30;
D=60;
translate([R,0,R]) {
    sphere(d=R*2);
    for (x=[1:4]) {
        translate([0,x*D,0]) {
            sphere(d=R*2);
        }
    }
    rotate([-90,0,0]) cylinder(h=8*R,r1=R,r2=R/2);
    rotate([90,0,0]) cylinder(h=3*R,r1=R,r2=R);
    translate([0,4*D,0]) rotate([-90,0,0]) cylinder(h=3*R,r1=R,r2=R);
}
```

From OpenSCAD you can export into several file formats. Export an
ASCII STL file "pipe_txt.stl". Sadly, it is rare for any software to support ASCII STL
files (which is also the case with TCLB). To create both binary stl file and
MSH file for ESYS-Particle with a util program provided with TCLB:

```bash
tools/stlutil -f pipe_txt.stl -o pipe.stl
tools/stlutil -f pipe_txt.stl -o pipe.msh
```

# ESYS-Particle simulation

## Configuration
The ESYS-Particle is simulation is set up in a python script "pipe.py". At
the begining of the script we have to initialize the `sim` object:

```python
from esys.lsm import *
from esys.lsm.util import Vec3, BoundingBox
from esys.lsm.geometry import *

sim = LsmMpi(numWorkerProcesses=1, mpiDimList=[1,1,1])
sim.initNeighbourSearch( particleType="RotSphere", gridSpacing=38, verletDist=0.7 )
sim.setSpatialDomain(
	BoundingBox(Vec3(0,0,0), Vec3(64,240,64)),
	circDimList = [False, False, False]
)
sim.setTimeStepSize(1)
sim.setNumTimeSteps(10000)
```

First we read in the mesh:

```python
sim.readMesh(
	fileName = "pipe.msh",
	meshName = "floor_mesh_wall"
)
```

Then we add a set of particles, randomly packed in a rectangle:

```python
geoRandomBlock = RandomBoxPacker(
            minRadius = 4.0000,
            maxRadius = 15.0000,
            cubicPackRadius = 11.0000,
            maxInsertFails = 1000,
            bBox = BoundingBox(
            Vec3(9.0000, 2.0000, 9.0000),
            Vec3(51.0000, 60.0000, 51.0000)
	),
	circDimList = [False, False, False],
	tolerance = 1.0000e-05
)
geoRandomBlock.generate()
geoRandomBlock_particles = geoRandomBlock.getSimpleSphereCollection()
```

We add friction interaction between particles:

```python
normalK = 3;
sim.createInteractionGroup (
	RotFrictionPrms (
		name = "friction",
		normalK = normalK,
		dynamicMu = 0.6,
		shearK = normalK/10.0,
		staticMu = 0.6,
		scaling = True
	)
)
```

and elastic interaction between particles and mesh wall:

```python
sim.createInteractionGroup (
	NRotElasticTriMeshPrms (
		name = "floorWall_repell",
		meshName = "floor_mesh_wall",
		normalK = normalK
	)
)
```

To start up the movement we add a small acceleration ($10^{-5}$):

```python
sim.createInteractionGroup (
	GravityPrms (
		name = "gravity",
		acceleration = Vec3(0.0000, 1e-5, 0.0000)
	)
)
```

To visualize the results, we add a check-pointer, which will write dump
files:

```python
sim.createCheckPointer (
	CheckPointPrms (
		fileNamePrefix = "flow_data",
		beginTimeStep = 0,
		endTimeStep = 20000,
		timeStepIncr = 100
	)
)
```

Finnaly, we finish the "pipe.py" file with the execution of the simulation:

```python
sim.run()
```

## Running ESYS-Particle
