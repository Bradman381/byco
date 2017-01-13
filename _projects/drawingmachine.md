---
title: Drawing Machine
brief: A 2D plotter with a polar coordinate system.
thumbnail: /assets/images/thumbnail_plotter.jpg
year: 2016
order: 99
---

<iframe src="http://stl.brentyi.com/viewer/1484125055069" scrolling="no"></iframe>

For our midterm project in UC Berkeley's *Introduction to Prototyping & Fabrication* course, my partner and I designed, built, and programmed a fully functional 2D plotter with a polar coordinate system.

---

### Mechanical Design

We constructed our plotter out of 1/4" plywood, and used standard NEMA17 steppers are used for both the linear and angular movements. A magnetic solenoid is then used to lift the pen up and down.

---

### Electronics

All of the electronics work was done on perfboard, and included:
- an Arduino Nano microcontroller
- two DRV8825 stepper drivers (one for x, one for theta)
- an IRLB8721 logic-level N-fet for actuating our solenoid
- connectors broken out for external switches & LEDs

---

### Firmware

To run the plotter, we developed a custom [g-code](https://en.wikipedia.org/wiki/G-code) interpreter that accepts standard CNC commands read from either our microcontroller's flash memory or a USB serial connection. The latter allows toolpaths to be easily generated using off-the-shelf CAM applications and sent to the machine via our dashboard application.

All of the firmware was written in C++ using the Arduino platform, and our dashboard application was built as a Google Chrome Packaged App in Javascript.

---

### Links

- [Demo video](https://www.youtube.com/watch?v=BZjUXDSYovs)
- [Firmware repository](https://github.com/brentyi/drawing_machine_firmware)
- [Dashboard application repository](https://github.com/brentyi/drawing_machine_dashboard)
- [Mechanical design repository](https://github.com/nanditapiyer/drawing_machine_hardware)
