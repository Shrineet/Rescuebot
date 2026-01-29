**Autonomous Search and Rescue Robot using TurtleBot3 (Waffle) and ROS2**  

**Project Overview**  


This project implements an Autonomous Search and Rescue Robot using ROS2 Humble and TurtleBot3 Waffle in a simulated environment.
The robot operates in a custom rescue world, executes autonomous rescue behavior, and reports detected victim positions.

The system is designed to be run using multiple ROS2 nodes, each responsible for a specific task such as simulation, rescue logic, and victim pose reporting.

**Main Features**  

1) Custom Gazebo rescue environment
2) Autonomous rescue behavior node
3) Victim pose reporting
4) Modular ROS2 architecture
5) TurtleBot3 Waffle robot model

**Technologies Used**  

1) ROS2 Humble Hawksbill
2) TurtleBot3 (Waffle)
3) Gazebo Simulator
4) Python

**📂 Workspace Structure**
```bash
rescue_ws/
├── src/
│   ├── rescue_worlds/        # Custom Gazebo rescue world
│   ├── rescue_behavior/      # Main rescue logic and behavior nodes
│   └── other ROS2 packages
├── build/
├── install/
└── log/
```

**Prerequisites**  
Before running the project, make sure the following are installed:

1) Ubuntu 22.04
2) ROS2 Humble
3) Gazebo
4) TurtleBot3 packages
5) Colcon

**Install TurtleBot3 packages:**

```bash
_sudo apt install ros-humble-turtlebot3*_
```

**How to Run the Project**

_**Terminal 1: Launch Simulation (Gazebo World)**_
This terminal starts the ROS2 environment and launches the custom rescue simulation world.

```bash
_source /opt/ros/humble/setup.bash
ros2 launch rescue_worlds rescue_tb3_world.launch.py_
```

**Purpose:**  
Sets up ROS2 environment
Launches a custom TurtleBot3 rescue world in Gazebo
Starts the simulation with obstacles and victims



_**Terminal 2: Build Workspace and Run Rescue Node**_  
This terminal builds the workspace and runs the main rescue behavior node.

```bash
_source /opt/ros/humble/setup.bash
cd ~/MyLab/rescue_ws
rm -rf build install log
colcon build --symlink-install
source install/setup.bash
ros2 run rescue_behavior rescue_node_
```

**Purpose:**  
Cleans old build files
Builds the entire workspace
Sources the newly built environment
Runs the main rescue logic node that controls the robot



_**Terminal 3: Run Victim Pose Reporter Node**_  
This terminal runs a helper node that continuously reports victim positions.

```bash
_source /opt/ros/humble/setup.bash
cd ~/MyLab/rescue_ws
source install/setup.bash
ros2 run rescue_behavior victim_pose_reporter_
```

 **Purpose:**  
Runs a separate node to report victim positions
Publishes victim pose information (position and orientation)
Useful for monitoring and debugging rescue performance


**All three terminals must run at the same time:**  
Terminal 1: Gazebo simulation + rescue world
Terminal 2: Main autonomous rescue behavior
Terminal 3: Victim pose reporting

Together, these components enable a complete autonomous search and rescue workflow.

**Expected Output**  

Gazebo simulation launches successfully
TurtleBot3 Waffle moves autonomously
Rescue behavior node controls robot actions
Victim positions are continuously reported
