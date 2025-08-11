# Multimeter HP 34401A

* HP 34401A
* Agilent 34401A
* Keysight 34401A

## SCPI 

Notes: 

* After using `DISPLAY OFF` SCPI command 0.3s delay needs to be added before procedeeing with another command
* When Autorange kicks in, delay must be added before starting measurment.
* I am adding 0.5s delay after voltage is changed on voltage source. One to sattle voltage, two for DMM to change ranges if needed and settle as well.
* Range switches after measurement is "INITiated". Query for currently used *range* after "INIT" -> "FETCH?"
  
## How to Achieve the Fastest Sample Rate for the Keysight 34401A DMM

Source: https://docs.keysight.com/kkb/how-to-achieve-the-fastest-sample-rate-for-the-keysight-34401a-dmm-588260753.html

When configured for the fastest reading rate, the 34401A can sample at 1000 readings/second. To configure it to this mode, you must:

* Measure either DC Volts, DC Current, 2-wire or 4-wire Resistance
* Turn off the display
* Set to 4.5 digit fast
* Turn off autozero
* Turn off autorange
* Turn off all math
* Set the delay to 0
* Set the trigger source to immediate
* VOLTage:DC
* CURRent:DC
* RESistance
* FRESistance

From computer control the following instrument commands should be used to set up the 34401A. In place of <function> use the command for the measurement you wish to make:

```scpi
*RST
*CLS
DISPlay OFF
FUNCtion "<function>"
<function>:RESolution MAXimum
<function>:NPLCycles MINimum
ZERO:AUTO OFF
<function>:RANGe:AUTO OFF
CALCulate:STATe OFF
TRIGger:SOURce IMMediate
TRIGger:DELay 0
READ? 
```
