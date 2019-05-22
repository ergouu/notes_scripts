#To view the computer graph ,firstly ,install the rqt tools

$ sudo apt-get install ros-<distro>-rqt
$ sudo apt-get install ros-<distro>-rqt-common-plugins

#run the tool

$ rosrun rqt_graph rqt_graph

#rostopic

#show the data published on a topic

$ rostopic echo [topic]

#show all topic 

$ rostopic list

#show type of the topic

$ rostopic type [topic]

#look details of the mesgs using rosmsg

$ rosmsg show [msg_type]

#or using pipeline

$ rostopic type [topic]|rosmsg show

#then we can publish the msg by manual using 

$ rostopic pub [topic] [msg_type] [args]

#such as I publish the msg of driving the racecar moving by

$ rostopic pub -l /vesc/low_level/ackermann_cmd_mux/output ackermann_msgs/AckermannDriveStamped -- '[38000,0,"0"]' '[-0.5,0.75,300,0,0.75,0.0]'

#the command publish message only once ,to publish message in specific hz by using -r

$ rostopic pub /vesc/low_level/ackermann_cmd_mux/output ackermann_msgs/AckermannDriveStamped -r 60 -- '[38000,0,"0"]' '[-0.5,0.75,300,0,0.75,0.0]'

#see how fast the node is publishing:

$ rostopic hz [topic]

# to plot the topic

$ rosrun rqt_plot rqt_plot

#then typing the topic which you want to plot and press plus button
