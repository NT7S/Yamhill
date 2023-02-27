# Project Yamhill Architecture
Jason Milldrum, NT7S<br/>
Etherkit LLC<br/>
Revision: 27 February 2023

## Overview
Project Yamhill is the successor to the Willamette Transceiver, also known as the qrp-l Group Project. The purpose of this endeavor is to provide a platform to learn about radio electronics at a system level. Modules that correspond to the blocks of a block diagram will be the basis upon which different types of radio designs will be created. A modular 3D printed backplane will be the chassis, user interface, and power supply for the radio experiments. The desired goal is to have a high-performance CW QRP transceiver at the end of the main project run, however there would be the capacity to build many other types of radios from the blocks as desired, such as a SSB transceiver, run more transmit power with a linear amplifier that can provide 20 watts or more, data radio, simple receiver, different architectures such as a phasing receiver, etc.

All designs and code will be permissively open sourced so that an end user is able to build one by himself if desired. All radio design specifications will be published, along with detailed information about how the user can make his own measurements with affordable test equipment to ensure that his radio is performing as expected.

## Backplane
The Yamhill backplane will be the foundation of every radio experiment in this project. Designed to be printed on a consumer-grade FDM 3D printer, it will hold all of the necessary block modules open-air in a reconfigurable grid, have an integrated power supply and power distribution system, have rear connectors needed for a complete transceiver, and house the front panel with the user interface, including microcontroller, LCD display, buttons, encoder tuning knob, etc.

Possibly two sizes, but we're going to start with the largest and see if there is demand for a more compact version.

### Block Module Grid
A grid of mounting holes for M3(?) screws to secure block module PCBs to the backplane will be spaced at 4 cm in each axis, with allowance for 5 mm of margin from the outside board edge at each mounting hole, with a 1 cm x 1 cm x 1 cm cable management channel being provided between each row and column of mounting holes.

Therefore, allowable PCB sizes will be 5 cm x 5 cm, 5 cm x 11 cm, 11 cm x 11 cm, 11 cm x 17 cm, etc.

### Signal Routing
DC power is to be provided by and distributed through a PCB that integrates with the backplane. Channels to be provided in the backplane (1 cm width?) for easy and neat distribution of other signals.

### On-board Rear Panel Connectors
- BNC (x2)
- SMA (x2)
- DC barrel (5.5 x 2.1 mm)
- 3.5 mm TRS (x2)
- USB-C (for UART)

### Front Panel
A front panel PCB will hold most of the user interface and brains of Project Yamhill. This PCB will be populated with:
- Arduino-compatible microcontroller
- Color LCD display module
- Large tuning encoder
- Two smaller encoders (for multifunction, possible AF gain)
- AF gain pot if not encoder controlled
- A plethora of microswitch pushbuttons
- A handful of status LEDs
- Two 3.5 mm TRS jacks
- Microphone jack (RJ-45?)
- Speaker (not sure if front-firing or chassis-mounted)

The front panel PCB will have a USB connection for programming the microcontroller, as well as at least two UARTs available for rig control, debugging purposes, etc., signal routeable to the back panel USB connector.

## Block Modules
Block modules are self-contained PCBs that will perform the functions of a block on the block diagram of a radio. Most components will be SMT, and those modules sold by Etherkit will have the SMT components installed by the manufacturer. Through-hole components such as toroidal inductors and board connectors will be installed by the end user.

### List
- PSU/Power Distribution (special case, backplane integration)
    - 12 V rail, derived from exterior PSU, minimum 1 A
    - 5 V rail, minimum 500 mA(?)
    - 3.3 V rail, minimum 500 mA(?)
    - Power switch
    - LED indicators
    - (optional) Li battery boost and charge
- AF Amplifier
    - 50(?) dB AF gain
    - Able to drive a 1 W speaker or phones
    - AF gain control
    - Sidetone injection
    - Transceive muting
- AF Preamplifier
    - ~40 dB AF gain for use in a DC receiver
- Audio Filter
    - DSP CODEC?
- Double-balanced Diode Ring Mixer/Modulator
    - Option for higher than level 7?
- KISS Mixer
- Crystal Ladder IF Filter
    - Various bandwidths available for SSB, CW, roofing
- IF Amplifier with AGC
- Receive Bandpass Filter
- Transmit Low-pass Filter
- Transmit/Receive Switch
- Wideband Oscillator
    - Most likely Si5351C, but open to options
- Transmit Preamplifier
- QRP Transmit Linear Amplifier
    - Maximum power output 5 W
- Higher Power Transmit Linear Amplifier
    - Maximum power output 20 W
- GPS Receiver
    - 10 MHz ref out
    - 1 PPS out
- SWR Bridge
- S-meter Detector
- Signal Distribution(?)

### Inter-module RF Signal Interconnects
Type TBD

### Inter-module DC/AF Signal Interconnects
Type TBD

## Proposed Learning Units
- Direct Conversion Receiver
- QRP CW Transmitter
- Superheterodyne CW QRP Transceiver
- WSPR Transmitter
- Superheterodyne SSB/CW QRP Transceiver

## QRP CW Transceiver Target Specifications
TBD

## Expected Required Test Equipment
- DVM
- Oscilloscope
- Spectrum analyzer such as tinySA
- VNA such as nanoVNA