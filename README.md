# Board Details

* MCP2515 SPI CAN Controller: Provides the missing CAN peripheral for the Feather SAMD21. Compatible with the [MCP2515 Arduino Library](https://github.com/autowp/arduino-mcp2515) initialising with `CS #6` and `INT #5`. The track to `#5` can be cut if the user does not require interrupts and wishes to use the pin for something else. 16 MHz crystal used for high-data rate capture.
* MCP2551 CAN Transceiver: Front-end for the differential CAN signals, 24 V compliant and upto 1 Mb/s data-rate. Slope-control can be configured with R2, by default it is configured in high-speed mode. I like this chip as it also acts as a signal buffer, providing ESD protection up-to 6 kV, +/-250 V transient protection and short-circuit protection, meaning no additional on-board protection is required. A 120R termination resistor is on-board but not connected by default (a solder link is provided to being in circuit). UPDATE: I've now routed the transeiver RX/TX to pins `#9` and `#10` so that the _STM32 Feather_ can use the on-board CAN peripheral rather than MCP2515.
* RX/TX LEDS: I've tied pull-up LEDs on the transmission lines between the MCP2515 and MCP2551 to provide indication of activity. They should not degrade the signal as they are low current (2 mA) but can be removed if edges are lost at high-speed.
* MCP1703T-5002E: 5 V LDO provides power to the Feather via __VUSB__ given a source of 5-16 V. The board __3V3__ is then powered by the Feather's on-board 3V3 regulator. __NOTE__ VIN should not be supplied with __VUSB__ to avoid back-powering the USB port.
* DS3231: Commonly used high-accuracy RTC module with on-board CR1220 back-up battery. Compatible with the [DS3231 Arduino Library](https://github.com/JChristensen/DS3232RTC).
* Hand-drawn silk art! Something I did on the train, inspired by feather's and bikes! CAN is synonymous with the automotive industry so I wanted to put a bike spin on things...

## Potential Improvements for Mass Assembly

* Make 0603 passives 0402.
* Use same CR1220 holder as Adafruit RTC Wing.

# Availability

I have some bare boards in fabrication at the moment, which I plan to hand-assemble for my own use. If there is interest, I will get an assembly run done (unless it wins the competition of course!) after this validation.
