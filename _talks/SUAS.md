---
title: "Student Unmanned Air Systems Competition"
collection: talks
type: "Competition"
permalink: /talks/SUAS
venue: "Webster Field"
date: 2015-06-15
location: "St Inigoes MD, USA"
---

Participated in the 14th Annual Student Unmanned Aerial Systems(UAS) Competition at Webster Field, St Inigoes, Maryland, USA from June 15 to 18, 2016. Placed 5th Overall.

Team website: http://www.edhitha-uas.com/

Early Stages
=====
My initial task in the team was to develop image processing programs that had to detect and extract targets of interest from aerial images. The aerial images were captured by an onboard Nikon DSLR camera that was remotely operated using an Odroid C1 and the gphoto2 bash terminal tool.

Some examples of the images obtained in-flight are:

<img src='/images/No Target.JPG'>
The above image is a typical image obtained, one with no targets in it.

<img src='/images/Target.JPG'>
The above image is a classic example of the type of images one would recive from the UAS at the competition , one with a non-target that can easily be detected as a target. The real target that is to be filtered out of this image is the Blue semi-circle in the top-right of the image, with a Pink 'I' on it.

And the result one would obtain upon running the program I co-developed on the image aove would be:
<img src='/images/1-8.PNG'>

Due to the small size of data available, I used heuristics such as Area of detected targets, setting dimensional constraints on the length and breadth, and checking if the centroid lied within the target's space.

Autonomous Detection, Localisation, Classification (ADLC) Task
=====

To process images as they came, we used the **inotify** library for registering to events upon receiving new images. This reduced the overhead on the Ground Control Station (GCS), which ran the image-processing program.

As per the competition requirements, we were also rewuired to estimate the geeographical position, for which I used the **GeographicLib** library, and geographical heading of the target detected from the image data and also to identify the visual characteristics, such as the colours present on, and shape of the target. The alphabet on the target was also to be determined.

The alphabet and shape were seperated using K-means clustering. I used the **Intel TBB library** to accelerate the K-means clustering process.

After seperating the alphabet and shape, we had to identify the shape and alphabet. I used **Tesseract OCR** in 2015 for recognising alphabets, which did not meet expectations but had to be used to time constraints and limited resources. A fellow teammate used Hu Moments to clssify the extracted shapes.

Finally, all the information was encapsulated into text files named the same as the images.

Sense, Detect, and Avoid (SDA) Task
=====

The efforts put into this task led to the first academic accomplishment of my career. I designed and implemented a novel algorithm for motion planning of the UAS, that was capable of generating paths that avoided static obstacles. The algorithm was [implemented]() in C++ for speed.

The algorithm makes use of the Particle Swarm Optimisation Metaheuristic, which simulates the behaviour of bird flocks and animal swarms to optimise problems. The algorithm I proposed models the path-planning problem as an optimisation problem, one where the objective is to minimise the distance to the target and to minimise travelling near obstacles, for which I used potential fields.

The following are screenshots from the Ground Control Station software, Mission Planner.
<img src='/images/justfly1.png'>
This images shows the trajectory taken by the aircraft which clearly avoids the circular obstacles that are in purple.

<img src='/images/sda.png'>
This image shows the generated waypoints that clearly avoid the obstacles shown.

All the planning was done in the cartesian space, and so the GPS coordinates were converted into the local euclidean space using the **GeographicLib** library.

Our team ended up placing fifth overall in 2015, and ever since, my passion for autonomous vehicular robotics has not faded.
