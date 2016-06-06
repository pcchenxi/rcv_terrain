cmake_minimum_required(VERSION 2.8.3)
project(terrain)

find_package(PCL 1.7 REQUIRED COMPONENTS)
find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  image_transport
  roscpp
  rospy
  sensor_msgs
  std_msgs
  tf
  pcl_ros
  laser_geometry
)


catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES terrain
#  CATKIN_DEPENDS roscpp rospy std_msgs
#  DEPENDS system_lib
)

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${PCL_INCLUDE_DIRS}
)

link_directories(
  ${PCL_LIBRARY_DIRS}
)

add_definitions(${PCL_DEFINITIONS})
include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(pointshape_based_processor src/pointshape_based_processor.cpp)

target_link_libraries(pointshape_based_processor
  ${OpenCV_LIBRARIES}
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
)





