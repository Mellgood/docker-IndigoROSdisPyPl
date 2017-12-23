# docker-IndigoROSdisPyPl
A Docker container with Ubuntu 14, ROS Indigo, Gazebo Gzweb, Python 3 and SWI-Prolog (it is compatible with SICStus Prolog and contains all its dependencies, so you can buy and install it too inside this container).

## Instructions:
-  docker pull agnesesalutari/docker-indigorosdispypl
-  xhost +local:root
-  **To run the container (you have tu use this command for the very first time you run the container only):** \
    docker run -it \\ \
    --name="IndigoROSdisPyPl" \\ \
    --env="DISPLAY" \\ \
    --env="QT_X11_NO_MITSHM=1" \\ \
    --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \\ \
    agnsal/docker-IndigoROSdisPyPl \\ \
    rqt
    export containerId=$(docker ps -l -q)
 -  **To work with the container:** \
    docker exec -it "IndigoROSdisPyPl" bash
 -  **To open Gazebo Gzweb GUI:** \
    gazebo
 -  **To exit and stop the container:** \
    exit \
    docker stop IndigoROSdisPyPl
 -  **After using the container:** \
    xhost -local:root
 -  **Tu run the container again:** \
    docker start "IndigoROSdisPyPl"
