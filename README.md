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
10. **In addition to (9), mount and connect a digital compass (e.g. [this](https://www.amazon.com/Digital-Compass-Magnetometer-Electronic-Magnetic/dp/B07PP67N9Q) connects over I2C). Stabilize to the orientation of choice with software on Kria, including compass directions and degrees. Overlay the 3D directions over the image like a virtual nautical compass. Need WiFi to see it. Sensor fusion in software.**
11. **In a planetarium, on rotating platform, without LIDAR or compass (may use as training signal), stabilize to the orientation of choice. Overlay celestial object names and constellations on view.** _Does the [Denver Planetarium](https://www.dmns.org/visit/planetarium/) actually have a [dome star projector](https://www.zeiss.com/planetariums/us/about-us/image-download/planetarium-projectors.html)?_

#### 1.2. Custom carrier

12. Perform (1) with multiple cameras.
13. Perform (2) with multiple cameras.
14. Perform (3) with multiple cameras.
15. Perform (4) with multiple cameras.
16. Perform (6) with multiple cameras. Compare to single-camera by switching in software or dynamically reprogramming, if necessary. Examine dependence of quality on rotational speed. Total angle covered at every moment and remaining gaps.
17. **Perform (10) with multiple cameras.**
18. **Perform (11) with multiple cameras.**

### 2. Outdoors

#### 2.1. Kit carrier

18. On [Sugarloaf](https://www.summitpost.org/sugarloaf-mountain-boulder-co/445263), perform (11).
19. On drone, with 1 camera, dynamically reprogram among face recognition, follow me, and segmentation. _Note that the drone has an IMU to add to sensor fusion!_
20. On drone, with 1 camera, perform autonomous flight with photogrametry-based stitching of a 3D model of some structure for autonomous inspection.
21. Add defect inspection to (20).
22. **Add 360 degree object avoidance to (21).** _May the [Wings Over the Rockies Museum](https://wingsmuseum.org/museum/) allow me to image one of their airplanes?_

#### 2.2. Custom carrier

23. Perform (22) with multiple cameras.
24. **With multiple cameras, GPS and IMU, demonstrate autonomous waypoint to waypoint flight with automoatic local obstacle avoidance (e.g. crossing Rock Creek through the trees) between waypoints.**

### Custom carrier requirements

#### 1. Ground and air version

1. 95 mm x 95 mm.
2. Battery power.
3. 6+2 camera connectors. _How can the maximum number of cameras be connected electrically?_
4. 9-DOF IMU.
5. Compass (I2C), if not integrated with IMU.
6. GPS (I2C).
7. LIDAR (UART).
8. WiFi.
9. Antenna on carrier.
10. CAN integration into CubeSat bus.
11. Full localization (e.g. u-blox), if not integrated with GPS.
12. Full comms (incl. cellular), if not integrated with WiFi.

#### 2. Space version

13. Space-grade components.
14. Memory scrubber.
15. Space comms.
16. ROS & robotics SLAM.
