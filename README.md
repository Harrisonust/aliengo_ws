# Aliengo workspaces

## Sub-workspaces
* aliengo-slam-ws
The native aliengo script, not used anywhere in the system.

* aliengo-legged-ws
The native aliengo low-level motion control library, also used by the aliengo controller. And an add-on high-level motion control library that is interfaced with slam package.

* aliengo-slave-catkin-ws(ROS)
The main workspace for slam activities. There is also a multi-machine communication package(aliengo-master-catkin-ws/src/multi_machine) that can send customized messages to the master.

* aliengo-master-catkin-ws(ROS)
This workspace contains launch files on the master machine side. There is also a multi-machine communication package(aliengo-master-catkin-ws/src/multi_machine) that can receive customized messages from the slave.

## Workflow
1. Launch the slam package in aliengo-slave-catkin-ws
    ```sh
    roslaunch slamware_ros_sdk_server_node.launch 
    ```

2. Send the position target from slave to master machine, this is supported natively by ROS
    Connect the network of two machines(set ROS_MASTER_URI). Check out `ROS_MASTER_URI` under http://wiki.ros.org/ROS/EnvironmentVariables

3. The master machine receives the command from slam, and feeds them to the leg controller
    ```sh
    sudo ./aliengo-legged-ws/build/optimal_nav
    ```
    The code runs in a forever loop and will keep listening the planned position and producing optimal motions.

## What have been done

- [x] Built and tested user-level controlling library for aliengo
- [x] Installed and tested slam system(using slamware lidar)
- [ ] Full testing
    - [x] Built the message between the master and slave machine
    - [ ] Full testing from the planned path to motion control

