# Post-processing of particle data

ESYS-Particle exports snapshot, which have to be transformed to the VTK
format. You can use the provided tool `dump2vtk`:

```bash
dump2vtk -rot -i flow_data -o flow_data_vtk -t 0 200 100
```

The options of the tool are:

Option<div style="width:110px;"></div> | Comment
------------------ | --------------------------
`-rot`             | This option *have to be* used if the simulation used RotParticles
`-i [fileprefix]`  | Specify the prefix of the snapshots (what was provided in `fileNamePrefix` in `CheckPointPrms`)
`-o [fileprefix]`  | The prefix for the created VTK files
`-t [i0] [di] [n]` | Provide the iteration number of the first snapshot `i0`, the number of iterations between snapshot `di`, and the number of snapshots `n`
`-mesh`            | Export the mesh in the VTK

