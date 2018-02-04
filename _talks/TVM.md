---
title: "Teleoperating Baxter Robot's Arms Using Motion Capture"
collection: talks
type: "Course Project"
permalink: /talks/2013-03-01-tutorial-1
venue: "CIBR Lab - Worcester Polytechnic Institute"
date: 2017-08-30
location: "Worcester MA, USA"
---

[More information here](http://exampleurl.com)

Introduction
======
The main aim of the project was to develop interoperability modules that is capable of mapping human motion isomorphically to Baxter Robot's arms. We had the Baxter Robot platform with a mobile base, and the Vicon Motion Capture System for human motion data acquisition.


Obtaining Joint Angles
======
Data was obtained using the Vicon motion capture system, and was transmitted and received over a local network using the vicon bridge ROS package. 

The joint angles of the human subject were determined using generalised inverse kinematic models of the Human Arm. The data was noisy and thus was low-pass filtered using a digital FIR filter, at a frequency of about 10Hz. The reasoning behind this was based on the assumption that no human joint-angle could oscillate at frequencies higher than 10Hz.

The Isomorphic Map
======
Also, due to the difference in configuration of Baxter's Arms, the joint angles inputs to Baxter's Arms had to be mapped to Baxter's Joint Space so that the mapping was visually-intelligible to the human subject.

An early result can show how difficult and agonising the control process was for the human subject and all related subjects interacting with the robot (Sincerest apologies for the video orientation):
[Video demo of early mapping](https://photos.app.goo.gl/PGO7z9vR89gf8a9d2)

The final mapping, developed by a teammate, was a lot more intelligible and isomorphic to human motion, as can be see [here](https://www.youtube.com/watch?v=Fy6iVArQv2A&feature=youtu.be).
