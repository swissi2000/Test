# Fusion 360 Probing

![](/images/fp001.PNG)

## Description
Fusion 360 has the capability to add WCS and Geometry Probing cycles directly into your program together with the Tool Path operations. 
WCS Probing routines can be used to speed up or even automate robust stock setups while Geometry Probing routines can be used to check features for position and size tolerance and automatically adjust tool diameters and tool offset heights for tool wear.

This guide does not cover how to use the Fusion 360 probing cycles and just goes into details how the different options that are available within the Probing Cycles do effect the Centroid specific implementation of the probing functionality.
If you are unfamiliar with the Fusion 360 probing functionality, there's plenty of information on the Internet. Here are just a few examples:

* [Fusion 360 Probing Lesson](https://youtu.be/CGCSAOqCFjM) 
* [WCS Stock Probing Tutorial](https://youtu.be/STJ_m2lTEZ8)
* [WCS Probing for robust Setups](https://youtu.be/vZnPwe3ZqwE)

## Implementation Details
One requirement for the Fusion 360 Probing functions to work is that the Post Processor needs to support the Probing Functionality but that's just the easy part. 
Looking at the output the post processor generates for the probing routines reveals the more difficult part.
Here's an example of the generated blocks:

```javascript
(PROBE WCS Y-SURFACE)
N30 T10 M06
N35 G54
N40 G00 A0.
N45 G00 X9.117 Y-5.5
N50 G43 Z15. H10
N55 G65 P9832
N60 G65 P9810 Z5. F1000.
N65 G65 P9810 Z-12.
N70 G65 P9811 Y0. Q2. M1. W1. S1.
N75 G65 P9810 Z5.
N80 G00 Z15.
N85 G65 P9833
```

As seen in the example above, the probing commands are just subprogram calls in the form of P98xx with a bunch of parameters and these subprogram don't exist for the Centroid Acorn board.
I took on the challange to write probing cycles to fully implement the functionality of the Fusion 360 WCS and Geometry probing cycles supporting all available options.
Contact me if you are interested in these probing routines.
 
## Supported Probing Cycles
The following WCS and Geometry Probing Cycles are supported:

* [Single Surface Probing XYZ (P9811)](ProbeSingleSurface.md)
* [Wall/Web Probing XY (P9812)](ProbeWall.md)
* [Channel/Slot Probing XY (P9813)](ProbeChannel.md)
* [Circular Boss Probing XY (P9814)](ProbeCircularBoss.md)
* [Circular Hole Probing XY (P9817)](ProbeCircularHole.md)
* [Rectangular Boss Probing XY (P9812 C1)](ProbeRectangularBoss.md)
* [Rectangular Hole Probing XY (P9813 C1)](ProbeRectangularHole.md)
* [Inner Corner Probing XY (P9815)](ProbeInnerCorner.md)
* [Outer Corner Probing XY (P9816)](ProbeOuterCorner.md)
* [Plane Angle Probing XY (P9843)](ProbeAngle.md)

## Special Probing Functions
In addition to the probing cycle sub-programs above, there are these supporting sub-programs:

* [Protected Probe Move (P9810)](ProbeProtectedMove.md)
* [Probe Start/Initialize (P9832)](ProbeInitialize.md)
* [Probe Stop (P9833)](ProbeStop.md)

## Reporting/Print Function
The WCS as well as the Geometry Probing Cycles do have a reporting function to record/print probing results to a log file.

See [Reporting/Print Function](ProbeReporting.md) for more details.  

## Probing Cuctomization
Many aspects of the probing cycles can be customized.

See [Probing Customization](ProbeCustomization.md) for all the possible configuration options.


[Back](index.md)

