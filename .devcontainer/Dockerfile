FROM ros:foxy

SHELL ["/bin/bash", "-c"]
RUN /bin/bash -c "source ~/.bashrc"

#basic env
RUN echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc && \
    source /opt/ros/foxy/setup.bash && \
    apt-get update && \
    apt install -y python3-pip nano openssh-server systemctl udev swig  && \
    pip install rosdep  && \
    rm /etc/ros/rosdep/sources.list.d/20-default.list && \
    rosdep init && rosdep update

#ydlidar build
RUN git clone https://github.com/YDLIDAR/YDLidar-SDK.git && \
    mkdir -p YDLidar-SDK/build  && \
    cd YDLidar-SDK/build && cmake .. && \
    make && make install && \
    cd .. && \
    pip install . && \
    cd .. && rm -r YDLidar-SDK

#LIMO package install
RUN mkdir -p LIMO_ROS2 && cd LIMO_ROS2 && \ 
    git clone --recursive https://github.com/agilexrobotics/limo_ros2.git src && \
    rosdep install --from-paths src --ignore-src -r -y && \
    cd .. && rm -r LIMO_ROS2
    echo "source /workspaces/install/setup.bash" >> ~/.bashrc && \