# Fusion 360 Probing Cycle: Single Surface XYZ 


![](/images/fp002.PNG)


## Description
Measures the exact position of a X-, Y- or Z-Surface.


## WCS Probing Cycle

```javascript
G65 P9811 A1 X5. Q2. M1. W1. S1
```
### Parameter A: Axis Index
Parameter A is the Axis Index where Axis X=1, Y=2 and Z=3, so A1 in the example above indicates a probing move allong the X-Axis.

### Parameter X, Y or Z: Expected Surface Position 
The value of parameter X, Y or Z indicates the expected position of the surface that has to be probed. 
This parameter must match the Axis Index A, that means if Axis Index is A1, then a X value is expected, for A2 it must be Y and for A3 is must be Z.
The position is calculated by Fusion 360 based on the defined WCS 0 location and the stock/model position of the surface.
If you wonder why the Axis Index A is needed and why not just passing a X, Y or Z value, you have to know that in the CNC12 scipting language a parameter has a default value of 0 and there's no way to differentiate if a parameter is 0 because the parameter has not been used or a value of 0 has been passed.

### Parameter Q: Overtravel Distance
The overtravel distance defines how far the probe is allowed to travel passde the expected surface position before the probing move is aborted with a "*Surface not found*" error.
This value should not be much larger than the position tolerance of the surface.

### Parameter M: Position Tolerance
This parameter defines the position error the surface is allowed to have and works in conjunction with the "*Out of Position*" check box in the Action Tab to stop the WCS probing cycle and display an "*Out of Tolerance*" message.

### Parameter W: Print Results
Possible values are W1 and W2 where W1 just increments the "*Feature*" number while W2 does increment the "*Component*" number and resets the "*Feature*" number to 1.
See [Print Results](ProbePrintResults.md) for more details.



[*Use Browser Back Button to Return*]