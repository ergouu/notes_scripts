#add repository

sudo apt-add-repository universe
sudo apt-add-repository multiverse
sudo apt-add-repository restricted



#setup sources
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
# Setup keys
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

#update package

Sudo apt-get update

#Installing bootstrap dependencies
sudo apt-get install python-rosdep python-rosinstall-generator python-wstool python-rosinstall build-essential -y

#Initializing rosdep
sudo rosdep init
rosdep update


#Create a catkin Workspace
mkdir ~/ros_catkin_ws
cd ~/ros_catkin_ws

#install desktop-notfull
rosinstall_generator desktop --rosdistro melodic --deps --tar > melodic-desktop.rosinstall
wstool init -j8 src melodic-desktop.rosinstall


#!!if install desktop-full
osinstall_generator desktop_full --rosdistro melodic --deps --tar > melodic-desktop-full.rosinstall
wstool init -j8 src melodic-desktop-full.rosinstall


#Resolving Dependencies
rosdep install --from-paths src --ignore-src --rosdistro melodic -y


#Building the catkin Workspace
./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release

source ~/ros_catkin_ws/install_isolated/setup.bash


#HOW to update and rebuild the catkin workspace, use desktop-full as the example

mv -i melodic-desktop-full.rosinstall melodic-desktop-full.rosinstall.old
rosinstall_generator desktop_full --rosdistro melodic --deps --tar > melodic-desktop-full.rosinstall


diff -u melodic-desktop-full.rosinstall melodic-desktop-full.rosinstall.old
wstool merge -t src melodic-desktop-full.rosinstall
wstool update -t src

#After update it ,you have to rebuild
./src/catkin/bin/catkin_make_isolated --install
source ~/ros_catkin_ws/install_isolated/setup.bash


#install VNC server ,to run this scriptps

#​ ​################################################################## 
#​ Script Name : vnc-startup.sh
#​ Description : Perform an automated install of X11Vnc
#​ Configure it to run at startup of the machine
#​ Date : Feb 2016
#​ Written by : Griffon
#​ Web Site :http://www.c-nergy.be - http://www.c-nergy.be/blog
#​ Version : 1.0
#
#​ Disclaimer : Script provided AS IS. Use it at your own risk.... #
#​ ​#################################################################
#​ Step 1 - Install X11VNC
#​ ​################################################################# 
sudo apt-get install x11vnc -y
#​ Step 2 - Specify Password to be used ​for​ VNC Connection
#​ ​#################################################################
sudo x11vnc -storepasswd /etc/x11vnc.pass
  
#​ Step 3 - Create the Service Unit File
#​ ​#################################################################
cat > /lib/systemd/system/x11vnc.service << EOF
[Unit]
Description=Start x11vnc at startup.
After=multi-user.target
[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repeat
-rfbauth /etc/x11vnc.pass -rfbport 5900 -shared
[Install]
WantedBy=multi-user.target
EOF
#​ Step 4 -Configure the Service
#​ ​################################################################
echo "Configure Services"
sudo systemctl enable x11vnc.service
sudo systemctl daemon-reload
sleep  5s
sudo shutdown -r now




