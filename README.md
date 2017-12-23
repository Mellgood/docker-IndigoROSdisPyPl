# docker-IndigoROSdisPyPl
A Docker container with Ubuntu 14, ROS Indigo, Gazebo, Python 3 and SWI-Prolog (it is compatible with SICStus Prolog and contains all its dependencies, so you can buy and install it too inside this container).

## Instructions:
-  **To get the Docker container:** \
        docker pull agnesesalutari/docker-indigorosdispypl
-  **To allow visualization:** \
        xhost +local:root
-  **To run the container (you have tu use this command for the very first time you run the container only):** \
        docker run -it \\ \
        --name="IndigoROSdisPyPl" \\ \
        --env="DISPLAY" \\ \
        --env="QT_X11_NO_MITSHM=1" \\ \
        --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \\ \
        agnesesalutari/docker-indigorosdispypl \\ \
        rqt \
        export containerId=$(docker ps -l -q)
 -  **To work inside the container:** \
        docker exec -it "IndigoROSdisPyPl" bash
 -  **To configure ROS:**
    1. **Enable bash to provide all ROS related commands:** 
        source /opt/ros/indigo/setup.bash
    2. **In order to work in an network environment:**\
        export ROS_MASTER_URI="http://127.0.0.1:11311" \
        export ROS_HOSTNAME="127.0.0.1" \
        export ROS_IP="127.0.0.1"
    3. **Create catkin workspace:** \
         mkdir -p ~/catkin_ws/src \
          cd ~/catkin_ws/src \
          catkin_init_workspace
    4. **Test:** \ 
        cd ~/catkin_ws/ \
        catkin_make \
        source devel/setup.bash
    5. **In order to reference the newly created local workspace in our bashrc (to make tools, like roslaunch and rosrun, able to       find the customly created packages):** \
         source catkin_ws/devel/setup.bash
 -  **To open Gazebo GUI:** \
    gazebo
 -  **To exit and stop the container:** \
    exit \
    docker stop IndigoROSdisPyPl
 -  **After using the container:** \
    xhost -local:root
 -  **Tu run the container again:** \
    docker start "IndigoROSdisPyPl"
