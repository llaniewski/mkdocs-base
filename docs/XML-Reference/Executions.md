#  Executions 
##  Solve 

```xml
<Solve .../>
```

Main solution element. It runs a prescribed number of iterations.
 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |

##  Adjoint 

```xml
<Adjoint .../>
```

 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]), [[Executions]] ([[<code>&lt;Solve/&gt;</code>|Executions#solve]], [[<code>&lt;Adjoint/&gt;</code>|Executions#adjoint]], [[<code>&lt;Optimize/&gt;</code>|Executions#optimize]], [[<code>&lt;Threshold/&gt;</code>|Executions#threshold]], [[<code>&lt;ThresholdNow/&gt;</code>|Executions#thresholdnow]], [[<code>&lt;Repeat/&gt;</code>|Executions#repeat]], [[<code>&lt;LoadBinary/&gt;</code>|Executions#loadbinary]], [[<code>&lt;SaveBinary/&gt;</code>|Executions#savebinary]], [[<code>&lt;LoadMemoryDump/&gt;</code>|Executions#loadmemorydump]], [[<code>&lt;SaveMemoryDump/&gt;</code>|Executions#savememorydump]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |

##  Optimize 

```xml
<Optimize .../>
```

 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]), [[Executions]] ([[<code>&lt;Solve/&gt;</code>|Executions#solve]], [[<code>&lt;Adjoint/&gt;</code>|Executions#adjoint]], [[<code>&lt;Optimize/&gt;</code>|Executions#optimize]], [[<code>&lt;Threshold/&gt;</code>|Executions#threshold]], [[<code>&lt;ThresholdNow/&gt;</code>|Executions#thresholdnow]], [[<code>&lt;Repeat/&gt;</code>|Executions#repeat]], [[<code>&lt;LoadBinary/&gt;</code>|Executions#loadbinary]], [[<code>&lt;SaveBinary/&gt;</code>|Executions#savebinary]], [[<code>&lt;LoadMemoryDump/&gt;</code>|Executions#loadmemorydump]], [[<code>&lt;SaveMemoryDump/&gt;</code>|Executions#savememorydump]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `Method=` | Optimization method | Value with unit (NULL) |
| `Material=` | Optional constraint on "amount of material", which is the sum of Topological parameters | Value with unit (NULL) |
| `XAbsTolerance=` |  | Value with unit (NULL) |
| `RelTolerance=` | Relative Tolerance | Value with unit (NULL) |
| `AbsTolerance=` | Absolute Tolerance | Value with unit (NULL) |
| `StopAtValue=` | At what value of the objective to stop | Value with unit (NULL) |
| `MaxEvaluations=` | Maximal number of evalulations (optimizer iterations) | Value with unit (NULL) |

##  Threshold 

```xml
<Threshold .../>
```

Goes with a threshold from 0 to 1. Then for a specific threshold sets all the parameter below the threshold to 0 and above the threshold to 1. Then runs the calculation for the binary (0-1) parameter set.
 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `Levels=` | Number of Levels to calculate between 0 and 1 | Value with unit (NULL) |

##  ThresholdNow 

```xml
<ThresholdNow .../>
```

For a specific threshold sets all the parameter below the threshold to 0 and above the threshold to 1. Then runs the calculation for the binary (0-1) parameter set.
 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `Level=` | Threshold level to apply | Value with unit (NULL) |

##  Repeat 

```xml
<Repeat Times="5">
  <Init/>
  <Solve Iterations="1000"/>
  <VTK/>
</Repeat>
```

A loop element 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `Times=` | Numer of Times to repeat a segment | Value with unit (NULL) |

##  LoadBinary 

```xml
<LoadBinary .../>
```

Load a Field from a binary file (low level) 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `file=` | path to a binary file (without the suffix) | Value with unit (NULL) |
| `comp=` | Field to load from the binary file | Value with unit (NULL) |

##  SaveBinary 

```xml
<SaveBinary .../>
```

Save a Field to a binary file (low level) 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `file=` | the name of the binary file | Value with unit (NULL) |
| `filename=` | full path to the binary file | Value with unit (NULL) |
| `comp=` | Field to save to the binary file | Value with unit (NULL) |

##  LoadMemoryDump 

```xml
<LoadMemoryDump .../>
```

Load all fields from a dump created by Save element 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `file=` | path to a binary file (without the suffix) | Value with unit (NULL) |

##  SaveMemoryDump 

```xml
<SaveMemoryDump .../>
```

Save all fields, to be loaded later on with LoadMemoryDump
Warning: Save and Load Memory Dump have to be used on the *same number of cores*, same model and same precision.
 
Possible children: [[Params]] ([[<code>&lt;Params/&gt;</code>|Params#params]]) 


| Attribute | Comment | Value |
| --- | --- | --- |
| `Iterations=` |  | Value with unit (int) |
| `file=` | the name of the binary file | Value with unit (NULL) |
| `filename=` | full path to the binary file | Value with unit (NULL) |

