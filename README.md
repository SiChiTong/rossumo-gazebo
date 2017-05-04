# ROS Sumo Gazebo
This is a gazebo simulation of the Parrot Jumping Sumo. It also includes ROS wrapper (from https://github.com/arnaud-ramey/rossumo ) for Ardrone SDK 3 modified to behave like the Gazebo Sumo. With both of these you can bothsimulate a Jumping Sumo Drone and run a real Sumo Drone through ROS. You can do things like record movements on the real Sumo drone with ROSBAG and play them in the simultion which is what was done in the video. The ultimate purpose of creating the simulation is to use reinforcement learning to teach a sumo to do tasks like climb stairs in Gazebo and then apply what was learnt to a real jumping sumo such as climbing stairs.

The following video shows is an example of a movements of a real Sumo recorded with ROSBAG on the left and the movements being played to the simulation in Gazebo. The layout of the real room and the Gazebo room is the same:

[![Youtube sumo](http://forthtemple.com/sumo/youtube500.jpg)](https://www.youtube.com/watch?v=5opPQ47Y-WE) 


# Installation Gazebo Only
Install ROS (eg http://wiki.ros.org/indigo/Installation/Ubuntu if from ubuntu)

If you just want run the model under gazebo then under your catkin_src directory:
```
cd ~/catkin_ws/src
git clone https://github.com/forthtemple/rossumo-gazebo.git
cd ~/catkin_ws
catkin_make --only-pkg-with-deps rossumo_gazebo
catkin_make --only-pkg-with-deps rossumo_description
```

# Run with Gazebo Only
In one terminal run:
```
roslaunch rossumo_gazebo rossumo_world.launch
```
In another terminal run:
```
rosrun rossumo teleop_twist_keyboard.py
```
and press the keys to move the sumo.

# Installation rossumo
To install the ROS wrapper for Ardrone SDK 3 follow instructions for install rossumo under 'rossumo' directory including building the ardrone SDK. It is a copy of https://github.com/arnaud-ramey/rossumo but has been modified to behave like the Gazebo sumo.

To record a real sumo
``` 
rosbag record rossumo1/cmd_vel /rossumo1/high_jump
```
To play it to your Gazebo sumo:
```
rosbag play 2017-05-04-13-28-38.bag /rossumo1/cmd_vel:=/cmd_vel /rossumo1/high_jump:=/high_jump
```








