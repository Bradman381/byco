---
title: Hexapedal Robot
brief: A bluetooth-controlled six legged robot.
thumbnail: /assets/images/thumbnail_rhex.jpg
year: 2016
order: 100
---

<iframe src="http://stl.brentyi.com/viewer/1483428675847" scrolling="no"></iframe>

For our final project in UC Berkeley's *Introduction to Prototyping & Fabrication* course, my partner and I designed, built, and programmed an [RHex](https://en.wikipedia.org/wiki/Rhex)-style hexapedal robot. The design is optimized to cross rough terrain at an extremely low cost (<$70).

---

### Mechanical Design

Mechanical design was done with an emphasis on simplicity: we only needed to fabricate 5 unique parts!

The chassis is constructed out of three pieces of 1/4" plywood, and the motorized leg modules are printed in ABS using a consumer-grade 3D printer.

---

### Electronics

We couldn't find any satisfactory off-the-shelf solutions for handling the electronics portions of our robot, so I ended designing a custom control PCB to meet our needs. Features:
- three TB6612 dual h-bridge driver ICs (for driving 6 individual leg motors)
- an ADXL345 3-axis accelerometer for orientation detection
- an MP1584 5V/3A buck converter (in case I want to add a Raspberry Pi or something in the future)
- an N-fet-based electronic power switch
- three I2C output connectors for our absolute encoders -- these were daisy chained, so we really only needed one
- a filtered battery voltage measurement input

To cut costs and reduce complexity, the board was designed to plug into an ATmega328P-powered Arduino Nano microcontroller.

---

### Firmware

All of the code for our robot was built around the Arduino platform in C++.

It's made of a few main components:
- an open-loop gait controller for generating synchronized leg trajectories in an alternating tripod gait
- six local joint controllers: these are simple PD loops w/ velocity feedforwards
- a BLE interface for sending status information & receiving twist commands
- a set of dynamically configurable settings which can be pushed to & pulled from the EEPROM (this is primarily for control loop tuning on the fly)

Potential features for the future:
- gait optimization based on accelerometer data (already supported by hardware --  for inclines, flip scenarios, etc)
- smarter leg control implementation
- quantitatively calculated leg trajectory parameters (speeds are currently preset)
- ROS support

---

### Links

Videos:
- [Final submission video](https://www.youtube.com/watch?v=aiBIEI0JHwY)
- [Earlier demo video](https://www.youtube.com/watch?v=FYNiEJGiTPM)

Source repositories:
- [Firmware](https://github.com/brentyi/sparky_firmware)
- [Mechanical design](https://github.com/nanditapiyer/sparky_mechanical)
- [Main control PCB design](https://github.com/brentyi/sparky_electronics)
- [Absolute encoder PCB design](https://github.com/brentyi/as5048b_breakout)
