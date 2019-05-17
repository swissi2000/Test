# Add Command to Begin/End of Job
## Description
This allows to add one M Command (CNC12 accepts only one M Command per block/line) or multiple G Commands.

![](/images/pp002.PNG)

## Implementation Details
The text entered in this property field must start with a M or a G followed by a number. If this is not the case, the text will be added to the job file as a comment. So this property does allow to add a comment to the job file at the beginning and the end instead of a command.

If the entered text does start with a M or G followed by a number, the whole line will be written as a block/line to the job file without further syntax check. If the string does contain something CNC12 doesn't like, CNC12 will stop the execution of the job file with an error message, so be careful that the command string is valid.

## Use Cases
This feature does give a lot of flexibility of how to use it. These are just a couple of options:

### Display a Message
Display a message on the monitor by adding 
```
M200 "My Message goes here.\n\nPress Cycle Start to continue"
```

### Execute a Macro
There are several options to execute a Macro. An easy way is to use one of the available mfuncxx.mac files like mfunc51.mac and mfunc52.mac to execute the desired Commands. As seen in the screenshot above, a simple M51 or M52 command can then be entered in the Property field to have the macro executed.

Another option is to use a M98 command to call a subprogramm/macro like this:

```
M98 "C:\cncm\ncfiles\begin.cnc"
M98 "C:\cncm\ncfiles\end.cnc"
```
In combination with the [Property: Write CNC12 Info Variables](CNC12.md), there are very creative ways to make use of this functionality as shown in the example below.

### Usage Example
Set the following Properties in the Post Processor:

```
Property: Add Command to Begin of Job = M98 "C:\cncm\ncfiles\begin.cnc"
Property: Add Command to End of Job   = M98 "C:\cncm\ncfiles\end.cnc"
Property: Write CNC12 Info Variables  = Yes
```



[Back](index.md)

