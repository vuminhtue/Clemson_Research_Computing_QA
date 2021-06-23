---
title: "Use of ROS container"
teaching: 5 min
exercises: 0
questions: "How to run ROS container in Palmetto HPC"
objectives:
- "Download ros docker file"
- "Open Rviz and Gazebo GUI in container"
keypoints:
- "ROS, container"
---
## What is ROS?
The Robot Operating System (ROS) is a set of software libraries and tools that help you build robot applications. From drivers to state-of-the-art algorithms, and with powerful developer tools, ROS has what you need for your next robotics project. And it's all open source.

## What is rviz?
rviz (short for “ROS visualization”) is a 3D visualization software tool for robots, sensors, and algorithms. It enables you to see the robot’s perception of its world (real or simulated).

## What is Gazebo?
Gazebo is a 3D robot simulator. Its objective is to simulate a robot, giving you a close substitute to how your robot would behave in a real-world physical environment. It can compute the impact of forces (such as gravity).

## Download ROS from dockerhub:
Website: https://hub.docker.com/_/ros

![image](https://user-images.githubusercontent.com/43855029/123154694-37d51a00-d435-11eb-833f-d13f4abae7f2.png)
Let's download noetic and kinetic ROS version:

Request for a compute node with a gpu and pull the docker images
```bash
$ singularity pull docker://osrf/ros:noetic-desktop-full
$ singularity pull docker://osrf/ros:kinetic-desktop-full
```

2 sif files are created in the same directory:

![image](https://user-images.githubusercontent.com/43855029/123155205-d2cdf400-d435-11eb-94d7-7ab6cc5c879b.png)

## Start the roscore in current terminal using either noetic or kinetic model


```bash
singularity exec -p ros_noetic-desktop-full.sif bash -c 'source /opt/ros/noetic/setup.bash; roscore'
singularity exec -p ros_kinetic-desktop-full.sif bash -c 'source /opt/ros/kinetic/setup.bash; roscore'
```

Here is the sample from using noetic version:

![image](https://user-images.githubusercontent.com/43855029/123155481-29d3c900-d436-11eb-9df9-b2c59eca7f51.png)


## Open new terminal, go to login node and ssh -X to current compute node with graphical display, go to  the singularity image location

Run any of these command for rviz/gazebo: for either noetic or kinetic model with NVIDIA support (using --nv)

```bash
singularity exec --nv -p ros_noetic-desktop-full.sif bash -c 'source /opt/ros/noetic/setup.bash; rviz'
singularity exec --nv -p ros_noetic-desktop-full.sif bash -c 'source /opt/ros/noetic/setup.bash; gazebo'
singularity exec --nv -p ros_kinetic-desktop-full.sif bash -c 'source /opt/ros/kinetic/setup.bash; rviz'
singularity exec --nv -p ros_kinetic-desktop-full.sif bash -c 'source /opt/ros/kinetic/setup.bash; gazebo'
```
Note: The **-p** is to make sure all child processes in the container are terminated when the container terminates.

![image](https://user-images.githubusercontent.com/43855029/123155946-b54d5a00-d436-11eb-8354-041e83699f71.png)


The corresponding RVIZ window appears:
![image](https://user-images.githubusercontent.com/43855029/123156005-c72efd00-d436-11eb-9c93-3fd0f454e3f4.png)

Or Gazebo:

![image](https://user-images.githubusercontent.com/43855029/123156157-f80f3200-d436-11eb-902c-f4fabe6ed096.png)

Similarly, you can use it without NVIDIA support:

```bash
singularity exec -p ros_noetic-desktop-full.sif bash -c 'source /opt/ros/noetic/setup.bash; rviz'
singularity exec -p ros_noetic-desktop-full.sif bash -c 'source /opt/ros/noetic/setup.bash; gazebo'
singularity exec -p ros_kinetic-desktop-full.sif bash -c 'source /opt/ros/kinetic/setup.bash; rviz'
singularity exec -p ros_kinetic-desktop-full.sif bash -c 'source /opt/ros/kinetic/setup.bash; gazebo'
```


