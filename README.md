# USB CDC (Virtual COM port) demo for Microstick II

Trivial USB CDC (Virtual COM port) demo, for Microstick II board,
generated with MCC.

WORK IN PROGRESS!

Requirements:
- insert PIC24FJ64GB002 into Microstick II socket
- PGM Switch should be in position `A` - PGC1, PGD1
- additionally you need `USB breakout cable`

![Microstick II as USB Device](https://raw.githubusercontent.com/hpaluch/pic24fj-usb-cdc-mcc.X/master/assets/microstick2-usb-cdc.jpg)

Need to connect:
```
USB Cable
Color Signal    Microstick II
                P1 (or U5)    and/or J6
==============================================
BLACK GND    -> PIN 8         also PIN 1 on J6
GREEN D+     -> PIN 21        also PIN 4 on J6
WHITE D-     -> PIN 22        also PIN 5 on J6
RED   +5V    -> 100OHm resistor  to PIN 15 - Vbus (sensing)
```
And:
Vdd from TP1 to PIN23 Vusb (supply for on-chip USB)

Please see https://ww1.microchip.com/downloads/en/DeviceDoc/39721b.pdf
figure `Figure 27-5: Self-Power Only`

Software used:
- MPLAB X IDE v5.45
- MCC plugin 4.0.2
- XC16 v1.70
- DFP: `PIC24F-GA-GB_DFP 1.4.141`

Installing Device Driver - in Device Manager:
* Other Devices -> `Product Name`
* Update driver...
* Use driver from sub-directory:
  ```
  mcc_generated_files\usb\utilities\Readme Signed Driver Package.txt
  ```
* I by accident use this - from MLA library:
  ```
  mla\v2018_11_26\apps\usb\device\cdc_basic\utilities\inf
  ```
* Device Must change to: Ports -> `USB Serial Port (COMx)`


Now fire up any terminal on COMx port (for example putty.exe)
and when you press any ASCII character it should output +1 character
(for example `b` for typed `a`). For details please
see:

```
mcc_generated_files\usb\example_mcc_usb_cdc.c 
```






