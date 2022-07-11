# Design-and-Implementation-of-a-computational-motion-planning-algorithm-based-on-navier-stokes-equations
This repositoery is based on the graduation project for Bachelor Degree in Mechatronics Engineering at Tishreen University, Syria - Summer 2021

## Abstract
Formation of non-holonomic swarm robots has received a lot of considerations in both academia and
industry over last two decades. Many path planning methods produce collision-free paths for a group of
multiple robots, but many of them are computationally expensive and complex to implement and develop.
In addition, these methods do not find a solution in all environments, or they find a solution that is not
optimal. In this project, we present a computational motion planning algorithm based on fluid dynamics
PDE for Robotic Swarms. This proposed method features a computationally cheap algorithm, and it is
easy to develop using updated tools and hardware. But, most importantly, it always ensures finding a
path, because partial differential equations of fluid dynamics always finds a solution that describes the
movement of the fluid’s particles towards a goal. The aforementioned feature gives this algorithm a clear
advantage because it is reliable, and it produces a smooth path. The validity of this algorithm will be
tested on a robotic swarm platform that we designed and implemented to ensure high quality and ease of
use. The control of the swarm is preformed centrally, and a visual feedback is provided continually to the
central computer from a camera that is fixed above the robots.

## Hardware description
In the end we will have a square platform (**4.2×4.2 [m²]**) with high walls and different types of obstacles. Above the platform there is a fixed **stereo camera**, and inside the platform there will be a **15 mobile robots**. We will design everything from scratch then we will test our proposed path planning algorithm on our designed platform. And this is a 3D design for the platform:

![platform](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/blob/main/Images/Platform_3D%20design.png)


## Project overview

### Designing Stage:

After many designs, we ended up with the octagon-shaped robot with two circuits (each one of them has two layers). We chose this design; because it was the most compact one. We used **SolidWorks** for designing the body while we used **Altium** for the circuits. 

- We can see below the body CAD design with the wheels in which we chose them like this to make our own encoder and it is important to mention that we chose the optimum number of the holes (33 holes):

![CAD](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/blob/main/Images/CAD%20design.png)

- circuits PCB design (the left circuit is the top one while the right circuit is the bottom one):

![PCB](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/blob/main/Images/circuits_PCB%20design.PNG)

### Manufacturing stage:
After the designing stage, we started printing the bodies and the wheels by using a 3D printer (we used Acid Polylactic with PLA as a material). And we were printing the circuits in parallel.

- circuits after manufacturing:

![circuits_2](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/blob/main/Images/circuits_real%20life.png)

- we can see below one robot after manufacturing and assembling, and for more images about manufacturing stage you can check the [Images Folder](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/tree/main/Images).

![robot](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/blob/main/Images/one%20robot_after%20assembling.png)

### Implementation
- We started in simulation; we implemented the PDE algorithm for one robot and tested it on different maps by using **MATLAB**. And as we can see below the PDE algorithm managed to find a path from the start point to the goal in each map:

![different_maps](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/blob/main/Images/PDE%20results%20for%20different%20maps.png)

As it is clear from the previous image; the PDE managed to find the path for any given map which gives it advantages over the most popular path planning algorithms (A*, Dijkestra and potential field) in terms of finding the path and time consumption.

- Then we started the impelmentaion in real life:
1. We calibrated the camera depeding on the pinhole camera model and we found the Intrinsic and Extrinsic parameters.
2. We used Aruco markers in order to identify each robot, and each robot has its own ID through the whole project; in which it will help us later in sending a specific message for each robot.
3. After working onthe feedback system, we started working on ROS on the central computer. We created three nodes each one has it is clear task -as it is clear below- then we connected the central computer with each robot wirelessly by using esp8266 chip.

 ![here the project scheme:](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/blob/main/Images/Algoritm%20Scheme.png)
## Project output
1. Platform (**4.2×4.2 [m²]**) with high walls and different types of obstacles.
2. **15 octagon-shaped mobile robots**  designed from scratch with dimensions (**6×7×6 [m³]**).
3. Implementing a computational motion planning algorithm on a single robot, then developing it and expanding it for the swarm of robots.
4. Comparing between our suggested algorithm and the famous algorithms in the literature (A*, Dijkstra, Potential Field) 
5. Extracting results that confirm the validity of the proposed algorithm and its superiority over conventional and non-traditional algorithms in terms of path-finding inevitability and other factors. You can check the following [video](https://www.dropbox.com/s/yim75ajkh6q3i72/video.mp4?dl=00).

## Files
- [Body Design Folder:](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/tree/main/Body%20Design)
includes **SolidWorks** files.
- [Circuits PCB Design Folder:](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/tree/main/Circuits%20PCB%20Design)
includes the **PCB** files for both top and bottom circuits, and it is important to metion that we used **Altium** software for designing the circuits.
- [Swarm Robot Firmware Folder:](https://github.com/SibaIssa/Design-and-Implementation-of-a-computational-motion-planning-algorithm/tree/main/Swarm%20Robot%20Firmware) includes **.cpp** files in which contain the code that we put it on the microcontroller on each robot, and we used **AVR** software for programming.

## Credits
I worked on this project with two of my colleagues:
- [Adnan Saood](https://github.com/adnan-saood)
- [Nada Salman](https://www.linkedin.com/in/nada-s-salman/)
