---
title: "Autonomous RC Car"
collection: talks
type: "Volunteer Project"
permalink: /talks/Autonomous RC Car
venue: "Worcester Polytechnic Institute"
date: 2017-12-07
location: "Worcester MA, USA"
---

[Repository](https://github.com/MapleNSteel/Autonomous-RC-Car)

Project on making a Traxxas Rally 4-wheel drive RC car autonomous. 

Preliminary Steps
======

The vehicle was presented to me with a Autopilot implemented on a Teensy Arduino 3.2 microcontroller, a Jetson TX2 for high-level tasks such as computer vision, SLAM, and issuing controls to the autopilot.

The system had a brushless unsensored motor and Electronic Speed Control (ESC) combo which is non-ideal as it is incapable of smooth movement at low speeds. The first task was to replace the ESC and motor with a sensored combination which solves the issue of "cogging" at low speeds.

<img src='/images/ReplacingMotor.jpg'>
I chose to go with the Tekin Redline Gen3 17.5 Turn Sensored Motor, and the Hobbywing Xerun XR10 Pro 80A ESC.

With the new motor and ESC installed I was able to achieve speeds as low as 3 cm/s and speeds as high as 20 m/s.

Completed: 15th January 2018

Autopilot
======

For the autopilot, given the computational-constraints on the microcontroller, I may consider running State-Estimation Modules on board the Jetson TX2, based on how well the Teensy 3.2 can deal with the task. Currently working with a team of three to decide on the right approach to achieve proper state-estimation. For now, the Dubin's Car model seems to be enough.

Serial communication modules also have to be designed to send commands to the controller and to receive odometry data from the microcontroller.

ETA: 9th February 2018

State Estimation, and SLAM
======

For estimating the position of the vehicle, we intend on using SLAM and an IMU, if necessary for state estimation.

ETA: To be decided.
