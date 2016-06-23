cmake_minimum_required(VERSION 2.8.3)
project(cwru_action)

find_package(catkin REQUIRED COMPONENTS
	roscpp
	std_msgs
	actionlib
	actionlib_msgs
	geometry_msgs
	trajectory_msgs
	message_generation
)


## System dependencies are found with CMake's conventions
find_package(Boost REQUIRED COMPONENTS system)

## Generate actions in the 'action' folder
add_action_files(DIRECTORY action
	FILES
	cart_move.action
	cwru_baxter_cart_move.action
	merry_get_can.action
	traj.action
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  std_msgs  
  geometry_msgs
  trajectory_msgs
  actionlib_msgs
)

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
catkin_package(
CATKIN_DEPENDS message_runtime
#  INCLUDE_DIRS include
#  LIBRARIES cwru_srv
  CATKIN_DEPENDS actionlib_msgs actionlib geometry_msgs std_msgs trajectory_msgs
  DEPENDS system_lib 
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
# include_directories(include)
include_directories(
  ${catkin_INCLUDE_DIRS}
)

## Add cmake target dependencies of the executable/library
## as an example, message headers may need to be generated before nodes
# add_dependencies(cwru_msgs_node cwru_msgs_generate_messages_cpp)
add_dependencies(${p} ${catkin_EXPORTED_TARGETS} ${PROJECT_NAME}_generate_messages_cpp)
#cs_install()
#cs_export()
    
