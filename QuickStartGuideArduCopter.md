# APM 2 & 2.5 Quick Start Guide ArduCopter #
  1. **Check requirements first!**
> > You need a Graupner HoTT v4 compatible receiver / transmitter both with the **latest firmware version**. The implementation for ArduPilot is developing and testing using following environment:
      * MC-32 firmware v1.030
      * GR-16 firmware v6a10\_f9
      * GR-12 firmware v3a40\_e9
  1. If you prefer to deploy a precompiled ArduPilot package please continue [here](HEXUpload.md) and after that skip to the next chapter how to create a patch cable.
  1. Download the Hott.pde and UserCode.pde files from the project website and copy it to you ArduCopter source directory ie. ardupilot-mega/ArduCopter
  1. Edit APM\_Config.h file and add following line to bottom of the file:
```
#define HOTT_TELEMETRY
#define HOTT_TELEMETRY_SERIAL_PORT	2
#define HOTT_SIM_GPS_SENSOR
#define HOTT_SIM_EAM_SENSOR
#define HOTT_SIM_VARIO_SENSOR
#define HOTT_SIM_GAM_SENSOR
//Use HoTT Alarms
#define HOTT_ALARMS

```
> > In this example we are using APM2 serial port 2.
  1. Add Hott.pde Arduino project

> Launch Arduino and load the ArduCopter sketch. Add Hott.pde file to this project by opening the Hott.pde file in Arduino. Compile and deploy the ArduCopter code.
# Connect HoTT receiver to APM2 #
  1. Create a patch cable
> > Create  patch cable with shorted RXD uand TXD pins on one side and removed middle (power) wire on the other side.
```
 APM2      HoTT receiver
 
 RXD -------+-- Telemetry
 TXD -1.5k -|
 GND ---------- GND
```
  1. Connect the HoTT telemetry port from the receiver (marked with a capital T) to the selected APM2 serial port (usually port 2). Plug the side with the connected RXD/TXD wires to APM2 and the other side with the removed  wire in the middle to the HoTT receiver. RXD/TXD are not connect directly but via a 1.5k resistor (thanks to Michael for this suggestion).


> _Note: The patch cable doesn't really requires the 1.5k resistor in series between TXD & RXD since the serial bus is specified up to 5v which has been confirmed by Graupner , but it is "best practice"._
> The patch cable:

> ![http://wiki.hott-for-ardupilot.googlecode.com/git/images/PatchCable2Details.png](http://wiki.hott-for-ardupilot.googlecode.com/git/images/PatchCable2Details.png)

> A picture from the receiver. There is no wire in the middle on the receiver side!
> ![http://wiki.hott-for-ardupilot.googlecode.com/git/images/PatchCable.png](http://wiki.hott-for-ardupilot.googlecode.com/git/images/PatchCable.png)

> And on the APM2 side:

> ![http://wiki.hott-for-ardupilot.googlecode.com/git/images/PatchCable_on_APM2.png](http://wiki.hott-for-ardupilot.googlecode.com/git/images/PatchCable_on_APM2.png)