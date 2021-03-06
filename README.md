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
7. LIDAR (UART). _Consider fusion in software vs hardware._
8. WiFi.
9. Antenna on carrier.
10. CAN integration into CubeSat bus.
11. Full localization (e.g. u-blox), if not integrated with GPS.
12. Full comms (incl. cellular), if not integrated with WiFi.

#### 2. Space version

13. Space-grade, rad-hard components.
14. Memory scrubber.
15. Space comms.
16. ROS & robotics SLAM.

### Notes

* optical rate gyro
* camera configuration can be 1 high-quality (hyperspectral) looking forward (for autonomous inspection) and 3 small ones on the sides (for 360?? obstacle avoidance)
* low-battery identification and soft shutdown

### Procurement

1. Cameras.
   1. Hyperspectral camera module (like [OV4682](https://www.e-consystems.com/blog/camera/camera-board/ov4682-multispectral-camera-module-launched/) which doesn't look to be available).
   2. The [NavQ]()https://nxp.gitbook.io/8mmnavq/'s camera is a [Google Coral Model CA1](https://coral.ai/products/camera/), and is [MIPI-CSI](https://resources.mipi.org/blog/a-look-under-the-hood-at-mipi-csi-2-and-mipi-dsi-2-in-automotive) connectable.
2. Absolute orientation module.
3. Fanless heatsink for Kria.
4. Sky atlas.

### 3D printing

1. Rotating platform mount for Kria original carrier, battery power, and camera(s). _Denver library [idealab](https://www.denverlibrary.org/idealab3D)!_
2. Add space for LIDAR to (1).
3. Drone mount for Kria original carrier, battery power, and 4 cameras.
5. (TBD) Drone mount for LIDAR. _No power solution yet. Best to investigate connecting Kria and LIDAR to drone batteries, either separate battery or from a doubled-up batteries, but this is well outside the lift capacity in the current configuration._

### Power

1. Kria K26 requires 5v.
2. RPLIDAR 3 requires 5v.
3. RDDRONE-FMUK66 requires 3.3v. The power module drawing from the battery-to-PDB connector looks custom. It's based on the [Monolythic Power MP1584EN step-down converter](https://www.monolithicpower.com/en/documentview/productdocument/index/version/2/document_type/Datasheet/lang/en/sku/MP1584EN-LF-Z/document_id/204). ([MP2338](https://www.monolithicpower.com/en/mp2338.html) is recommended for new designs.) There are similar products available (e.g. this [adjustable DC-DC buck converter module](https://www.amazon.com/MP1584EN-DC-DC-Converter-Adjustable-Module/dp/B01MQGMOKI?th=1)). The prominent 4R7 is a power inductor. _Note: The drone's power converter is a "pass-through" with 6 lines coming out to the FMUK66 (1 red and 5 black) while the main battery-to-PDB continues on both ends._
