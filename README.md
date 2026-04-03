# tesollo_dg_3f_gripper
ROS2 package for TESOLLO DG-3F Gripper with MODBUS-RTU

## Installation
```bash
cd <path_to_ws>/src
git clone https://github.com/wei-hsuan-cheng/tesollo_dg_3f_gripper.git
rosdep install --from-path tesollo_dg_3f_gripper --ignore-src -r -y
```

## Build
```bash
cd <path_to_ws>
colcon build --symlink-install --packages-select tesollo_dg_3f_gripper && . install/setup.bash
```

## Execute
```bash
ros2 launch delto_3f_description upload_gripper.launch.py
rros2 run delto_3f_driver main_node --ros-args -p port_name:=/dev/ttyUSB0 -r joint_states:=gripper_joint_states
```

## Usage
```bash
ros2 action send_goal /gripper_command control_msgs/action/GripperCommand "{command: {position: 0.0, max_effort: 0}}"
ros2 action send_goal /gripper_command control_msgs/action/GripperCommand "{command: {position: 1.0, max_effort: 100}}"
```