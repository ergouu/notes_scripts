# You Just  need to choose one(1 or 2) of the two methods to install ROS, do not install ROS twice!

# 1.Install Melodic by apt-get

#install desktop-full (PC or SDK env)

$ sudo apt-get install -y ros-melodic-desktop-full

#or just install desktop(in jetson tx2)

$ sudo apt-get install -y ros-melodic-desktop

# 2.Install  Melodic by Source(Not recommeded)

#add repository

$ sudo apt-add-repository universe

$ sudo apt-add-repository multiverse

$ sudo apt-add-repository restricted



#setup sources

$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

#Setup keys

$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116

#update package

$ sudo apt-get update

#Installing bootstrap dependencies

$ sudo apt-get install python-rosdep python-rosinstall-generator python-wstool python-rosinstall build-essential -y

#Initializing rosdep

$ sudo rosdep init

$ rosdep update


#Create a catkin Workspace

$ mkdir ~/ros_catkin_ws

$ cd ~/ros_catkin_ws

#install desktop-notfull

$ rosinstall_generator desktop --rosdistro melodic --deps --tar > melodic-desktop.rosinstall

$ wstool init -j8 src melodic-desktop.rosinstall


#!!if install desktop-full

$ osinstall_generator desktop_full --rosdistro melodic --deps --tar > melodic-desktop-full.rosinstall
$ wstool init -j8 src melodic-desktop-full.rosinstall


#Resolving Dependencies

$ rosdep install --from-paths src --ignore-src --rosdistro melodic -y


#Building the catkin Workspace

$ ./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release

$ source ~/ros_catkin_ws/install_isolated/setup.bash


#HOW to update and rebuild the catkin workspace, use desktop-full as the example

$ mv -i melodic-desktop-full.rosinstall melodic-desktop-full.rosinstall.old

$ rosinstall_generator desktop_full --rosdistro melodic --deps --tar > melodic-desktop-full.rosinstall


$ diff -u melodic-desktop-full.rosinstall melodic-desktop-full.rosinstall.old

$ wstool merge -t src melodic-desktop-full.rosinstall

$ wstool update -t src

#After update it ,you have to rebuild

$ ./src/catkin/bin/catkin_make_isolated --install

$ source ~/ros_catkin_ws/install_isolated/setup.bash
