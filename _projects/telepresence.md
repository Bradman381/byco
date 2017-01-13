---
title: VR Telepresence Robot
brief: A Google Cardboard-controlled telepresence robot built at HackIllinois.
thumbnail: /assets/images/thumbnail_telepresence.jpg
year: 2016
order: 86
---

![telepresence robot](/assets/images/telepresence.png)

At HackIllinois 2016, my team built a telepresence robot that allowed a user remotely explore an environemnt via a Google Cardboard VR headset.

---

### Overview

Our robot featured a drivetrain with a camera mounted on top of an onboard 3-DOF gimbal, which allowed us to sync the robot's camera orientation with our user's actual head movements, as it streamed camera images back to the user's VR headset for display.

We leveraged [ROS](http://wiki.ros.org/) for handling communication between the different pieces of code running on the Beaglebone Black that powered our robot, and used a web socket (via [roslibjs](https://github.com/RobotWebTools/roslibjs)) to communicate between our phone application and Linux processor.

As a contributor to the software-side of our project, I built the phone application and image+sensor data streaming setup, while making significant additions to the lower-level code that ran on our embedded Beaglebone processor.

---

### Issues

To circumvent problems with gimbal lock, we used quaternion representations for all of our orientations.

With our initial naive phone orientation estimation, we were extremely susceptible to the effects of gyro drift. To resolve this, we inserted a simple complementary filter into our software stack. This effectively combined information from high-pass filtered gyroscope readings (to eliminate drift) and low-pass filtered accelerometer readings (to eliminate noise), and left us with really clean orientation data.

---

### Links
[All of the code can be found in our Github organization!](https://github.com/natural-telepresence)
