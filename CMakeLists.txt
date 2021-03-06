cmake_minimum_required(VERSION 3.0.2)
project(ros_service)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  message_runtime
  roscpp
  rospy
)

## Generate services in the 'srv' folder
add_service_files(
  FILES
  Service.srv
)

## Generate added messages and services with any dependencies listed here
generate_messages(
#   DEPENDENCIES
#   std_msgs  # Or other packages containing msgs
)

catkin_package(
  INCLUDE_DIRS include
#  LIBRARIES ros_service
#  CATKIN_DEPENDS message_generation message_runtime roscpp rospy
#  DEPENDS system_lib
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(ros_service_node
  src/ros_service.cpp
  src/ros_service_node.cpp
)
add_dependencies(ros_service_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(ros_service_node ${catkin_LIBRARIES})

add_executable(ros_service_client_node
  src/ros_service_client.cpp
  src/ros_service_client_node.cpp
)
add_dependencies(ros_service_client_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(ros_service_client_node ${catkin_LIBRARIES})

add_executable(ros_service_alt_node
  src/ros_service_alt.cpp
  src/ros_service_alt_node.cpp
)
add_dependencies(ros_service_alt_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(ros_service_alt_node ${catkin_LIBRARIES})
