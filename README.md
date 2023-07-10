# SLAM-Based Interactive Robot Navigator - Jupyter Enhancement:

The project depends on Jupyter notbook to control previous simulation of SLAM-Based Interactive Robot Navigator (please check previous repo):   
https://github.com/youssefattia98/SLAM-Based-Interactive-Robot-Navigator.git    
This repo consists of the following points:  
 1)How to Setup the Simulator and Jupyter.   
 2)Final output.  
 3)Essential improvements.       

1)How to Setup the Simulator and Jupyter.  
================================

The simulator requires specific ROS version and I recommend using the Docker image dedicated to this course to make installation and running easier. After cloning the repo to the ROS work space and building it:      
```bash
$ catkin_make
``` 
 The following commands should be used in the workspace directory to install.

```bash
$ sudo apt-get install konsole
$ sudo bash run.sh
```
If console application is not preferred installed the simulation can be run using the following commands.

```bash
$ sudo roslaunch final_assignment simulation_gmapping.launch 
$ sudo roslaunch final_assignment move_base.launch
$ sudo roslaunch ass3 launcheverything.launch
```
  For Jupter setup:
```bash
$ sudo jupyter notebook --allow-root --ip 0.0.0.0
$ sudo http://localhost:8888
```
  If you want to run Jupyter from windows it is possible if it is forwarded to this port like so:  
```bash
$ docker run -it --name my_jupyter -p 6080:80 -p 5900:5900 -p 8888:8888 carms84/noetic_ros2 
```

2)Final Output. 
================================


https://user-images.githubusercontent.com/69837845/170798997-f444bbc0-ee9c-4d64-b8b8-850611416786.mp4


This speed up video shows a testing of each cell of the Jupyter code and how the robot is controlled throw it.

3)Future Improvments. 
================================
Add speed slider
----------------------

It was noticed that the robot control in the second and the third choice was too slow and the user may want to increase the robot speed, so it better for future improvemnts to add a slider to control the robot speed. It will be simple modification in the following lines:
```python
    if direction == 1:
        #Front direction
        vel.linear.x = 0.5
        vel.angular.z = 0.0
    elif direction == 2:
        #Left direction
        vel.linear.x = 0.0
        vel.angular.z = 0.5
    elif direction == 3:
        #Right direction
        vel.linear.x = 0.0
        vel.angular.z = -0.5
    elif direction == 4:
        #Back direction
        vel.linear.x = -0.5
        vel.angular.z = -0.0
    elif direction ==5:
        #stop
        vel.linear.x = -0.0
        vel.angular.z = -0.0
```
in which `vel.linear.x` and `vel.angular.z` should be a global varbile controlled with a slider. Here is a simple example of a slider that can be added:
```python
widgets.FloatSlider(
    value=0.5,
    min=0,
    max=2.0,
    step=0.1,
    description='Test:',
    disabled=False,
    continuous_update=False,
    orientation='horizontal',
    readout=True,
    readout_format='.1f',
)
```

Better on Native linux
----------------------
As I have mentioned in the beginning of this readme it is recommended to use the docker image of the course to ease the setup of everything, but after testing over and over it was noticed that the docker image consumes 100% of the CPU this is due to the simulation need to Graphical processing and there is no GPU connected to the docker. After some research it was noted that there is no possible way to connect the GPU to docker if docker is running on windows, but it is possible docker is running on Linux. However, the packages that are on the internet for that case are not really user friendly and moreover it useless to have a Linux docker image on a native Linux system so at this point my conclusion is: **Try this repo on Native Linux system and not the course docker image.**  
Also, I would like to note that not everything in the code can work with eachother and it was impossible to test all the graphs at the same time due to the high CPU load as mentioned before. However, the video shows that eveything can work but it need a **HUGE CPU.**
