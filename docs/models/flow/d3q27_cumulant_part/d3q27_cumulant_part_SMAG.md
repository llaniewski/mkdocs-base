

## Description
d3q27_cumulant_part_SMAG


## Details
[Model description files](Model description) files for this model:
[Dynamics.c](https://github.com/llaniewski/TCLB/blob/(HEAD detached at e162aac)/src/d3q27_cumulant_part_SMAG/Dynamics.c.Rt)
[Dynamics.R](https://github.com/llaniewski/TCLB/blob/(HEAD detached at e162aac)/src/d3q27_cumulant_part_SMAG/Dynamics.R)

### [Zonal Settings](Settings)

| Name | Comment |
| --- | --- |
|`Velocity`|Inlet velocity|
|`Pressure`|Inlet pressure|
|`Turbulence`|Turbulence intensity|
|`FluxInObj`|Weight of [Volume flux] in objective|
|`DragInObj`|Weight of [Force exerted on body in X-direction] in objective|
|`LiftInObj`|Weight of [Force exerted on body in Z-direction] in objective|
|`LateralInObj`|Weight of [Force exerted on body in Y-direction] in objective|


### [Global Settings](Settings)

| Name | Derived | Comment |
| --- | --- | --- |
|`nu`||Viscosity|
|`nubuffer`||Viscosity in the buffer layer|
|`GalileanCorrection`||Galilean correction term|
|`ForceX`||Force force X|
|`ForceY`||Force force Y|
|`ForceZ`||Force force Z|
|`Smag`||Smagorinsky coefficient for SGS modeling|
|`Omega`||relaxation rate for 3rd order cumulants|
|`ParticleVelocityLimit`||(local) particle velocity limit|
|`Threshold`||Parameters threshold|

### [Exported Quantities](Quantities) (VTK, etc)

| Name | [Unit](Units) | Comment |
| --- | --- | --- |
|`P`|`Pa`|P|
|`U`|`m/s`|U|
|`Solid`|`1`|Solid|
|`F`|`N/m3`|F|

#### [Exported Global Integrals](Globals) (CSV, etc)

| Name | [Unit](Units) | Comment |
| --- | --- | --- |
|`Flux`|`m3/s`|Volume flux|
|`Drag`|`N`|Force exerted on body in X-direction|
|`Lift`|`N`|Force exerted on body in Z-direction|
|`Lateral`|`N`|Force exerted on body in Y-direction|
|`Objective`|`1`|Objective function|

### [Node Types](Node-Types)

| Group | Types |
| --- | --- |
|ADDITIONALS|NSymmetry, SSymmetry|
|BODY|Body|
|BOUNDARY|WVelocityTurbulent, NVelocity, SVelocity, NPressure, SPressure, EPressure, EVelocity, Wall, WPressure, WVelocity|
|COLLISION|MRT|
|HO_BOUNDARY|IB|
|SETTINGZONE|DefaultZone|

### [Solved fields](Fields)

| Name | Access pattern | Comment |
| --- | --- | --- |
|`f000`|![stencil](/images/st_b1p0p0p0p0p0p0.png)|density F 0|
|`f100`|![stencil](/images/st_b1n1p0p0p0p0p0.png)|density F 1|
|`f200`|![stencil](/images/st_b1p0p0p0p1p0p0.png)|density F 2|
|`f010`|![stencil](/images/st_b1p0n1p0p0p0p0.png)|density F 3|
|`f110`|![stencil](/images/st_b1n1n1p0p0p0p0.png)|density F 4|
|`f210`|![stencil](/images/st_b1p0n1p0p1p0p0.png)|density F 5|
|`f020`|![stencil](/images/st_b1p0p0p0p0p1p0.png)|density F 6|
|`f120`|![stencil](/images/st_b1n1p0p0p0p1p0.png)|density F 7|
|`f220`|![stencil](/images/st_b1p0p0p0p1p1p0.png)|density F 8|
|`f001`|![stencil](/images/st_b1p0p0n1p0p0p0.png)|density F 9|
|`f101`|![stencil](/images/st_b1n1p0n1p0p0p0.png)|density F 10|
|`f201`|![stencil](/images/st_b1p0p0n1p1p0p0.png)|density F 11|
|`f011`|![stencil](/images/st_b1p0n1n1p0p0p0.png)|density F 12|
|`f111`|![stencil](/images/st_b1n1n1n1p0p0p0.png)|density F 13|
|`f211`|![stencil](/images/st_b1p0n1n1p1p0p0.png)|density F 14|
|`f021`|![stencil](/images/st_b1p0p0n1p0p1p0.png)|density F 15|
|`f121`|![stencil](/images/st_b1n1p0n1p0p1p0.png)|density F 16|
|`f221`|![stencil](/images/st_b1p0p0n1p1p1p0.png)|density F 17|
|`f002`|![stencil](/images/st_b1p0p0p0p0p0p1.png)|density F 18|
|`f102`|![stencil](/images/st_b1n1p0p0p0p0p1.png)|density F 19|
|`f202`|![stencil](/images/st_b1p0p0p0p1p0p1.png)|density F 20|
|`f012`|![stencil](/images/st_b1p0n1p0p0p0p1.png)|density F 21|
|`f112`|![stencil](/images/st_b1n1n1p0p0p0p1.png)|density F 22|
|`f212`|![stencil](/images/st_b1p0n1p0p1p0p1.png)|density F 23|
|`f022`|![stencil](/images/st_b1p0p0p0p0p1p1.png)|density F 24|
|`f122`|![stencil](/images/st_b1n1p0p0p0p1p1.png)|density F 25|
|`f222`|![stencil](/images/st_b1p0p0p0p1p1p1.png)|density F 26|
|`fx`|![stencil](/images/st_b1p0p0p0p0p0p0.png)|fx|
|`fy`|![stencil](/images/st_b1p0p0p0p0p0p0.png)|fy|
|`fz`|![stencil](/images/st_b1p0p0p0p0p0p0.png)|fz|
|`sol`|![stencil](/images/st_b1p0p0p0p0p0p0.png)|sol|

### [Densities - default accessors](Densities)

| Name | [Field](Fields) | Pulling field from | Comment |
| --- | --- | --- | --- |
|`f000`|f000|![stencil](/images/st_b1p0p0p0p0p0p0.png)|density F 0|
|`f100`|f100|![stencil](/images/st_b1p1p0p0p1p0p0.png)|density F 1|
|`f200`|f200|![stencil](/images/st_b1n1p0p0n1p0p0.png)|density F 2|
|`f010`|f010|![stencil](/images/st_b1p0p1p0p0p1p0.png)|density F 3|
|`f110`|f110|![stencil](/images/st_b1p1p1p0p1p1p0.png)|density F 4|
|`f210`|f210|![stencil](/images/st_b1n1p1p0n1p1p0.png)|density F 5|
|`f020`|f020|![stencil](/images/st_b1p0n1p0p0n1p0.png)|density F 6|
|`f120`|f120|![stencil](/images/st_b1p1n1p0p1n1p0.png)|density F 7|
|`f220`|f220|![stencil](/images/st_b1n1n1p0n1n1p0.png)|density F 8|
|`f001`|f001|![stencil](/images/st_b1p0p0p1p0p0p1.png)|density F 9|
|`f101`|f101|![stencil](/images/st_b1p1p0p1p1p0p1.png)|density F 10|
|`f201`|f201|![stencil](/images/st_b1n1p0p1n1p0p1.png)|density F 11|
|`f011`|f011|![stencil](/images/st_b1p0p1p1p0p1p1.png)|density F 12|
|`f111`|f111|![stencil](/images/st_b1p1p1p1p1p1p1.png)|density F 13|
|`f211`|f211|![stencil](/images/st_b1n1p1p1n1p1p1.png)|density F 14|
|`f021`|f021|![stencil](/images/st_b1p0n1p1p0n1p1.png)|density F 15|
|`f121`|f121|![stencil](/images/st_b1p1n1p1p1n1p1.png)|density F 16|
|`f221`|f221|![stencil](/images/st_b1n1n1p1n1n1p1.png)|density F 17|
|`f002`|f002|![stencil](/images/st_b1p0p0n1p0p0n1.png)|density F 18|
|`f102`|f102|![stencil](/images/st_b1p1p0n1p1p0n1.png)|density F 19|
|`f202`|f202|![stencil](/images/st_b1n1p0n1n1p0n1.png)|density F 20|
|`f012`|f012|![stencil](/images/st_b1p0p1n1p0p1n1.png)|density F 21|
|`f112`|f112|![stencil](/images/st_b1p1p1n1p1p1n1.png)|density F 22|
|`f212`|f212|![stencil](/images/st_b1n1p1n1n1p1n1.png)|density F 23|
|`f022`|f022|![stencil](/images/st_b1p0n1n1p0n1n1.png)|density F 24|
|`f122`|f122|![stencil](/images/st_b1p1n1n1p1n1n1.png)|density F 25|
|`f222`|f222|![stencil](/images/st_b1n1n1n1n1n1n1.png)|density F 26|
|`fx`|fx|![stencil](/images/st_b1p0p0p0p0p0p0.png)|fx|
|`fy`|fy|![stencil](/images/st_b1p0p0p0p0p0p0.png)|fy|
|`fz`|fz|![stencil](/images/st_b1p0p0p0p0p0p0.png)|fz|
|`sol`|sol|![stencil](/images/st_b1p0p0p0p0p0p0.png)|sol|

### [Action stages](Stages)

| Name | Main procedure | Preloaded densities | Pushed fields |
| --- | --- | --- | --- |
|BaseIteration|Run|f000, f100, f200, f010, f110, f210, f020, f120, f220, f001, f101, f201, f011, f111, f211, f021, f121, f221, f002, f102, f202, f012, f112, f212, f022, f122, f222, fx, fy, fz, sol|f000, f100, f200, f010, f110, f210, f020, f120, f220, f001, f101, f201, f011, f111, f211, f021, f121, f221, f002, f102, f202, f012, f112, f212, f022, f122, f222, fx, fy, fz, sol|
|CalcF|CalcF|f000, f100, f200, f010, f110, f210, f020, f120, f220, f001, f101, f201, f011, f111, f211, f021, f121, f221, f002, f102, f202, f012, f112, f212, f022, f122, f222, fx, fy, fz, sol|fx, fy, fz, sol|
|BaseInit|Init|_none_|f000, f100, f200, f010, f110, f210, f020, f120, f220, f001, f101, f201, f011, f111, f211, f021, f121, f221, f002, f102, f202, f012, f112, f212, f022, f122, f222, fx, fy, fz, sol|


### [Actions](Stages)

| Name | Stages |
| --- | --- |
|Iteration|BaseIteration, CalcF|
|Init|BaseInit, CalcF|

