# Rotary Table Axis

![](/images/pp016.PNG)

## Description
This Property allows to enable a rotary axis in the Post Processor. The default Property setting is *No rotary*. Do not enable this Property if no *A, B or C* axis has been configured in CNC12. 

Possible options are:

* No Rotary (Default)
* Along +X (A Axis)
* Along +Y (B Axis)
* Along +Z (C Axis)
* Along -X (A- Axis)
* Along -B (B- Axis)
* Along -Z (C- Axis)

This graphics is showing the positive directions of all the axis:

![](/images/pp017.JPG)




## Implementation Details
The default value is *G28*. Selecting *No Move* can be dangerous and is not recommended. Use it at yourt own risk!

The coordinates of the *G28* and *G30* commands can be configured in CNC12 under *Setup[F1]->Part[F1]->WCS Table[F9]->Return[F1]*

![](/images/pp014.PNG)

The default values in CNC12 for *G28* and *G30* for all axis is *0*, so by default the machine will return to the *Z0* position at the end of the job.

Choose one of the available Return-Options and modify the return coordinates in CNC12 as required.


[Back](index.md)