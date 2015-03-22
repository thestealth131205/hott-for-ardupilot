# Technical details #

  * Overview
> The one wire serial bus which HoTT is a 19200 baud 8N1 serial UART. Graupner itself uses 3.3V as in/out level, the confirmed max. input voltage is 5V (TTL levels).

  * Timing
> HoTT uses a single wire bus to communicate with sensors and receiver. The receiver pools the sensor every 200ms for data. In text mode each sensor is queried every 800ms according to the specs, but this value is not very stable.

> # Binary mode #
> ![http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets.png](http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets.png)

> Each sensor is queried two times in a 200ms period before the HoTT receiver moves to the next sensor.

> ![http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets_detail.png](http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets_detail.png)
> The 5ms "Idle line" is required by HoTT specs to prevent false answers to request.

> ![http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets_detail2.png](http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets_detail2.png)
> ![http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets_detail2_3ms.png](http://wiki.hott-for-ardupilot.googlecode.com/git/images/HoTTPackets_detail2_3ms.png)

> HoTT specifies also a 2ms delay between data packets. (Ok it's 2.48ms in the screenshot :) ) Graupner modules itself (tested on a GEM module) uses a 3ms delay here...

> The whole request+answer takes at 19200 baud (8N1) in binary mode about **120ms**.
> In text mode it requieres ca. **440ms** to finish a transaction. As you can see, it's not the fastest one.

# Bus scan #
The new HoTT implementation uses a bus scan for HoTT modules, so it's not longer possible to select them in your transmitter. The scan is initiated after the transmitter has been turned on. The scan loops thru all possible module id's and if it receives a valid answer, the module is marked as available in the transmitter.

**Note:** You can force to the rescan the bus by goining into the Telemetry menu in your transmitter and "reelect" the HoTT telemetry receiver.