#  Geometry Primitive 
##  Box 

```xml
<Box .../>
```

 

| Attribute | Comment | Value |
| --- | --- | --- |

##  Pipe 

```xml
<Pipe .../>
```

 

| Attribute | Comment | Value |
| --- | --- | --- |

##  Wedge 

```xml
<Wedge .../>
```

 

| Attribute | Comment | Value |
| --- | --- | --- |
| `direction=` |  | Value with unit (NULL) |

##  STL 

```xml
<STL file="geometry.stl" scale="1m" x="10" side="out"/>
```

Imports a STL file as geometrical object. The element works in two modes. In the first mode, it fills elements inside or outside of the STL geometry (casting rays along some axis). In the second mode (`side="surface"`) it fills elements touching the geometry (on both sides) and **calculates the cuts* for Interpolated-BounceBack-type conditions.
 

| Attribute | Comment | Value |
| --- | --- | --- |
| `file=` | STL file to import | Value with unit (NA) |
| `side=` | Specifies if to fill the interior (in), exterior (out), or the surface (see description) | Value with unit (NULL) |
| `ray_axis=` | Specifies the axis along which rays will be cast for in/out filling of STL | Value with unit (NULL) |
| `scale=` | Specifies the scale by which the STL geometry should be multiplied. If you work in physical units, this can be e.g. "1m" | Value with unit (float) |

