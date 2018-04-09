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
10. Add `192.168.1.33 theboatdoctor-nuc` to the `/etc/hosts` file. 
11. Enable ssh on the raspberry pi using `raspi-config`
12. Download and install VNCserver from here: https://www.realvnc.com/en/connect/download/vnc/raspberrypi/
13. Add the following lines to your ~/.bashrc
```
source /opt/ros/kinetic/setup.bash
source ~/catkin_ws/devel/setup.bash
export ROS_MASTER_URI="http://192.168.1.33:11311"
export ROS_HOSTNAME="192.168.1.30"
export ROS_IP="192.168.1.30"
``` 
14. Install rosserial library following instructions here: http://wiki.ros.org/rosserial_arduino/Tutorials
15. Clone the SparkFun LSM9DS1 Arduino Library into the Arduino sketchbook's libraries folder using `git clone https://github.com/sparkfun/SparkFun_LSM9DS1_Arduino_Library.git`. Then copy all of the files from the src folder into the main folder and delete the src folder.

## VNC Instructions:
1. Press the robot's power button, which will turn on the Raspberry Pi and router automatically.
2. Wait a minute or 2 for the Raspberry Pi to properly boot up.
3. Connect your computer to the router by connecting to The Boat Doctor wifi with password `TheBoatDoctor`.
4. On your computer, ssh to `theboatdoctor-pi@192.168.1.30` or type `sshpi` if you are on the NUC and enter the password `TheBoatDoctor`.
5. Then type `vncserver` in the ssh terminal and note down the ip address that the vnc server is broadcasting on.
6. Reconnect to CMU-SECURE, open up VNC Viewer and enter the ip address that was displayed in the ssh terminal. Enter `theboatdoctor-pi` as the username with the password `TheBoatDoctor`.

## Uploading code to the Arduino using the VNC
1. Type `sudo chmod a+rw /dev/ttyACM0` or `chmodmega` in the terminal and enter the password `TheBoatDoctor`.
2. Then on the top left corner of the screen, select Applications > Programming > Arduino IDE
3. An error message will pop up on screen, but just press `Add`.
4. When the Arduino IDE window opens, if you have trouble seeing the entire window, go to the bottom of the VNC window and right click the Arduino window and select `Always on top`.
5. Now go to the top left corner of the window and select File > Sketchbook > TheBoatDoctorArduino.
6. Make sure that Tools > Board has the Arduino Mega 2560 or Mega ADK selected and Tools > Serial Port has /dev/ttyACM0 selected.
7. Click the Upload button and wait for the entire program to be compiled and uploaded to the Arduino Mega.

## Issues accessing the Internet
1. Disconnect from TheBoatDoctorEthernet if you encounter any trouble with accessing the internet.