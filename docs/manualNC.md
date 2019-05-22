# Fusion 360 Manual NC Commands

## Description
Logic has been added to the Post Processor to support the following *Manual NC* commands in Fusion 360:

* Comment
* Display Message
* Pass through
* Call program

Manual NC commands can be added anywhere in the Fusion 360 CAM Browser structure:

![](/images/pp044.PNG)

## Implementation Details

### Comment
This command gives the option to place comments into the job file. The formatting of the comment will be based on the [*Property: Comment Line Formatting*](commentFormatting.md).

![](/images/pp045.PNG)

The job file will look like this:

```javascript
.
.
N5160 G0 Z50.
(Comment placed before Finish Outside Contour)
(Finish Outside Contour)
N5270 X73.233 Y-56.101
N5275 Z15.
.
.
```

### Display Message
This command gives the option to display a message on the screen. The job execution will stop until the message is been confirmed with a Cycle Start command.

![](/images/pp046.PNG)

The job file will look like this:

```javascript
.
.
N5160 G0 Z50.
(Comment placed before Finish Outside Contour)
(Finish Outside Contour)
N5270 X73.233 Y-56.101
N5275 Z15.
.
.
```


[Back](index.md)