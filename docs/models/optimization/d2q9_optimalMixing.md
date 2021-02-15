

## Description
d2q9_optimalMixing


## Details
[Model description files](Model description) files for this model:
[Dynamics.c](https://github.com/llaniewski/TCLB/blob/(HEAD detached at e162aac)/src/d2q9_optimalMixing/Dynamics.c.Rt)
[Dynamics.R](https://github.com/llaniewski/TCLB/blob/(HEAD detached at e162aac)/src/d2q9_optimalMixing/Dynamics.R)

### [Zonal Settings](Settings)

| Name | Comment |
| --- | --- |
|`MovingWallVelocity`|inlet/outlet/init velocity|
|`Velocity`|inlet/outlet/init velocity|
|`Pressure`|Inlet pressure|
|`Temperature`|Temperature|
|`TotalTempSqrInObj`|Weight of [TotalTempSqr] in objective|
|`CountCellsInObj`|Weight of [CountCells] in objective|
|`NMovingWallForceInObj`|Weight of [NMovingWallForce] in objective|
|`SWallForceInObj`|Weight of [SWallForce] in objective|
|`MovingWallPowerInObj`|Weight of [MovingWallPower] in objective|


### [Global Settings](Settings)

| Name | Derived | Comment |
| --- | --- | --- |
|`omega`|1.0/(3*nu + 0.5)|one over relaxation time|
|`nu`||viscosity|
|`omegaT`|1.0/(3*K + 0.5)|one over relaxation time - thermal|
|`K`||thermal_diffusivity|
|`Threshold`||Parameters threshold|

### [Exported Quantities](Quantities) (VTK, etc)

| Name | [Unit](Units) | Comment |
| --- | --- | --- |
|`Rho`|`kg/m3`|Rho|
|`T`|`K`|T|
|`U`|`m/s`|U|
|`RhoB`|`1`|RhoB|
|`TB`|`1`|TB|

#### [Exported Global Integrals](Globals) (CSV, etc)

| Name | [Unit](Units) | Comment |
| --- | --- | --- |
|`TotalTempSqr`|`1`|TotalTempSqr|
|`CountCells`|`1`|CountCells|
|`NMovingWallForce`|`1`|NMovingWallForce|
|`SWallForce`|`1`|SWallForce|
|`MovingWallPower`|`1`|MovingWallPower|
|`Objective`|`1`|Objective function|

### [Node Types](Node-Types)

| Group | Types |
| --- | --- |
|BOUNDARY|NMovingWall, SWall, Solid, Wall|
|COLLISION|MRT|
|SETTINGZONE|DefaultZone|

### [Solved fields](Fields)

| Name | Access pattern | Comment |
| --- | --- | --- |
|`f[0]`|![stencil](/images/st_a1p0p0p0p0p0p0.png)|f[0]|
|`f[1]`|![stencil](/images/st_a1n1p0p0n1p0p0.png)|f[1]|
|`f[2]`|![stencil](/images/st_a1p0n1p0p0n1p0.png)|f[2]|
|`f[3]`|![stencil](/images/st_a1p1p0p0p1p0p0.png)|f[3]|
|`f[4]`|![stencil](/images/st_a1p0p1p0p0p1p0.png)|f[4]|
|`f[5]`|![stencil](/images/st_a1n1n1p0n1n1p0.png)|f[5]|
|`f[6]`|![stencil](/images/st_a1p1n1p0p1n1p0.png)|f[6]|
|`f[7]`|![stencil](/images/st_a1p1p1p0p1p1p0.png)|f[7]|
|`f[8]`|![stencil](/images/st_a1n1p1p0n1p1p0.png)|f[8]|
|`g[0]`|![stencil](/images/st_a1p0p0p0p0p0p0.png)|g[0]|
|`g[1]`|![stencil](/images/st_a1n1p0p0n1p0p0.png)|g[1]|
|`g[2]`|![stencil](/images/st_a1p0n1p0p0n1p0.png)|g[2]|
|`g[3]`|![stencil](/images/st_a1p1p0p0p1p0p0.png)|g[3]|
|`g[4]`|![stencil](/images/st_a1p0p1p0p0p1p0.png)|g[4]|

### [Densities - default accessors](Densities)

| Name | [Field](Fields) | Pulling field from | Comment |
| --- | --- | --- | --- |
|`f[0]`|f[0]|![stencil](/images/st_a1p0p0p0p0p0p0.png)|f[0]|
|`f[1]`|f[1]|![stencil](/images/st_a1p1p0p0p1p0p0.png)|f[1]|
|`f[2]`|f[2]|![stencil](/images/st_a1p0p1p0p0p1p0.png)|f[2]|
|`f[3]`|f[3]|![stencil](/images/st_a1n1p0p0n1p0p0.png)|f[3]|
|`f[4]`|f[4]|![stencil](/images/st_a1p0n1p0p0n1p0.png)|f[4]|
|`f[5]`|f[5]|![stencil](/images/st_a1p1p1p0p1p1p0.png)|f[5]|
|`f[6]`|f[6]|![stencil](/images/st_a1n1p1p0n1p1p0.png)|f[6]|
|`f[7]`|f[7]|![stencil](/images/st_a1n1n1p0n1n1p0.png)|f[7]|
|`f[8]`|f[8]|![stencil](/images/st_a1p1n1p0p1n1p0.png)|f[8]|
|`g[0]`|g[0]|![stencil](/images/st_a1p0p0p0p0p0p0.png)|g[0]|
|`g[1]`|g[1]|![stencil](/images/st_a1p1p0p0p1p0p0.png)|g[1]|
|`g[2]`|g[2]|![stencil](/images/st_a1p0p1p0p0p1p0.png)|g[2]|
|`g[3]`|g[3]|![stencil](/images/st_a1n1p0p0n1p0p0.png)|g[3]|
|`g[4]`|g[4]|![stencil](/images/st_a1p0n1p0p0n1p0.png)|g[4]|

### [Action stages](Stages)

| Name | Main procedure | Preloaded densities | Pushed fields |
| --- | --- | --- | --- |
|BaseIteration|Run|f[0], f[1], f[2], f[3], f[4], f[5], f[6], f[7], f[8], g[0], g[1], g[2], g[3], g[4]|f[0], f[1], f[2], f[3], f[4], f[5], f[6], f[7], f[8], g[0], g[1], g[2], g[3], g[4]|
|BaseInit|Init|_none_|f[0], f[1], f[2], f[3], f[4], f[5], f[6], f[7], f[8], g[0], g[1], g[2], g[3], g[4]|


### [Actions](Stages)

| Name | Stages |
| --- | --- |
|Iteration|BaseIteration|
|Init|BaseInit|

