# Aliengo workspaces

## Sub-workspaces
* aliengo-slam-ws
The native aliengo script, not used anywhere in the system.

* aliengo-legged-ws
The native aliengo low-level motion control library, also used by the aliengo controller. And a high-level library that is interfaced with slam package.

* aliengo-slave-catkin-ws(ROS)
The main workspace for slam activities. There is also a multi-machine communication package(aliengo-master-catkin-ws/src/multi_machine) that can send custom message to master.

* aliengo-master-catkin-ws(ROS)
This workspace contains launch files on master machine side. There is also a multi-machine communication package(aliengo-master-catkin-ws/src/multi_machine) that can receive custom message from slave.

## What have been done

- [x] Built and tested user-level controlling library for aliengo
- [x] Installed and tested slam system(using slamware lidar)
- [ ] Full testing
    - [x] Built the message between the master and slave machine
    - [ ] Full testing from the planned path to motion control

        