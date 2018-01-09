# docker-IndigoROSdisPyPl
A Docker container with Ubuntu 14, ROS Indigo, Gazebo, Redis, Python 3 and SWI-Prolog (it is compatible with SICStus Prolog and contains all its dependencies, so you can buy and install it too inside this container). \
ROS ad the catkin workspace are still configured and you just can use all the environment without the need to configure them, but if you have to change something in the configuration please see the point 5. of the instructions below.

## Instructions:
1.  **To get the Docker container:** \
```shell
docker pull agnesesalutari/docker-indigorosdispypl
```
2.  **To allow visualization:** \
```shell
xhost +local:root
```
3.  **To run the container (you have tu use this command for the very first time you run the container only):** \
```shell
docker run -it \\ \
--name="IndigoROSdisPyPl" \\ \
--env="DISPLAY" \\ \
--env="QT_X11_NO_MITSHM=1" \\ \
--volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \\ \
agnesesalutari/docker-indigorosdispypl \\ \
rqt \
export containerId=$(docker ps -l -q)
```
 4.  **To work inside the container:** \
 ```shell
 docker exec -it "IndigoROSdisPyPl" bash
 ```
 5.  **(OPTIONAL) To re-configure ROS use the following lines, changing the parameter values, if needed:** \
 ```shell
 export ROS_MASTER_URI="http://127.0.0.1:11311" \
 export ROS_HOSTNAME="127.0.0.1" \
 export ROS_IP="127.0.0.1"
 ```
 6. **To add ROS environment variables to the bash:** \
 ```shell
 echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc \
 source ~/.bashrc
 ```
 6. **Create catkin workspace:** \
 ```shell
mkdir -p ~/catkin_ws/src \
cd ~/catkin_ws/src \
catkin_init_workspace
```
 7. **Test:** \
 ```shell
cd ~/catkin_ws/ \
catkin_make \
source devel/setup.bash
```
 8. **In order to reference the newly created local workspace in your bashrc (to make tools, like roslaunch and rosrun, able to  
     find the customly created packages):** \
```shell
source catkin_ws/devel/setup.bash
```
 9.  **To open Gazebo GUI:** \
```shell
gazebo **or** roslaunch gazebo YourFile.launch **or** rosrun gazebo_ros YourExecutable
```
 10. **To exit the container:** \
 ```shell
exit
```
 11.  **(IMPORTANT) To save the container state, not to lose your work on it:** \
 ```shell
docker commit "IndigoROSdisPyPl"
```
 12.  **To stop the container:** \
 ```shell
docker stop "IndigoROSdisPyPl"
```
 13.  **After using the container:** \
 ```shell
xhost -local:root
```
 14.  **Tu run the container again:** \
 ```shell
docker start "IndigoROSdisPyPl"
```
