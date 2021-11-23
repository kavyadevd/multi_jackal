cmake_minimum_required(VERSION 2.8.3)
project(multi_jackal_tutorials)

find_package(catkin REQUIRED COMPONENTS roslaunch genmsg actionlib_msgs actionlib rospy std_msgs)
find_package(geometry_msgs)

add_action_files(DIRECTORY action FILES NavigateWaypoint.action InspectWaypoint.action ChargeJackal.action ChargeWarthog.action Wait.action)

catkin_python_setup()


generate_messages(DEPENDENCIES actionlib_msgs std_msgs geometry_msgs)

catkin_package()

roslaunch_add_file_check(launch/one_jackal.launch)
roslaunch_add_file_check(launch/two_jackal.launch)
roslaunch_add_file_check(launch/three_jackal.launch)
roslaunch_add_file_check(launch/jackal_with_gps.launch)

install(
	DIRECTORY launch rviz worlds
	DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
