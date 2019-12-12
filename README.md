 
Simon Says - Master's Final Project
==============================

- [Introduction](#introduction)
- [Four ROS Packages](#four-ros-packages)
  * [1. Speech Commands Classification](#1-speech-commands-classification)
  * [2. Object Detection](#2-object-detection)
  * [3. Plane Detection](#3-plane-detection)
  * [4. Turtlebot Control](#4-turtlebot-control)
- [Other Packages](#other-packages)
- [Acknowledgement](#acknowledgement)



# Introduction
**Background:** This is the final project for my Master's degree of Robotics in Northwestern University.
**Date**: 2019/12/15.

**Abstract:** The project name is called `Simon Says`: After I say a number, the Turtlebot Robot detects this number on the whiteboard in front of it, and then moves there and  crashes into the number. 

**Demo**:
![](doc/project_demo.gif)

In 2019/06, I took the above demo video. The project's repo is [here](https://github.com/felixchenfy/Command_Robot_to_Move). However, the code is in a mess and is hardware dependent, which I do not recommend reading. 

In 2019/10~2019/12, I divided this big project into 4 separate ROS packages and refactored the code. Each package uses ROS topics/services as interface, and is self-contained. See below. (But I haven't combined them to create another video demo.)

# Four ROS Packages

## 1. Speech Commands Classification
    
**Method:** MFCCs features + LSTM.

**Abstract:** (1) Press key to record audio; (2) Speak a word to microphone; (3) Finally, see the classification result on GUI and ROS topic.

**Repo:** https://github.com/felixchenfy/ros_speech_commands_classification

## 2. Object Detection

**Method:** Data augmentation + YOLOv3.

**Abstract:** Run 3 scripts to (1) Synthesize images (by putting few template images onto backgrounds), (2) Train YOLOv3, and (3) Detect objects for: one image, images, video, webcam, or ROS topic.

**Repo:**  https://github.com/felixchenfy/ros_yolo_as_template_matching

## 3. Plane Detection

**Method:** Depth Image + RANSAC
    
**Abstract:** A python node to detect planes from depth image by using RANSAC algorithm.

**Repo:**  https://github.com/felixchenfy/ros_detect_planes_from_depth_img

## 4. Turtlebot Control

**Method:** "Move to Pose" algorithm

**Abstract:** ROS services for controlling Turtlebot3 to target pose.

**Repo:**  https://github.com/felixchenfy/ros_turtlebot_control

# Other Packages

I have developed several other small packages that might be helpful when dealing with **image** data:
* [ros_images_publisher](https://github.com/felixchenfy/ros_images_publisher): A python script to publish color or depth images from a folder to ROS topic.
* [ros_pub_and_sub_rgbd_and_cloud](https://github.com/felixchenfy/ros_pub_and_sub_rgbd_and_cloud): Python nodes to publish/subscribe RGB-D images and their point clouds (or any of them) to/from ROS topics.
* [ros_record_rgbd_images](https://github.com/felixchenfy/ros_record_rgbd_images): Press key to record color/depth images from ROS topics or Realsense.
* [record_images_from_usbcam](https://github.com/felixchenfy/record_images_from_usbcam): Run one script and press 's'/'d' to save your laptop's camera images to disk.
* [open3d_ros_pointcloud_conversion](https://github.com/felixchenfy/open3d_ros_pointcloud_conversion) 2 Python API functions for point cloud conversion between Open3D and ROS.

# Acknowledgement

The idea of this `Simon Says` project was proposed by Prof. Ying Wu. Many thanks to Prof. Wu for providing me the chance of joining his lab, working on this interesting project, and sharing papers in the group meeting. 

Also, I'd like to express great thanks to Matthew, who is the Vice Director of MS Robotics program, for the guidance and help to my project through out the whole program.