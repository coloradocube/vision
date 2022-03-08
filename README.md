# CubeSat Vision

Computer vision for CubeSat operations based on the Xilinx Kria K26.

## Original submission

The [original submission](https://www.hackster.io/contests/xilinxadaptivecomputing2021/hardware_applications/14401) proposed a multi-camera vision system for a CubeSat to support the following functions:
* situational awareness
* celestial navigation
* attitude determination & control
* autonomous inspection
* _swarm operations_
* _comms bandwidth reduction_

## Project experiments

The projects have to be feasible on the ground or in the air up to 50 m per FCC regulations:
1. Indoors, on static surface, identify faces with 1 camera. This is the Smart Camera demo app. 
2. Indoors, on static surface, identify faces and alert for proximity with 1 camera and LIDAR. Overlay LIDAR on video. Sensor fusion in software. _How to do in hardware?_ 
3. Dynamically reprogram to do (1) or (2).
4. Do (1) and (2) simultaneously.
5. Indoors, on rotating platform, stitch a 360 degree view with 1 camera. Stabilize to the orientation of choice with software on client. Need WiFi to see it. _What WiFi module will work?_
6. Indoors, on rotating platform, stitch a 360 degree view with 1 camera. Stabilize to the orientation of choice with software on Kria. Need WiFi to see it. 
7. Indoors, on rotating platform, segment objects and alert for proximity with 1 camera and LIDAR. Sensor fusion in software. Need WiFi to see the segmentation. 
8. Dynamically reprogram to do (6) or (7).
9. Do (6) and (7) simultaneously.
10. 
