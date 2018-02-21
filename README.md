# TheBoatDoctorRaspberryPi

## Setup Instructions:
1.  Download Ubuntu MATE 16.04.2 (Xenial) for the Raspberry Pi from here: https://ubuntu-mate.org/download/
2.  Follow instructions here to mount the Ubuntu MATE img onto the microSD card for the Raspberry Pi: https://ubuntu-mate.org/raspberry-pi/
3.  Insert the microSD card into the Raspberry Pi and follow the installation instructions.
4.  Connect to the CMU-SECURE wireless network following instructions here: https://www.cmu.edu/computing/services/endpoint/network-access/wireless/how-to/connect.html (You can install the certificate by loading it on a usb drive or briefly turning on your phone's hotspot and allowing the Raspberry Pi to connect to internet through the hotspot.)
5.  Run sudo apt update && sudo apt upgrade
6.  Firefox will be broken afterwards so follow all of the instructions here to fix firefox: https://steemit.com/technology/@neuromancer/fix-crashing-firefox-after-update-on-linux-systems-by-downgrading-the-fast-and-simple-method
7.  Next, follow this guide to enable to Raspberry Pi Camera: https://larrylisky.com/2016/11/24/enabling-raspberry-pi-camera-v2-under-ubuntu-mate/
8.  Install ROS Kinetic following instructions here: http://wiki.ros.org/kinetic/Installation/Ubuntu
9.  Install raspicam\_node following instructions here: https://github.com/UbiquityRobotics/raspicam_node
10. Enable ssh on the raspberry pi using `raspi-config`
11. Add the following lines to your ~/.bashrc
```
source /opt/ros/kinetic/setup.bash
source ~/catkin_ws/devel/setup.bash
export ROS_MASTER_URI="http://192.168.1.33:11311"
export ROS_HOSTNAME="192.168.1.30"
export ROS_IP="192.168.1.30"
```
