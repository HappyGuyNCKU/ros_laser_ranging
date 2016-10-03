cmake_minimum_required(VERSION 2.8.3)
project(laser_ros CXX)

find_package(catkin REQUIRED
  roscpp
  std_msgs
)

catkin_package(
 INCLUDE_DIRS inc
 LIBRARIES lib
 CATKIN_DEPENDS roscpp
)

include_directories(inc/ ${catkin_INCLUDE_DIRS} )

add_executable(laser_ros_node src/measure.cpp)

FIND_LIBRARY(laser_ros_lib VL53L0X_Rasp lib)
target_link_libraries(laser_ros_node
  ${laser_ros_lib}
  ${catkin_LIBRARIES}
)
