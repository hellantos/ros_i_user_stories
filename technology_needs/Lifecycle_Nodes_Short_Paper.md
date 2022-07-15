# ROS-Industrial Lifecycle Management Challenge Description

**Objective**:  
This document shall capture the challenges and issues that arise when developing ROS nodes and specifically drivers using the lifecycle mechanism.

**Target Audience**
ROS2 developers


## Problematic Use Cases

**Debugging Lifecycle Nodes:**  
When developing lifecycle nodes it is important to debug and test the different states of the lifecycle. Therefore, it would be useful to have a simple way of launching a lifecycle node in a specific state. Currently, launch_ros does not allow this. In order to bring a node to a specific state, a rather lengthy script is necessary and it is potentially faster to write a bash script using the ros2 lifecycle tool. Therefore, it would be interesting to add a feature to launch_ros that enables specifying the necessary transitions.

This has been addressed by:  
PR: https://github.com/ros2/launch_ros/pull/317


**Composition with Lifecycles:**  
In many cases, it would be interesting to use lifecycle nodes in combination with composition. One important example could be drivers for device/field busses such as CANopen or Ethercat, where this would enable adding one node per device on the bus.
While the combination of lifecycle nodes and composition is theoretically possible, it is not supported by launch_ros. In launch_ros nodes that are part of a composed container are not handled as real nodes and it is not possible to apply lifecycle functionalities.

This has been addressed by:   
Issue: https://github.com/ros2/launch_ros/issues/41  
Prototype: https://github.com/ipa-cmh/launch_ros_experimental

