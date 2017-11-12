cmake_minimum_required(VERSION 2.8.3)
project(vision_pkg)


find_package(catkin REQUIRED COMPONENTS
  roscpp
  cv_bridge
  std_msgs
  actionlib 
  actionlib_msgs
)


find_package(Boost REQUIRED COMPONENTS system)
find_package( OpenCV REQUIRED )




catkin_package(
  CATKIN_DEPENDS roscpp std_msgs actionlib actionlib_msgs
)


include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${Boost_INCLUDE_DIRS}
)


add_executable(node_cam src/node_cam.cxx)


add_dependencies(node_cam vision_pkg_generate_messages_cxx)
add_dependencies(pub_node vision_pkg_generate_messages_cxx)


target_link_libraries(node_cam ${catkin_LIBRARIES})
include_directories(node_cam ${OpenCV_INCLUDE_DIRS})







