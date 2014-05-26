nRF51822-cli
==================

Provides a build system for nRF51822 projects.

Handles
- Compilation
- Flash Programming
- SoftDevices

Heritage
---------

There are several similar projects available such as [this](https://github.com/hlnd/nrf51-pure-gcc-setup), [that](https://github.com/pauloborges/nrf51822-linux-template), and the [other](https://github.com/EarthLord/nrf51Demo). Each has their own merits.

This project aims to be as simple and well documented as possible, for example, the very concise JLink shorthand commands are expanded and [written more naturally](linky).

In practice:
- ./erase
- ./flash <SoftDevice> <Application>

The flash command takes as arguments a SoftDevice and an application.
- An internal lookup table determines the code offset for the given SoftDevice.
- The application is checked for SoftDevice compatibility.
- Both are flashed to the device.

The erase command takes no arguments.
- Erasing both region0 and region1 areas, if defined.
- Erasing the User Information Configuration Registers.


Requirements
------------

- nRF51 SDK
- S110 SoftDevice
- SEGGER JLink
- nRF51822 Evaluation Kit board PCA1001

In each case, there are multiple versions of these available. The code should be easily modifiable to support them.
