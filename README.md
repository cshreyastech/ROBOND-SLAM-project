## Project: SLAM README

#### Packages required
1. Install ROS
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' && sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116 && sudo apt-get update && sudo apt-get install ros-kinetic-desktop-full && sudo rosdep init && rosdep update && echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc && source ~/.bashrc

Note: Skip this step if ROS is already installed. 
```

2. Install dependencies
```
sudo apt-get install ros-kinetic-rtabmap ros-kinetic-rtabmap-ros && sudo apt-get remove ros-kinetic-rtabmap ros-kinetic-rtabmap-ros
```

3. Install RTAB-Map
```
cd ~ && git clone https://github.com/introlab/rtabmap.git rtabmap && cd rtabmap/build && cmake .. && make && sudo make install
```

4. create .gazebo folder
```
Open gazebo and then close it.
```

5. Add model collision adjustments
```
curl -L https://s3-us-west-1.amazonaws.com/udacity-robotics/Term+2+Resources/P3+Resources/models.tar.gz | tar zx -C ~/.gazebo/
```

6. Install turtlebot teleop packages in src folder
```
git clone https://github.com/turtlebot/turtlebot_simulator
git clone https://github.com/turtlebot/turtlebot
```

7. Install dependencies from catkin folder
```
source devel/setup.bash
rosdep -i install turtlebot_gazebo
rosdep -i install turtlebot_teleop
```

---
#### Steps to run SLAM poject
Open first terminal
```
source devel/setup.bash
roslaunch explore_bot new_world.launch
```

Open second terminal
```
source devel/setup.bash
roslaunch explore_bot teleop.launch
```

Open third terminal
```
source devel/setup.bash
roslaunch explore_bot mapping.launch
```
Open forth terminal
```
source devel/setup.bash
roslaunch explore_bot rviz.launch
```
Open fifth terminal
```
rtabmap-databaseViewer ~/.ros/rtabmap.db
```

```
---
