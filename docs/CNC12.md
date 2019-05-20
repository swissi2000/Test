# Write CNC12 Info Variables

![](/images/pp019.PNG)

## Description
CNC12 offers 100 internal *User-String-Variables* that can be used by macros during job execution. The names of these variables are *#300 - #399*.

If this *Property* is enabled, the Post Processor will fill *User-String-Variables* with Information from Fusion 360 that can be used within CNC12. By default, the following information will be written to the job file:

```javascript
// File, Setup and Tool Path Information
#300 Holds Tool Information from the Fusion 360 Tool Library. Updated before each Tool Change
#301 Holds the Fusion 360 Design File Name. Defined at the beginning and does not change
#302 Holds the Fusion 360 Program Name/Number as specified in the Post Window
#303 Holds the Fusion 360 Program comment as specified in the Post Window
#304 Holds the Fusion 360 Setup Name. Changes for each Setup in the Post
#305 Holds the Fusion 360 Setup Notes. Changes for each Setup in the Post
#306 Holds the Fusion 360 Tool Path Name. Changes for every new Tool Path
#307 Holds the Fusion 360 Tool Path Notes. Changes for every new Tool Path

// Tool Info from the Fusion 360 Tool Library. Updated before each Tool Change in the Post
#308 Tool Type 
#309 Tool Unit (mm or in) 
#310 Tool Diameter
#311 Number of Flutes
#312 Tool Coolant
#313 Tool Description from General Tab of Tool Settings
#314 Tool Comment from Post Processor Tab of Tool Settings

//Feed and Speed Info. Updated before each Tool Change in the Post
#315 Spindle Speed
#316 Spindle Direction CW or CCW
#317 Optimal Load (WOC)
#318 Maximum Step Down (DOC)
#319 Feed Rate
#320 Feed per Tooth
#321 Ramp Feed Rate
#322 Plunge Feed Rate
#323 Feed per Revolution

//Setup Info. Updated for each new Setup in the Post
#324 Origin Point
#325 Z Clearance Height. Useful to display the distance when checkApproach Property is used
#326 Current WCS

// First 10 Tools made available in variables when both Properties "writeTools" and "writeCNC12Vars" are true and variable name is assigned
#351 - #360 Variable that will hold the Fusion 360 Tool Info for the first 10 Tools used

```

## Implementation Details


[Back](index.md)