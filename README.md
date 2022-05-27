# Research Track II Assignment 1.2 description:

Assignment 1.2 for Research  II course, The assigemnt depends on Jupyter notbook to control previous simulation of Research Track Assignment 3 (please check previous repo):   
https://github.com/youssefattia98/Research-Track-I-3.git       
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

https://user-images.githubusercontent.com/69837845/169133911-7c5d3031-20aa-4a92-9878-ef7c49fbbab3.mp4  

This speed up video shows a testing of each cell of the Jupyter code and how the robot is controlled throw it.

3)Future Improvments. 
================================
Add speed slider
----------------------

It was noticed that the robot control in the second and the third choice was too slow and the user may want to increase the robot speed, so it better for future improvemnts to add a slider to control the robot speed. It will be simple modification in the following lines:

Better on Native linux
----------------------
Connect GPU to Docker
----------------------


