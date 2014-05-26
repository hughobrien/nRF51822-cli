nRF51822-cli
============

Provides a GCC based build system for [nRF51822](https://www.nordicsemi.com/eng/Products/Bluetooth-R-low-energy/nRF51822) projects. 

Handles:
- ~~Compilation~~ (working on it)
- Flash Programming
- SoftDevices

Heritage
---------

There are several similar projects available such as [this](https://github.com/hlnd/nrf51-pure-gcc-setup), [that](https://github.com/pauloborges/nrf51822-linux-template), and the [other](https://github.com/EarthLord/nrf51Demo). Each has their own merits.

This project aims to be as simple and well documented as possible, for example, the [very concise](https://github.com/pauloborges/nrf51822-linux-template/blob/master/scripts/erase.jlink) JLink shorthand commands are expanded and [written more naturally](https://github.com/hughobrien/nRF51822-cli/blob/master/flash).

I previously used TI's [CC2540](http://www.ti.com/tool/cc2540emk) but their design [all but requires](http://e2e.ti.com/support/wireless_connectivity/f/538/t/195635.aspx) the purchase of a commercial IDE. Thankfully Nordic saw sense.

Usage
-----
In practice:
<pre>./erase</pre>
<pre>./flash SoftDevice Application</pre>

flash:
- An internal lookup table determines the correct code offset for the given SoftDevice.
- The application is checked to see if it was linked against a SoftDevice.
- Both are flashed to the chip.

erase:
- Erases both region0 and region1 areas, if defined.
- Erases the User Information Configuration Registers.

Tests
-----
Using the [Nordic NRFGo Studio](http://www.nordicsemi.com/chi/node_176/2.4GHz-RF/nRFgo-Studio) both the SoftDevice and the application binaries were read from the flashed chip and successfully verified against the original hexfiles.

Requirements
------------

- [nRF51 SDK](https://www.nordicsemi.com/eng/Products/Bluetooth-R-low-energy/nRF51822)
- [A SoftDevice, s100v5/v6/v7, s120](https://www.nordicsemi.com/eng/Products/Bluetooth-R-low-energy/nRF51822)
- [SEGGER JLink](http://www.segger.com/jlink-software.html)
- [nRF51822 Evaluation Kit board PCA1001](http://www.nordicsemi.com/eng/Products/Bluetooth-R-low-energy/nRF51822-Evaluation-Kit)
- [GNU Tools for ARM](https://launchpad.net/gcc-arm-embedded)

In each case, there are multiple versions of these available. The code should be easily modifiable to support them.
