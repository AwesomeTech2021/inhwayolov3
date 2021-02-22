- jetson-torch
https://forums.developer.nvidia.com/t/pytorch-for-jetson-version-1-7-0-now-available/72048/5

- discord install
https://linuxconfig.org/how-to-install-discord-on-ubuntu-18-04-bionic-beaver-linux

- gazebo9 install
https://www.programmersought.com/article/57944393651/

- gazebo에서 drone 실행하는 방법 -> 순서대로 하기
1. https://docs.px4.io/master/en/dev_setup/dev_env_linux_ubuntu.html#gazebo-jmavsim-and-nuttx-pixhawk-targets
2. https://docs.px4.io/master/en/simulation/gazebo.html

- qgroundcontrol install
https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html
 
     -> sudo usermod -a -G dialout 사용자이름
 
- qgroundcontrol 3.5.6
 https://github.com/mavlink/qgroundcontrol/releases/tag/v3.5.6

- 이 에러 날때
Unable to register with master node [http://localhost:11311/]: master may not be running yet. Will keep trying.
     -> roscore 명령어 실행

- roscore 안될 때
https://answers.ros.org/question/60366/problem-with-roscore/

- Obstacle avoidance base setting
https://github.com/Jaeyoung-Lim/avoidance

- roslauch 실행할 때 반복해야할 것

cd ~/Firmware

export QT_X11_NO_MITSHM=1

make px4_sitl_default gazebo

. ~/Firmware/Tools/setup_gazebo.bash ~/Firmware ~/Firmware/build/px4_sitl_default

export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:~/Firmware

echo export GAZEBO_MODEL_PATH=${GAZEBO_MODEL_PATH}:~/catkin_ws/src/avoidance/avoidance/sim/models:~/catkin_ws/src/avoidance/avoidance/sim/worlds >> ~/.bashrc

source ~/catkin_ws/devel/setup.bash

roslaunch global_planner global_planner_stereo.launch

rosrun mavros mavsys mode -c OFFBOARD
rosrun mavros mavsafety arm

gz camera --camera-name=gzclient_camera --follow=iris

roslaunch safe_landing_planner safe_landing_planner.launch

- Obstacle avoidance
https://github.com/mmmmmmwei/obstacle_avoidance_drone

- catkin build error
https://github.com/catkin/catkin_tools/issues/525

- sudo apt install libpcl1 ros-melodic-octomap-* ros-melodic-yaml-* no package error
    
    sudo apt install libpcl1 ros-melodic-octomap-* 만 진행
    
- RLException: while processing /home/inhwa/catkin_ws/src/avoidance/global_planner/launch/mavros_sitl.launch:
Invalid roslaunch XML syntax: [Errno 2] No such file or directory: u'/home/inhwa/catkin_ws/src/avoidance/global_planner/launch/mavros_sitl.launch'
The traceback for the exception was written to the log file

    경로 바꿔줘야 함
