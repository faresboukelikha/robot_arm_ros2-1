# 🚀 Robot urdf (Dual-Robot Visual & Simulation Project)
This package features a second custom robot designed in SolidWorks and integrated into ROS 2 for Gazebo simulation, alongside a cinematic Blender animation of the robot carrying a box and edited with After Effects.
## 🛠️ Prerequisites & Installation
Run the following command to automatically install dependencies found in the workspace:
```bash
rosdep install -i --from-path src --rosdistro jazzy -y
```
## 🏃 Execution Steps
Follow these terminal commands in order to bring the robot to life:

### 1️⃣ Terminal 1: Build & Launch Simulation
This command compiles the workspace, opens Gazebo, and spawns the robot arm in the world.
```bash
colcon build --packages-select robot_urdf
source install/setup.bash
ros2 launch robot_urdf gazebo.launch.py
```
### 2️⃣ Terminal 2: ROS-Gazebo Bridge
This starts the communication bridge that allows ROS 2 to send trajectory messages to the Gazebo simulation.
```bash
source install/setup.bash
ros2 run ros_gz_bridge parameter_bridge /model/RobotURDF/joint_trajectory@trajectory_msgs/msg/JointTrajectory@gz.msgs.JointTrajectory
```
### 3️⃣ Terminal 3: Robot Control GUI
Activate the "Sliders" window to manually control each joint of the arm in real-time.
```bash
source install/setup.bash
ros2 run rqt_joint_trajectory_controller rqt_joint_trajectory_controller
```

## 📂 File Structure Breakdown

| File/Folder | Description |
| :--- | :--- |
| **`config/`** | YAML files defining controller types and joint limits. |
| **`launch/`** | Python launch scripts for spawning the robot and starting nodes. |
| **`meshes/`** | High-quality **.STL** files exported from SolidWorks (Base, Links, and Gripper). |
| **`urdf/`** | The **RobotURDF.urdf** file containing the complete kinematic chain. |
| **`blender/`** | Contains the **.blend** file for the box-carrying animation and VFX. |
| **`CMakeLists.txt`** | Build instructions for the Colcon build system. |
| **`package.xml`** | Manifest file listing project dependencies (ROS 2 Jazzy). |
