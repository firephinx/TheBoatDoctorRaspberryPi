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

## Startup Instructions:
1. Press the robot's power button, which will turn on the Raspberry Pi and router automatically.
2. Wait a minute or 2 for the Raspberry Pi to properly boot up.
3. Connect your laptop to the router by connecting to The Boat Doctor wifi with password `TheBoatDoctor`.
4. On your laptop, `ssh theboatdoctor-pi@192.168.1.30` and enter the password `TheBoatDoctor`.
5. Then type vncserver in the client and note down the ip address that the vnc server is broadcasting on.
6. Reconnect to CMU-SECURE and use the ip address that was displayed on VNCViewer. Enter `theboatdoctor-pi` as the username with the password `TheBoatDoctor`.

## Uploading code to the Arduino
1. Type `sudo chmod a+rw /dev/ttyACM0` in the terminal and enter the password `TheBoatDoctor`.
2. Then on the top left corner of the screen, select Applications > Programming > Arduino IDE
3. An error message will pop up on screen, but just press `Add`.
4. When the Arduino IDE window opens, if you have trouble seeing the entire window, go to the bottom of the VNC window and right click the Arduino window and select `Always on top`.
5. Now go to the top left corner of the window and select File > Open or `Ctrl-O` and find the "TheBoatDoctorArduino.ino" which should be located in the home/theboatdoctor-pi/Documents/TheBoatDoctorArduino folder.
6. Make sure that Tools > Board has the Arduino Mega 2560 or Mega ADK selected and Tools > Serial Port has /dev/ttyACM0 selected.
7. Click the Upload button and wait for the entire program to be compiled and uploaded to the Arduino Mega.

## Issues accessing the Internet
1. Disconnect from the Intranet (the ethernet connection) if you encounter troubles with accessing the internet.