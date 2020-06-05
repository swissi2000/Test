# Fusion 360 Probing Customization Parameters 

## Description
Many features of the Fusion 360 Probing Cycles for Centroid can be customized. 

All the parameters that can be customized are located in the script file

```javascript
C:\cncm\probing\probe_initialize.cnc
```

All the configuration parameters related to Fusion 360 Probing Cycles are in a dedicated, marked section.

## Fusion 360 Probing Configuration Parameters

This is the customization section of the configuration file "*C:\cncm\probing\probe_initiliza.cnc*":

```javascript
;--------------------------------------------------------------------------------------------
; Fusion 360 Probing Cycle Parameters
;--------------------------------------------------------------------------------------------
#381   = "c:\cncm\ncfiles\probing-report.log" ; log file to record Fusion 360 probing results
#33998 = 0   ; 0=Fast Probing Move first then slow, 1=skip fast probing move and do only slow
#33997 = 0   ; Display WCS measurements before setting WCS. -1=No display, 0=message needs to be confirmed with Cycle Start, >0=Wait time in seconds
#33996 = 0   ; Display Geometry measurements. -1=No display, 0=message needs to be confirmed with Cycle Start, >0=Wait time in seconds
#33995 = 0   ; Display Tool Wear adjustment message. -1=No display, 0=message needs to be confirmed with Cycle Start, >0=Wait time in seconds
;#33994      ; Reserved for Feature # used for Printing Function
#33993 = 155 ; non volatile user parameter that keeps component # for probing log (possible 150 - 159)
#33992 = 0   ; Out of Tolerance Messages: -1 = do not show, 0 = wait for confirmation, >0 = display time in seconds
#33991 = 0   ; Display CSR Actiove Warning Message, 0 = Display, 1 = Do not display
#33990 = 0.5 ; Max. Tool Wear adjustment allowed (always in mm). 0=No Limit. No adjustment will be made if this amount is exceeded and a warning message will be presented
```

### Print File Name (#381)
The user text variable #381 specifies the file name used to print/log probing results if this function was selected in the Fusion 360 probing cycle. 
Any valid file name can be used. The default file name is:

```javascript
#381   = "c:\cncm\ncfiles\probing-report.log" 
```

### Fast/Slow Probing Sequence (#33998)
This parameter allows to configure the preferred probing sequence. 

Options are:

```
0 = (Default) Fast probing move first followed by a slow probing move
1 = Slow probing move only
```

### Display WCS Measurements (#33997)
This parameter allows to customize the way WCS Measurements are displayed before WCS is set.

Options are:

```
-1 = No display. WCS will be set without showing WCS Measurements
0  = (Default) WCS Measurements are displayed and need to be confirmed with *Cycle Start* 
>0 = A value larger than 0 will indicate the number of seconds the WCS Measurements will be displayed before automatic continuation
```


[*Use Browser Back Button to Return*]