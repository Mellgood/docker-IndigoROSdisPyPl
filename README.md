# docker-ROS_Indigo_Gzweb
A docker container with Ubuntu 14, ROS Indigo and Gazebo Gzweb.

## Instructions:
-  docker pull agnsal/docker-ROS_Indigo_Gzweb
-  sudo usermod -a -G docker <username>
-  xhost +local:root
-  **To run the container (you have tu use this command for the very first time you run the container only):** \
    docker run -it
    --env="DISPLAY"
    --env="QT_X11_NO_MITSHM=1"
    --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw"
    agnsal/docker-ROS_Indigo_Gzweb
    rqt
    export containerId=$(docker ps -l -q)
 -  **To open Gazebo Gzweb GUI:** \
    gazebo
 -  **To stop the container:** \
    docker stop agnsal/docker-ROS_Indigo_Gzweb
 -  **After using the container:** \
    xhost -local:root
 -  **Tu run the container again:** \
    docker start <containerId>
