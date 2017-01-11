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

Our plotter is primarily constructed out of 1/4" plywood.

Standard NEMA17 steppers are used for both the linear and angular movements, and a magnetic solenoid is used to lift the pen up and down.

---

### Electronics

All of the electronics work was done on a piece of perfboard, which included:
- an Arduino Nano microcontroller
- two DRV8825 stepper drivers
- an IRLB8721 logic-level N-fet for actuating our solenoid
- connectors broken out for external switches & LEDs

---

### Firmware

To run our plotter, we developed a custom [g-code](https://en.wikipedia.org/wiki/G-code) interpreter to accept standard CNC commands over a serial connection made to our dashboard application. 

---

### Links

- [Demo video](https://www.youtube.com/watch?v=BZjUXDSYovs)
- [Firmware repository](https://github.com/brentyi/drawing_machine_firmware)
- [Dashboard application repository](https://github.com/brentyi/drawing_machine_dashboard)
- [Mechanical design repository](https://github.com/nanditapiyer/drawing_machine_hardware)
