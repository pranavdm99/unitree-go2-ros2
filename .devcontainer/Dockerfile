FROM osrf/ros:humble-desktop

USER root

# Install basic tools
RUN apt update && apt install -y git wget curl software-properties-common lsb-release gnupg xterm

# Install clang tools
RUN wget https://apt.llvm.org/llvm.sh && chmod +x llvm.sh && ./llvm.sh 18 all
RUN update-alternatives --install /usr/bin/clangd clangd /usr/bin/clangd-18 100 \
    && update-alternatives --install /usr/bin/clang++ clang++ /usr/bin/clang++-18 100 \
    && update-alternatives --install /usr/bin/clang clang /usr/bin/clang-18 100 \
    && update-alternatives --install /usr/bin/clang-tidy clang-tidy /usr/bin/clang-tidy-18 100 \
    && update-alternatives --install /usr/bin/run-clang-tidy run-clang-tidy /usr/bin/run-clang-tidy-18 100
ENV CC=/usr/bin/clang-18
ENV CXX=/usr/bin/clang++-18

WORKDIR /workspace
ENV RMW_IMPLEMENTATION=rmw_cyclonedds_cpp

# Configure bash
RUN echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
RUN apt update && apt install -y \
    ros-humble-rmw-cyclonedds-cpp \
    ros-humble-rosidl-generator-dds-idl \
    ros-humble-gazebo-ros \
    ros-humble-gazebo-ros-pkgs \
    ros-humble-gazebo-plugins \
    ros-humble-ros2-control \
    ros-humble-ros2-controllers \
    ros-humble-gazebo-ros2-control \
    ros-humble-joint-state-publisher \
    ros-humble-joint-state-publisher-gui \
    ros-humble-xacro \
    ros-humble-teleop-twist-keyboard \
    ros-humble-controller-manager \
    ros-humble-robot-localization \
    ros-humble-joy \
    ros-humble-velodyne \
    ros-humble-velodyne-gazebo-plugins \
    ros-humble-velodyne-description \
    ros-humble-velodyne-msgs \
    ros-humble-velodyne-pointcloud \
    ros-humble-velodyne-driver \
    ros-humble-velodyne-laserscan

CMD [ "bash" ]