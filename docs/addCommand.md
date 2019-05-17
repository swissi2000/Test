# Add Command to Begin/End of Job
## Description
This allows to add one M Command (CNC12 accepts only one M Command per block/line) or multiple G Commands.

![](/images/pp002.PNG)

## Implementation Details
The text entered in this property field must start with a M or a G followed by a number. If this is not the case, the text will be added to the job file as a comment. So this property does allow to add a comment to the job file at the beginning and the end instead of a command.

If the entered text does start with a M or G followed by a number, the whole line will be written as a block/line to the job file without further syntax check. If the string does contain something CNC12 doesn't like, CNC12 will stop the execution of the job file with an error message.

## Use Cases
This feature does give you a lot of flexibility of how to use it. These are just a couple of options:

### Display a Message
You can display a message on your monitor by adding 
'''
M200 = "My Message goes here.\n\nPress Cycle Start to continue"
'''


[Back](index.md)

