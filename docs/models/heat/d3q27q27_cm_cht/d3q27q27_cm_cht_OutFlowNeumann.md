

## Description

# This model uses

* d3q27 cumulant collision kernel for hydrodynamics
* d3q27 cumulant or cascaded collision kernel for heat
* Boussinesq approx to couple heat with hydrodynamics

## BC

* periodic
* Dirichlet - Equilibrium scheme (1st order convergence)
* Dirichlet - Anti Bounce Back (2nd order convergence)
* Dirichlet - Interpolated Anti Bounce Back (2nd order convergence)
* Neumann like bc - impose heat flux

* WVelocity inlet
* EPressure Outlet
* Neumann Outlet
* Convective Outlet


## Details
[Model description files](Model description) files for this model:
[Dynamics.c](https://github.com/llaniewski/TCLB/blob/(HEAD detached at e162aac)/src/d3q27q27_cm_cht_OutFlowNeumann/Dynamics.c.Rt)
[Dynamics.R](https://github.com/llaniewski/TCLB/blob/(HEAD detached at e162aac)/src/d3q27q27_cm_cht_OutFlowNeumann/Dynamics.R)

### [Zonal Settings](Settings)

| Name | Comment |
| --- | --- |
|`VelocityX`|inlet/outlet/init x-velocity component|
|`VelocityY`|inlet/outlet/init y-velocity component|
|`VelocityZ`|inlet/outlet/init z-velocity component|
|`Pressure`|inlet/outlet/init pressure|
|`InitTemperature`|Initial/Inflow temperature distribution|
|`InitHeatFlux`|Initial/Inflow heat flux through boundary|
|`conductivity`|thermal conductivity of fluid (W/(m·K))|
|`material_density`|density of material [kg/m3]|
|`cp`|specific heat capacity at constant pressure of fluid (J/(kg·K))|
|`Sigma_GH`|Initial width of the Gaussian Hill|
|`FDragInObj`|Weight of [Force exerted on body in X-direction] in objective|
|`FLateralInObj`|Weight of [Force exerted on body in Y-direction] in objective|
|`FLiftInObj`|Weight of [Force exerted on body in Z-direction] in objective|
|`XHydroFLuxInObj`|Weight of [Momentum flux in X-direction] in objective|
|`YHydroFLuxInObj`|Weight of [Momentum flux in Y-direction] in objective|
|`ZHydroFLuxInObj`|Weight of [Momentum flux in Z-direction] in objective|
|`XHydroFLux2InObj`|Weight of [Momentum flux (2nd logger) in X-direction] in objective|
|`YHydroFLux2InObj`|Weight of [Momentum flux (2nd logger) in Y-direction] in objective|
|`ZHydroFLux2InObj`|Weight of [Momentum flux (2nd logger) in Z-direction] in objective|
|`HeatFluxXInObj`|Weight of [Heat flux in X-direction] in objective|
|`HeatFluxYInObj`|Weight of [Heat flux in Y-direction] in objective|
|`HeatFluxZInObj`|Weight of [Heat flux in Z-direction] in objective|
|`HeatFluxX2InObj`|Weight of [Heat flux (2nd logger) in X-direction] in objective|
|`HeatFluxY2InObj`|Weight of [Heat flux (2nd logger) in Y-direction] in objective|
|`HeatFluxZ2InObj`|Weight of [Heat flux (2nd logger) in Z-direction] in objective|
|`HeatSourceInObj`|Weight of [Total Heat flux from body] in objective|


### [Global Settings](Settings)

| Name | Derived | Comment |
| --- | --- | --- |
|`GravitationX`||applied rho*GravitationX|
|`GravitationY`||applied rho*GravitationY|
|`GravitationZ`||applied rho*GravitationZ|
|`nu`||kinematic viscosity|
|`GalileanCorrection`||Galilean correction term|
|`nu_buffer`||kinematic viscosity in the buffer layer|
|`conductivity_buffer`||thermal conductivity in the buffer layer|
|`Omegafor3rdCumulants`||relaxation rate for 3rd order cumulants|
|`h_stability_enhancement`||magic stability enhancement|
|`BoussinesqCoeff`||BoussinesqCoeff=rho_0*thermal_exp_coeff|
|`CylinderCenterX`||X coord of cylinder with imposed heat flux|
|`CylinderCenterY`||Y coord of cylinder with imposed heat flux|
|`CylinderCenterX_GH`||X coord of Gaussian Hill|
|`CylinderCenterY_GH`||Y coord of Gaussian Hill|
|`Threshold`||Parameters threshold|

### [Exported Quantities](Quantities) (VTK, etc)

| Name | [Unit](Units) | Comment |
| --- | --- | --- |
|`Rho`|`kg/m3`|Rho|
|`U`|`m/s`|U|
|`H`|`J`|H|
|`T`|`K`|T|
|`m00_F`|`1`|m00_F|
|`material_density`|`kg/m3`|material_density|
|`cp`|`J/kg/K`|cp|
|`conductivity`|`W/m/K`|conductivity|
|`RawU`|`m/s`|RawU|

#### [Exported Global Integrals](Globals) (CSV, etc)

| Name | [Unit](Units) | Comment |
| --- | --- | --- |
|`FDrag`|`N`|Force exerted on body in X-direction|
|`FLateral`|`N`|Force exerted on body in Y-direction|
|`FLift`|`N`|Force exerted on body in Z-direction|
|`XHydroFLux`|`kg/s`|Momentum flux in X-direction|
|`YHydroFLux`|`kg/s`|Momentum flux in Y-direction|
|`ZHydroFLux`|`kg/s`|Momentum flux in Z-direction|
|`XHydroFLux2`|`kg/s`|Momentum flux (2nd logger) in X-direction|
|`YHydroFLux2`|`kg/s`|Momentum flux (2nd logger) in Y-direction|
|`ZHydroFLux2`|`kg/s`|Momentum flux (2nd logger) in Z-direction|
|`HeatFluxX`|`W`|Heat flux in X-direction|
|`HeatFluxY`|`W`|Heat flux in Y-direction|
|`HeatFluxZ`|`W`|Heat flux in Z-direction|
|`HeatFluxX2`|`W`|Heat flux (2nd logger) in X-direction|
|`HeatFluxY2`|`W`|Heat flux (2nd logger) in Y-direction|
|`HeatFluxZ2`|`W`|Heat flux (2nd logger) in Z-direction|
|`HeatSource`|`W`|Total Heat flux from body|
|`Objective`|`1`|Objective function|

### [Node Types](Node-Types)

| Group | Types |
| --- | --- |
|ADDITIONALS|DarcySolid, Smoothing|
|ADDITIONALS_HEAT|HeaterDirichletTemperatureEQ, HeaterDirichletTemperatureABB, HeaterSource, HeaterNeumannHeatFluxCylinder, HeaterNeumannHeatFluxEast|
|BODY|Body|
|BOUNDARY|ENeumann, EPressure, EVelocity, Solid, Wall, WPressure, WVelocity|
|COLLISION|CM, CM_HIGHER, CM_HIGHER_NONLINEAR, Cumulants, BGK|
|OBJECTIVEFLUX|FluxMeasurmentZone1, FluxMeasurmentZone2|
|OBJECTIVEFORCE|ForceMeasurmentZone|
|SETTINGZONE|DefaultZone|

### [Solved fields](Fields)

| Name | Access pattern | Comment |
| --- | --- | --- |
|`f000`|![stencil](/images/st_b2n1p0p0p0p0p0.png)|flow LB density F 0|
|`f100`|![stencil](/images/st_b2n2p0p0p0p0p0.png)|flow LB density F 1|
|`f200`|![stencil](/images/st_b2p0p0p0p1p0p0.png)|flow LB density F 2|
|`f010`|![stencil](/images/st_b2n1n1p0p0p0p0.png)|flow LB density F 3|
|`f110`|![stencil](/images/st_b2n2n1p0p0p0p0.png)|flow LB density F 4|
|`f210`|![stencil](/images/st_b2p0n1p0p1p0p0.png)|flow LB density F 5|
|`f020`|![stencil](/images/st_b2n1p0p0p0p1p0.png)|flow LB density F 6|
|`f120`|![stencil](/images/st_b2n2p0p0p0p1p0.png)|flow LB density F 7|
|`f220`|![stencil](/images/st_b2p0p0p0p1p1p0.png)|flow LB density F 8|
|`f001`|![stencil](/images/st_b2n1p0n1p0p0p0.png)|flow LB density F 9|
|`f101`|![stencil](/images/st_b2n2p0n1p0p0p0.png)|flow LB density F 10|
|`f201`|![stencil](/images/st_b2p0p0n1p1p0p0.png)|flow LB density F 11|
|`f011`|![stencil](/images/st_b2n1n1n1p0p0p0.png)|flow LB density F 12|
|`f111`|![stencil](/images/st_b2n2n1n1p0p0p0.png)|flow LB density F 13|
|`f211`|![stencil](/images/st_b2p0n1n1p1p0p0.png)|flow LB density F 14|
|`f021`|![stencil](/images/st_b2n1p0n1p0p1p0.png)|flow LB density F 15|
|`f121`|![stencil](/images/st_b2n2p0n1p0p1p0.png)|flow LB density F 16|
|`f221`|![stencil](/images/st_b2p0p0n1p1p1p0.png)|flow LB density F 17|
|`f002`|![stencil](/images/st_b2n1p0p0p0p0p1.png)|flow LB density F 18|
|`f102`|![stencil](/images/st_b2n2p0p0p0p0p1.png)|flow LB density F 19|
|`f202`|![stencil](/images/st_b2p0p0p0p1p0p1.png)|flow LB density F 20|
|`f012`|![stencil](/images/st_b2n1n1p0p0p0p1.png)|flow LB density F 21|
|`f112`|![stencil](/images/st_b2n2n1p0p0p0p1.png)|flow LB density F 22|
|`f212`|![stencil](/images/st_b2p0n1p0p1p0p1.png)|flow LB density F 23|
|`f022`|![stencil](/images/st_b2n1p0p0p0p1p1.png)|flow LB density F 24|
|`f122`|![stencil](/images/st_b2n2p0p0p0p1p1.png)|flow LB density F 25|
|`f222`|![stencil](/images/st_b2p0p0p0p1p1p1.png)|flow LB density F 26|
|`h000`|![stencil](/images/st_b2n1p0p0p0p0p0.png)|heat LB density H 0|
|`h100`|![stencil](/images/st_b2n2p0p0p0p0p0.png)|heat LB density H 1|
|`h200`|![stencil](/images/st_b2p0p0p0p1p0p0.png)|heat LB density H 2|
|`h010`|![stencil](/images/st_b2n1n1p0p0p0p0.png)|heat LB density H 3|
|`h110`|![stencil](/images/st_b2n2n1p0p0p0p0.png)|heat LB density H 4|
|`h210`|![stencil](/images/st_b2p0n1p0p1p0p0.png)|heat LB density H 5|
|`h020`|![stencil](/images/st_b2n1p0p0p0p1p0.png)|heat LB density H 6|
|`h120`|![stencil](/images/st_b2n2p0p0p0p1p0.png)|heat LB density H 7|
|`h220`|![stencil](/images/st_b2p0p0p0p1p1p0.png)|heat LB density H 8|
|`h001`|![stencil](/images/st_b2n1p0n1p0p0p0.png)|heat LB density H 9|
|`h101`|![stencil](/images/st_b2n2p0n1p0p0p0.png)|heat LB density H 10|
|`h201`|![stencil](/images/st_b2p0p0n1p1p0p0.png)|heat LB density H 11|
|`h011`|![stencil](/images/st_b2n1n1n1p0p0p0.png)|heat LB density H 12|
|`h111`|![stencil](/images/st_b2n2n1n1p0p0p0.png)|heat LB density H 13|
|`h211`|![stencil](/images/st_b2p0n1n1p1p0p0.png)|heat LB density H 14|
|`h021`|![stencil](/images/st_b2n1p0n1p0p1p0.png)|heat LB density H 15|
|`h121`|![stencil](/images/st_b2n2p0n1p0p1p0.png)|heat LB density H 16|
|`h221`|![stencil](/images/st_b2p0p0n1p1p1p0.png)|heat LB density H 17|
|`h002`|![stencil](/images/st_b2n1p0p0p0p0p1.png)|heat LB density H 18|
|`h102`|![stencil](/images/st_b2n2p0p0p0p0p1.png)|heat LB density H 19|
|`h202`|![stencil](/images/st_b2p0p0p0p1p0p1.png)|heat LB density H 20|
|`h012`|![stencil](/images/st_b2n1n1p0p0p0p1.png)|heat LB density H 21|
|`h112`|![stencil](/images/st_b2n2n1p0p0p0p1.png)|heat LB density H 22|
|`h212`|![stencil](/images/st_b2p0n1p0p1p0p1.png)|heat LB density H 23|
|`h022`|![stencil](/images/st_b2n1p0p0p0p1p1.png)|heat LB density H 24|
|`h122`|![stencil](/images/st_b2n2p0p0p0p1p1.png)|heat LB density H 25|
|`h222`|![stencil](/images/st_b2p0p0p0p1p1p1.png)|heat LB density H 26|
|`U`|![stencil](/images/st_b2n1p0p0p0p0p0.png)|U|

### [Densities - default accessors](Densities)

| Name | [Field](Fields) | Pulling field from | Comment |
| --- | --- | --- | --- |
|`f000`|f000|![stencil](/images/st_b2p0p0p0p0p0p0.png)|flow LB density F 0|
|`f100`|f100|![stencil](/images/st_b2p1p0p0p1p0p0.png)|flow LB density F 1|
|`f200`|f200|![stencil](/images/st_b2n1p0p0n1p0p0.png)|flow LB density F 2|
|`f010`|f010|![stencil](/images/st_b2p0p1p0p0p1p0.png)|flow LB density F 3|
|`f110`|f110|![stencil](/images/st_b2p1p1p0p1p1p0.png)|flow LB density F 4|
|`f210`|f210|![stencil](/images/st_b2n1p1p0n1p1p0.png)|flow LB density F 5|
|`f020`|f020|![stencil](/images/st_b2p0n1p0p0n1p0.png)|flow LB density F 6|
|`f120`|f120|![stencil](/images/st_b2p1n1p0p1n1p0.png)|flow LB density F 7|
|`f220`|f220|![stencil](/images/st_b2n1n1p0n1n1p0.png)|flow LB density F 8|
|`f001`|f001|![stencil](/images/st_b2p0p0p1p0p0p1.png)|flow LB density F 9|
|`f101`|f101|![stencil](/images/st_b2p1p0p1p1p0p1.png)|flow LB density F 10|
|`f201`|f201|![stencil](/images/st_b2n1p0p1n1p0p1.png)|flow LB density F 11|
|`f011`|f011|![stencil](/images/st_b2p0p1p1p0p1p1.png)|flow LB density F 12|
|`f111`|f111|![stencil](/images/st_b2p1p1p1p1p1p1.png)|flow LB density F 13|
|`f211`|f211|![stencil](/images/st_b2n1p1p1n1p1p1.png)|flow LB density F 14|
|`f021`|f021|![stencil](/images/st_b2p0n1p1p0n1p1.png)|flow LB density F 15|
|`f121`|f121|![stencil](/images/st_b2p1n1p1p1n1p1.png)|flow LB density F 16|
|`f221`|f221|![stencil](/images/st_b2n1n1p1n1n1p1.png)|flow LB density F 17|
|`f002`|f002|![stencil](/images/st_b2p0p0n1p0p0n1.png)|flow LB density F 18|
|`f102`|f102|![stencil](/images/st_b2p1p0n1p1p0n1.png)|flow LB density F 19|
|`f202`|f202|![stencil](/images/st_b2n1p0n1n1p0n1.png)|flow LB density F 20|
|`f012`|f012|![stencil](/images/st_b2p0p1n1p0p1n1.png)|flow LB density F 21|
|`f112`|f112|![stencil](/images/st_b2p1p1n1p1p1n1.png)|flow LB density F 22|
|`f212`|f212|![stencil](/images/st_b2n1p1n1n1p1n1.png)|flow LB density F 23|
|`f022`|f022|![stencil](/images/st_b2p0n1n1p0n1n1.png)|flow LB density F 24|
|`f122`|f122|![stencil](/images/st_b2p1n1n1p1n1n1.png)|flow LB density F 25|
|`f222`|f222|![stencil](/images/st_b2n1n1n1n1n1n1.png)|flow LB density F 26|
|`h000`|h000|![stencil](/images/st_b2p0p0p0p0p0p0.png)|heat LB density H 0|
|`h100`|h100|![stencil](/images/st_b2p1p0p0p1p0p0.png)|heat LB density H 1|
|`h200`|h200|![stencil](/images/st_b2n1p0p0n1p0p0.png)|heat LB density H 2|
|`h010`|h010|![stencil](/images/st_b2p0p1p0p0p1p0.png)|heat LB density H 3|
|`h110`|h110|![stencil](/images/st_b2p1p1p0p1p1p0.png)|heat LB density H 4|
|`h210`|h210|![stencil](/images/st_b2n1p1p0n1p1p0.png)|heat LB density H 5|
|`h020`|h020|![stencil](/images/st_b2p0n1p0p0n1p0.png)|heat LB density H 6|
|`h120`|h120|![stencil](/images/st_b2p1n1p0p1n1p0.png)|heat LB density H 7|
|`h220`|h220|![stencil](/images/st_b2n1n1p0n1n1p0.png)|heat LB density H 8|
|`h001`|h001|![stencil](/images/st_b2p0p0p1p0p0p1.png)|heat LB density H 9|
|`h101`|h101|![stencil](/images/st_b2p1p0p1p1p0p1.png)|heat LB density H 10|
|`h201`|h201|![stencil](/images/st_b2n1p0p1n1p0p1.png)|heat LB density H 11|
|`h011`|h011|![stencil](/images/st_b2p0p1p1p0p1p1.png)|heat LB density H 12|
|`h111`|h111|![stencil](/images/st_b2p1p1p1p1p1p1.png)|heat LB density H 13|
|`h211`|h211|![stencil](/images/st_b2n1p1p1n1p1p1.png)|heat LB density H 14|
|`h021`|h021|![stencil](/images/st_b2p0n1p1p0n1p1.png)|heat LB density H 15|
|`h121`|h121|![stencil](/images/st_b2p1n1p1p1n1p1.png)|heat LB density H 16|
|`h221`|h221|![stencil](/images/st_b2n1n1p1n1n1p1.png)|heat LB density H 17|
|`h002`|h002|![stencil](/images/st_b2p0p0n1p0p0n1.png)|heat LB density H 18|
|`h102`|h102|![stencil](/images/st_b2p1p0n1p1p0n1.png)|heat LB density H 19|
|`h202`|h202|![stencil](/images/st_b2n1p0n1n1p0n1.png)|heat LB density H 20|
|`h012`|h012|![stencil](/images/st_b2p0p1n1p0p1n1.png)|heat LB density H 21|
|`h112`|h112|![stencil](/images/st_b2p1p1n1p1p1n1.png)|heat LB density H 22|
|`h212`|h212|![stencil](/images/st_b2n1p1n1n1p1n1.png)|heat LB density H 23|
|`h022`|h022|![stencil](/images/st_b2p0n1n1p0n1n1.png)|heat LB density H 24|
|`h122`|h122|![stencil](/images/st_b2p1n1n1p1n1n1.png)|heat LB density H 25|
|`h222`|h222|![stencil](/images/st_b2n1n1n1n1n1n1.png)|heat LB density H 26|
|`U`|U|![stencil](/images/st_b2p0p0p0p0p0p0.png)|U|

### [Action stages](Stages)

| Name | Main procedure | Preloaded densities | Pushed fields |
| --- | --- | --- | --- |
|BaseIteration|Run|f000, f100, f200, f010, f110, f210, f020, f120, f220, f001, f101, f201, f011, f111, f211, f021, f121, f221, f002, f102, f202, f012, f112, f212, f022, f122, f222, h000, h100, h200, h010, h110, h210, h020, h120, h220, h001, h101, h201, h011, h111, h211, h021, h121, h221, h002, h102, h202, h012, h112, h212, h022, h122, h222, U|f000, f100, f200, f010, f110, f210, f020, f120, f220, f001, f101, f201, f011, f111, f211, f021, f121, f221, f002, f102, f202, f012, f112, f212, f022, f122, f222, h000, h100, h200, h010, h110, h210, h020, h120, h220, h001, h101, h201, h011, h111, h211, h021, h121, h221, h002, h102, h202, h012, h112, h212, h022, h122, h222, U|
|BaseInit|Init|_none_|f000, f100, f200, f010, f110, f210, f020, f120, f220, f001, f101, f201, f011, f111, f211, f021, f121, f221, f002, f102, f202, f012, f112, f212, f022, f122, f222, h000, h100, h200, h010, h110, h210, h020, h120, h220, h001, h101, h201, h011, h111, h211, h021, h121, h221, h002, h102, h202, h012, h112, h212, h022, h122, h222, U|


### [Actions](Stages)

| Name | Stages |
| --- | --- |
|Iteration|BaseIteration|
|Init|BaseInit|

