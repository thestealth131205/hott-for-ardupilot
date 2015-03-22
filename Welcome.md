# Introduction #

_HoTT for ArduPilot_ is a Graupner HoTT v4 telemetry protocol implementation for ArduCopter.


# How it works #
Graupner HoTT telemetry protocol uses a one wire bus to communicate with different telemetry module profiles. The RC receiver polls every attached module on bus for telemetry data in a round-robin manner. The response from a module is transfered back to the RC transmitter. For more details see [Graupner homepage HoTT announcement](http://www.graupner.de/en/newsdetail/6adb64b6-0a32-443d-bf32-678d599ded4d).

_Note: A module is a set of defined sensors for temperature, RPM, current etc._

The acutal implementation includes following module profiles:
  * [GPS](GPSProfile.md)
  * EAM _Electric Air Module_
  * GAM _General Air Module_
  * VARIO _Vario module_

Each profile can be deactivated/activated in the source code, so you can also use the code together with a "real" existing HoTT module and let ArduPilot process all other profiles.

**Developed for AMP2 hardware. Not tested with APM1.**

# Current status #
**Note:** _The development has been stopped for ATmega versions of APM. Why? Because of the very limited resources left on the Atmel device. Since the timing is very critical for the APM performance, doing "some extra stuff" can easy leads to a non-functional APM and a crash. The latest version for ArduCopter < 2.9 is v0.9.7.2b._

  * [Binary mode ](HoTT_Binary_mode.md) implemented
  * [Text mode ](HoTT_Text_mode.md) implemented but unused now.
  * Alarms (since v0.9.3b)
  * **PX4 / Pixhawk version** Development moved to GitHUB  see https://github.com/3yc/hott-for-ardupilot

Things to come:
  * Documentation
  * ArduPlane version
  * PX4 / Pixhawk version for the latest stable ArduCopter (v3.1.2)

# Where to start #
> Check [Quick Start Guide](QuickStartGuideArduCopter.md) for ArduCopter.

# Technical details #
> Check [detail page](TechnicalDetailHoTT.md) for more info.