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

## Download ROS from dockerhub:
Website: https://hub.docker.com/_/ros

![image](https://user-images.githubusercontent.com/43855029/123154694-37d51a00-d435-11eb-833f-d13f4abae7f2.png)
Let's download noetic and kinetic ROS version:

Request for a compute node with tesla v100 gpu and pull the docker images
```bash
$ singularity pull docker://osrf/ros:noetic-desktop-full
$ singularity pull docker://osrf/ros:kinetic-desktop-full
```
