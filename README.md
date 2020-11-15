### Video demos

<p align='left'>
    <img src="./gifs/day2night.gif" alt="drawing" width="400"/>
    <img src="./gifs/panorama.gif" alt="drawing" width="400"/>
</p>

<p align='left'>
    <img src="./gifs/kidnap.gif" alt="drawing" width="400"/>
    <img src="./gifs/lastmile.gif" alt="drawing" width="400"/>
</p>

<p align='left'>
    <img src="./gifs/field1.gif" alt="drawing" width="400"/>
    <img src="./gifs/field2.gif" alt="drawing" width="400"/>
</p>

### YouTuBe

[Day-to-Night](https://youtu.be/4oTsYiRGueI)         
[LastmileDelivery](https://youtu.be/aFI46kuOIZY)
[FieldTest](https://youtu.be/mqoAdgJs6QY)         
[DenseVegatation](https://youtu.be/dV1twE4ZAPA)

### A Brief Description
- **cameleon_teleop**: joystick control.
- **jaguar4x4_driver**: drrobot jaguar 4x4 robot driver. 
- **stroll_bearnav**: V-T&R, visual teach and repeat.
- **zed-ros-wrapper**: ZED stereo camera ros wrapper.


### Prerequsites

- Setup the system, network and instll ZED SDK following this doc: https://docs.google.com/document/d/1bVcLDn5SaNdEJfhhgs9zo8NH3Q-CBlKi2X29lBY4dmA/edit?usp=sharing

### Environment

- Ubuntu 16.04 + ROS kinetic

### Install jaguar_nav

1. Create a catkin workspace:
   ```
   $ mkdir ~/jaguar_ws/
   $ git clone git clone git@github.com:kevinlisun/jaguar_nav.git src
   $ cd ~/jajuar_ws/src
   ```
  
2. Pull the repositories:
   ```
   $ wstool update
   $ cd ..
   $ rosdep install --from-paths src --ignore-src -r -y
   ```
3. Compile:
   ```
   $ catkin_make -DCMAKE_BUILD_TYPE=Release
   ```
4. Add ROS workspace to the environment.

   Add `source ~/jaguar_ws/devel/setup.bash` to ~/.bashrc

### Joystick Control

1. Launch the robot (drivers and camera).
   ```
   $ roslaunch jaguar4x4_2014 robot.launch
   ```
2. Launch the joystick control.
  ```
  $ roslaunch cameleon_teleop cameleon_teleop.launch
  ```
Now you should be able to drive the robot using the joystick (you will need to hold the LB button).

### Teach (Mapping)

1. Launch the stroll-nav core and GUI.
   ```
   $ roslaunch stroll_bearnav stroll-core.launch
   $ roslaunch stroll_bearnav stroll-gui.launch
   ```

2. Input the file name in the "Mapper" window and click "SEND GOAL".
   Now you should be able to controll the robot using "up down left right", and the robot will move with a constant and for continouly maneuver, you should press the button multiple times rather than hold it (you should NOT hold the LB button otherwise will switch to joystick control).

3. Press the LB button to pause or intervene. Press button "A" on joystick to complete the mapping session and save the map.

### Repeat (Autonomous Navigation)

1. Load the "map" using the "loadMap" GUI. This may takes a while.
2. Set the traversals: 1 and click "SEND GOAL". 

You probably will need to give the robot an initial speed by pressing "up" button several times, then the robot should be able to navigate autonomously.
