#  Optimization and Optimal Control 
##  OptimalControl 

```xml
<OptimalControl .../>
```

 

| Attribute | Comment | Value |
| --- | --- | --- |
| `what=` | Select a time-dependent setting to optimize | Select from: list(special = "SettingInZone") |

##  OptimalControlSecond 

```xml
<OptimalControlSecond what="Velocity-inlet" lower="0.0" upper="0.05"/>
```

Parametrises a time-dependend Setting with the value of every second iteration. Values inbetween are interpolated.
 

| Attribute | Comment | Value |
| --- | --- | --- |
| `what=` | Select a time-dependent setting to optimize | Select from: list(special = "SettingInZone") |
| `lower=` | Lower limit on the value of the Setting | Value with unit (float) |
| `upper=` | Upper limit on the value of the Setting | Value with unit (float) |

##  Fourier 

```xml
<Fourier>
  <OptimalControlSecond what="Velocity-inlet"/>
</Fourier>
```

Makes a truncated Fourier transform of a time-dependent Setting (OptimalControl)
 

| Attribute | Comment | Value |
| --- | --- | --- |
| `modes=` | Number of Fourier modes to use for the parametrization | Select from: int |
| `lower=` | Lower limit on the Fourier coefficients | Value with unit (float) |
| `upper=` | Upper limit on the Fourier coefficients | Value with unit (float) |

##  BSpline 

```xml
<BSpline nodes="10" lower="-1" upper="1">
  <OptimalControlSecond what="Velocity-inlet"/>
</BSpline>
```

Makes B-Spline transform/smoothing of a time-dependent Setting (OptimalControl)
 

| Attribute | Comment | Value |
| --- | --- | --- |
| `nodes=` | Number of degrees of freedom (parameters) of the b-spline | Numeric (int) |
| `periodic=` | If the b-spline should be periotic in the control period | Unknown type |
| `lower=` | Lower limit on the values | Value with unit (float) |
| `upper=` | Upper limit on the values | Value with unit (float) |

##  RepeatControl 

```xml
<RepeatControl length="100" lower="-1" upper="1">
  <OptimalControl what="Velocity-inlet"/>
</RepeatControl>
```

Repeats a control for optimal control
 

| Attribute | Comment | Value |
| --- | --- | --- |
| `length=` | Length of the control to repeat | Value with unit (int) |
| `lower=` | Lower limit on the values | Value with unit (float) |
| `upper=` | Upper limit on the values | Value with unit (float) |

