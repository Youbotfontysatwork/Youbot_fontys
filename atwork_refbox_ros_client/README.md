Refere box client



The implementation made of the referee box communication is set of 3 nodes written in cpp and a launch file connected to the robot_example_ros node, the one from the referee box client, in the following structure pictured in the rqt graph.
![alt text](https://github.com/Youbotfontysatwork/youbot_fontys/blob/master/atwork_refbox_ros_client/rqt.png)
The three nodes are the logging_node, a publisher sending a boolean to the robot_example_ros node transmitting to the referee box that the robot is in fact logging to send the tasks. The inventory_sender is subscribed to the robot_example_node to get the competition messages data of the items to be picked and publishes them as string data. Finally the task_sender is also subscribed to the to the robot_example_ros to get the data of the locations the robot has to go. From the ros parameters in transforms the positions in geometry pose data to publish it.

Referee box client Logging node:

This node is a publisher sending the information that the robot logging. The type of message is specific to this competition it is an atwork_ros_msgs::LoggingStatus. This type of message is the type supported by the topic to which it publishes /robot_example_ros/logging_status. The include files of the atwork_ros_msgs is provided by the referee box ros communication package. This node is made of one main loop, where all the Ros functions are called to declare the components of a ros publisher. Further, the while loop is responsible for publishing the msg which is a boolean set on True, meaning that the robot is in fact logging as shown in the screenshot below of the atwork-view.
![alt text](https://github.com/Youbotfontysatwork/youbot_fontys/blob/master/atwork_refbox_ros_client/loggingg.png)

Referee box client Inventory Sender:

The referee box client inventory sender subcribes to two topics the task_info and the inventory to gather information on the location of the objects and the object itself. The structure of the code is a such, 2 void callbacks from the two nodes and a main loop declaring the subscribers and publishers.

In both callback loops, the code makes the information printed on the terminal it is launched on. In comments the number code used by the referee box is shown, for the user to know the
 meaning of the number identifying the type of object or location. Then the scrip publishes the relevant data as standard strings for the youbot further data treatment. Finally the main loop declares all the components for ROS to interprete the node as a suscriber/publisher. Down below is the data got while listening to the topic that the inventory sender publishes.
![alt text](https://github.com/Youbotfontysatwork/youbot_fontys/blob/master/atwork_refbox_ros_client/source.png)
