#  Setup Elements 
##  Control 

```xml
<Control Iterations="1s">
  <CSV file="example/sin.csv" Time="x*1s">
    <Params PY="Sin*0.5m+1m"/>
    <Params PR="Cos*2+1"/>
  </CSV>
</Control>
```

Element prescribing time-dependent Settings 

| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` | Length of the time-dependentcy | Value with unit (int) |

##  SyntheticTurbulence 

```xml
<SyntheticTurbulence .../>
```

Prescribe properties of the synthetic turbulence generated for initialization and boundary conditions 

| Attribute | Comment | Value |
| --- | --- | --- |
| `Modes=` | Number of harmonic modes to generate for the turbulence | Numeric (int) |
| `Spread=` | The way to divide the spectrum to a finite number of modes | Select from: Even, Log, Quantile |
| `Spectrum=` | Type of spectrum to use | Select from: Von Karman, One Wave |
| `MainWaveLength=` | Main wave-length in the Von Karman spectrum | Value with unit (float) |
| `DiffusionWaveLength=` | Diffusion scale wave-length in the Von Karman spectrum | Value with unit (float) |
| `MinWaveLength=` | Minimal space wave-length | Value with unit (float) |
| `MaxWaveLength=` | Maximal space wave-length | Value with unit (float) |
| `TimeWaveLength=` | Time wave-length of the syntetic turbulence (can be also `TimeWaveNumber` or `TimeWaveFrequency`) | Value with unit (float) |

