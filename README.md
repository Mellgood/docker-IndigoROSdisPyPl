# docker-IndigoROSdisPyPl
A Docker container with Ubuntu 14, ROS Indigo, Gazebo, Python 3 and SWI-Prolog (it is compatible with SICStus Prolog and contains all its dependencies, so you can buy and install it too inside this container). \
ROS ad the catkin workspace are still configured and you just have to run use all the environment only, so you don't need to configure anything, 

## Instructions:
1.  **To get the Docker container:** \
        docker pull agnesesalutari/docker-indigorosdispypl
2.  **To allow visualization:** \
        xhost +local:root
3.  **To run the container (you have tu use this command for the very first time you run the container only):** \
        docker run -it \\ \
        --name="IndigoROSdisPyPl" \\ \
        --env="DISPLAY" \\ \
        --env="QT_X11_NO_MITSHM=1" \\ \
        --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \\ \
        agnesesalutari/docker-indigorosdispypl \\ \
        rqt \
        export containerId=$(docker ps -l -q)
 4.  **To work inside the container:** \
        docker exec -it "IndigoROSdisPyPl" bash
 5.  **(OPTIONAL) To re-configure ROS use the following lines, changing the parameter values, if needed:**
    - **Enable bash to provide all ROS related commands:** 
        source /opt/ros/indigo/setup.bash
    - **In order to work in an network environment:**\
        export ROS_MASTER_URI="http://127.0.0.1:11311" \
        export ROS_HOSTNAME="127.0.0.1" \
        export ROS_IP="127.0.0.1"
    - **Create catkin workspace:** \
         mkdir -p ~/catkin_ws/src \
          cd ~/catkin_ws/src \
          catkin_init_workspace
    - **Test:** \ 
        cd ~/catkin_ws/ \
        catkin_make \
        source devel/setup.bash
    - **In order to reference the newly created local workspace in our bashrc (to make tools, like roslaunch and rosrun, able to       find the customly created packages):** \
         source catkin_ws/devel/setup.bash
 6.  **To open Gazebo GUI:** \
    gazebo
 7. **To exit the container:** \
    exit
 8.  **(IMPORTANT) To save the container state, not to lose your work on it:** \
    docker commit "IndigoROSdisPyPl"
 9.  **To stop the container:** \
    docker stop "IndigoROSdisPyPl"
 10.  **After using the container:** \
    xhost -local:root
 11.  **Tu run the container again:** \
    docker start "IndigoROSdisPyPl"
