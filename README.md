# Introduction
This article primarily introduces how to install ROS2 Humble on the EMS-TGL Ubuntu 22.04 environment provided by Avalue Technology Inc.

## Configure ROS2 apt Repository
### Ensure that the Ubuntu Universe repository is enabled
```bash
sudo apt update
sudo apt install -y software-properties-common curl
sudo add-apt-repository universe
```

## Add ROS2 GPG Key and Repository
```bash
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] \
http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

## Install ROS2 Humble
```bash
sudo apt update
sudo apt install -y ros-humble-desktop
```

## Configure ROS2 Environment
```bash
sudo nano ~/.bashrc
```
Please add the following content to the end of the file: ~/.bashrc.
```
# ROS 2 Humble
source /opt/ros/humble/setup.bash
export ROS_DISTRO=humble
export RMW_IMPLEMENTATION=rmw_fastrtps_cpp
```

## Testing
```bash
# In one terminal
. ~/ros2_humble/ros2-linux/setup.bash
ros2 run demo_nodes_cpp talker

# In another terminal
. ~/ros2_humble/ros2-linux/setup.bash
ros2 run demo_nodes_py listener
```

# Reference.
[Ubuntu (binary) — ROS2 Documentation: Humble documentation](https://docs.ros.org/en/humble/Installation/Alternatives/Ubuntu-Install-Binary.html#)
