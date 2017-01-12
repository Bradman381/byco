---
title: VR Telepresence Robot
brief: A Google Cardboard-controlled telepresence robot built at HackIllinois.
thumbnail: /assets/images/thumbnail_telepresence.jpg
year: 2016
order: 86
---

At HackIllinois 2016, my team built a telepresence robot that allowed a user remotely explore an environemnt via a Google Cardboard VR headset.

---

### Overview

Our robot featured a drivetrain with a camera mounted on top of an onboard 3-DOF gimbal, which allowed us to sync the robot's camera orientation with our user's actual head movements, as it streamed camera images back for display.

We leveraged [ROS](http://wiki.ros.org/) for handling communication between the different pieces of code running on the Beaglebone Black that powered our robot, and used a web socket (via [roslibjs](https://github.com/RobotWebTools/roslibjs)) to communicate between our phone application and Linux processor.

I worked on software for the project and built the phone application and image+sensor data streaming setup, while making significant contributions to the lower-level code that ran on our embedded Beaglebone processor.

---

### Issues

To circumvent issues with gimbal lock, we used quaternions to represent all of our orientation information.

Because we relied heavily on gyroscope data for orientation information, our robot was also initially extremely susceptible to drift. To resolve this, we inserted a simple complementary filter into our software stack. This effectively combines information from low-pass filtered accelerometer readings (to eliminate noise) and high-pass filtered gyroscope readings (to eliminate drift), and left us with really clean orientation data.

---

### Links
[All of the code can be found in our Github organization!](https://github.com/natural-telepresence)
