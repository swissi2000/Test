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

```
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

* [Single Surface Probing XYZ](ProbeSingleSurface.md)
* [Wall/Web Probing XY](ProbeWall.md)
* [Channel/Slot Probing XY](ProbeChannel.md)
* [Circular Boss Probing XY](ProbeCircularBoss.md)
* [Circular Hole Probing XY](ProbeCircularHole.md)
* [Rectangular Boss Probing XY](ProbeRectangularBoss.md)
* [Rectangular Hole Probing XY](ProbeRectangularHole.md)
* [Inner Corner Probing XY](ProbeInnerCorner.md)
* [Outer Corner Probing XY](ProbeOuterCorner.md)
* [Plane Angle Probing XY](ProbeAngle.md)

### Display a Message
Display a message on the monitor by adding 
```
M200 "Ready to start the Job?\n\nPress Cycle Start to continue\nRESET to Cancel"
```

![](/images/pp003.PNG)

This provides additional machine protection by giving a chance to cancel the Job if *Cycle Start* has been pressed by accident.

### Execute a Macro
There are several options to execute a Macro. An easy way is to use one of the available *mfuncxx.mac* files like *mfunc51.mac* and *mfunc52.mac* to execute multiple Commands. A simple *M51* or *M52* command can then be entered in the Property field to have the macro executed.

Another option is to use a M98 command to call a subprogramm/macro like this:

```
M98 "C:\cncm\ncfiles\begin.cnc"
M98 "C:\cncm\ncfiles\end.cnc"
```
In combination with the [Property: Write CNC12 Info Variables](CNC12.md), there are very creative ways to make use of this functionality. To get some ideas, look at the following example.

### Usage Example
This example will display an Information Screen at the start of a job file and will record the Date, Time, Run-Time-Length as well as the Name and Version Number of the Fusion 360 CAM File the job was created with, to a log file. The log file does have the same name as the job but with a .log extension and will be in the same directory as the job file. Modify the scripts to your needs.

Set the following Properties in the Post Processor:

```
Property: Add Command to Begin of Job = M98 "C:\cncm\ncfiles\begin.cnc"
Property: Add Command to End of Job   = M98 "C:\cncm\ncfiles\end.cnc"
Property: Write CNC12 Info Variables  = Yes
```
Get the files *begin.cnc* and *end.cnc* from the [Repository](https://github.com/swissi2000/Test) and copy them to the *C:\cncm\ncfiles* folder.

When running a job in CNC12 that was created with these Property settings, CNC12 will present an Info Message when the *Cycle Start* button is pressed:

![](/images/pp004.PNG)

The Info Message does give the following information:

* Fusion 360 CAM File Name
* Program Name
* Program Comment
* Setup Name
* Setup Notes if any where entered
* Origin Point (Part Zero) in relation to Stock Coordinates
* WCS
* List of Tools used in the Job (limited to first 10 Tools)

The log file 1001.log will look like this:

```
1001.log

    Run Date: Sat May 11 10:05:34 2019
    Based on CAM File: Lift Plate v10
    Run Time:  0:06:15

    Run Date: Sat May 18 11:30:59 2019
    Based on CAM File: Lift Plate v11
    Run Time:  0:04:23

```    

Goto [Property: Write CNC12 Info Variables](CNC12.md) for more details about what Fusion 360 information will be available in CNC12. 
Also check out the chapter [Support for Manual NC Commands](manualNC.md) for more options to inject commands into a job file.


[Back](index.md)

