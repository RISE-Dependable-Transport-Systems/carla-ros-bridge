# ROS/ROS2 bridge for CARLA simulator

This ROS package is a bridge that enables two-way communication between ROS and CARLA. The information from the CARLA server is translated to ROS topics. In the same way, the messages sent between nodes in ROS get translated to commands to be applied in CARLA.

This version requires CARLA 0.9.15

## Features

- Provide Sensor Data (Lidar, Semantic lidar, Cameras (depth, segmentation, rgb, dvs), GNSS, Radar, IMU)
- Provide Object Data (Transforms (via [tf](http://wiki.ros.org/tf)), Traffic light status, Visualization markers, Collision, Lane invasion)
- Control AD Agents (Steer/Throttle/Brake)
- Control CARLA (Play/pause simulation, Set simulation parameters)

## Getting started and documentation

Installation instructions and further documentation of the ROS bridge and additional packages are found [**here**](https://carla.readthedocs.io/projects/ros-bridge/en/latest/).

## Issues

- Compilation issues with rviz_carla_plugin, carla_ad_demo, pcl_recorder. Skip them during build step:
  ```
  colcon build --symlink-install --packages-skip rviz_carla_plugin carla_ad_demo pcl_recorder
  ```

## Setup

- `rosdep install -i --from-path src --rosdistro humble -r -y`
- `pip install -r src/carla-ros-bridge/requirements.txt`

## Usage

```
ros2 launch carla_ros_bridge carla_ros_bridge.launch.py passive:=True
ros2 launch carla_ros_bridge carla_ros_bridge.launch.py passive:=True log_level:=debug
```
