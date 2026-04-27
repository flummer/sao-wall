# SAO Wall

This is a design for a large PCB (300x400mm) with 16 SAO connectors to work either as a standalone display (fits in an IKEA RÖDALM picture frame) or be monted along with other panels to form a larger wall for displaying many SAOs.

This is heavily inspired by [Brian Benchoffs SAO Wall](https://bbenchoff.github.io/pages/ShittyWall.html), that has been used at several Supercon events, but this design does a few things slightly different, not least the power setup.

## Main concept and idea

The design is separated into two parts:

- SAO Connector board, which is the large PCB, that has all the connectors, polyfuses for each output and then a set of connectors for hooking up to the 4 power rails, the 2 I2C busses and all the GPIO pins for all SAOs
- USB-C PD and Pico controll board is the smaller board that has the voltage regulators (4x AP63203WU-7 buck converters), USB-C PD controller (STUSB4531) and a footprint for a Raspberry Pi Pico (1 or 2).

The setup with two boards is done so that the more generic part (the connector PCB) that is also a bit on the expensive side can be ordered once and maybe a combined order for multiple people, and then the more opinionated element with the powering circuit and maybe a micro controller can be easier made in low volume (most simple is a piece of proto board and a simple 3.3v poser supply).

The USB-C PD power setup that is included here is meant to work nicely with most USB-C power supplies and at the same time be able to power all 16 SAOs to the full specification of the SAO standard (250mA @ 3.3V for each SAO).

The Raspberry Pi Pico is connected very similar to hos the [Hackaday SAO Badge]() was made, with 2 I2C busses (using the same pins) and hooked up to GPIO pins of most of the SAOs (10 out of the 16) as there is a limited number of available connections on the Pico. It's not 100% pin compatible with the Hackaday SAO Badge, but it should be an easy tweak if you would like to run the same firmware.


## Designed in KiCad v10

To open the project, you will need to install the most recent release (v10), KiCad v9 or earlier won't open this design directly.

[Electronics schematics for the connector board as a PDF file](https://github.com/flummer/sao-wall/blob/main/sao-connector-board-schematics.pdf) and [Electronics schematics for the USB-C PD and Pico control board as a PDF file](https://github.com/flummer/sao-wall/blob/main/usb-pd-pico-controller-schematics.pdf) are included for reference.


## License

The hardware design of the `main` branch of this repository is released under the following license:

* the "Creative Commons Attribution-ShareAlike 4.0 International License"
  (CC BY-SA 4.0) full text of this license is included in the LICENSE file
  and a copy can also be found at
  [http://creativecommons.org/licenses/by-sa/4.0/](http://creativecommons.org/licenses/by-sa/4.0/)
