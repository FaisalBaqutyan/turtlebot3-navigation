# turtlebot3-navigation


in this section i will explain how turtlebot3 navigation works, i'm using here ros2 humble 


## install backges 
first we have to install the required packges 

```
sudo apt install ros-humble-gazebo
sudo apt install ros-humble-cartographer
sudo apt install ros-humble-cartographer-ros
sudo apt install ros-humble-navigation2
sudo apt install ros-humble-nav2-bringup
sudo apt install ros-humble-dynamixel-sdk
sudo apt install ros-humble-turtlebot3-msgs
sudo apt install ros-humble-turtlebot3
```


## gazebo simulation
for the navigation we have to first start the gazebo simulation

i will export the model first 

```
export TURTLEBOT3_MODEL=waffle
source /usr/share/gazebo/setup.bash
```

next we can launch the simulation 

```
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

![Screenshot from 2024-07-28 13-27-14](https://github.com/user-attachments/assets/c7d624a7-3f7a-45ee-8e86-926f7f4c6e1b)


to control the robot i will open another terminal and write 

```
ros2 run turtlebot3_teleop teleop_keyboard
```

![Screenshot from 2024-07-28 13-31-23](https://github.com/user-attachments/assets/fe5a7d0d-5f9d-4e57-bd10-77cf4d63438d)


## navigation 

for the navigation i will run the SLAM node in another terminal after i simulate  gazebo

```
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
```

next i opened a new terminal to control the robot


![Screenshot from 2024-07-28 14-01-58](https://github.com/user-attachments/assets/1f8910eb-3fb4-441e-b9e8-c29a90e536c1)


finally, after the mab is commpleted i opened a new terminal and saved the mab 

```
ros2 run nav2_map_server map_saver_cli -f ~/map
```



