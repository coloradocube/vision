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

The projects have to be feasible on the ground or in the air up to 50 m per FCC regulations.

### 1. Indoors

#### 1.1. Kit carrier

1. On static surface, identify faces with 1 camera. This is the Smart Camera demo app. _How is the overlay accomplished?_
2. On static surface, identify faces and alert for proximity with 1 camera and LIDAR. Overlay LIDAR on video. Sensor fusion in software. _How to do in hardware?_ 
3. Dynamically reprogram to do (1) or (2).
4. Do (1) and (2) simultaneously.
5. On rotating platform, stitch a 360 degree view with 1 camera. Stabilize to the orientation of choice with software on client. Need WiFi to see it. _What WiFi module will work?_
6. On rotating platform, stitch a 360 degree view with 1 camera. Stabilize to the orientation of choice with software on Kria. Need WiFi to see it. 
7. On rotating platform, segment objects and alert for proximity with 1 camera and LIDAR. Sensor fusion in software. Need WiFi to see the segmentation. 
8. Dynamically reprogram to do (6) or (7).
9. Do (6) and (7) simultaneously.
10. In addition to (9), mount and connect a digital compass (e.g. [this](https://www.amazon.com/Digital-Compass-Magnetometer-Electronic-Magnetic/dp/B07PP67N9Q) connects over I2C). Stabilize to the orientation of choice with software on Kria, including compass directions and degrees. Overlay the 3D directions over the image like a virtual nautical compass. Need WiFi to see it. Sensor fusion in software.

#### 1.2. Custom carrier

11. Perform (1) with multiple cameras.
12. Perform (2) with multiple cameras.
13. Perform (3) with multiple cameras.
14. Perform (4) with multiple cameras.
15. Perform (6) with multiple cameras. Compare to single-camera by dynamically reprogramming.
16. Perform (10) with multiple cameras.

### 2. Outdoors

#### 2.1. Kit carrier

#### 2.2. Custom carrier


### Custom carrier requirements

1. Battery power.
2. 
