cmake_minimum_required(VERSION 3.5)
project(staubli_rx160_moveit_plugins)

find_package(moveit_core REQUIRED)
find_package(pluginlib REQUIRED)
find_package(rclcpp REQUIRED)
find_package(tf2_kdl REQUIRED)

# enable C++11 if needed for MoveIt on Kinetic
if ("${moveit_core_VERSION}" VERSION_GREATER "0.9.0")
  add_definitions(-std=c++11)
endif()

# include_directories(${catkin_INCLUDE_DIRS})

find_package(LAPACK REQUIRED)

ament_export_libraries(moveit_core REQUIRED)
ament_export_libraries(pluginlib REQUIRED)
ament_export_libraries(rclcpp REQUIRED)
ament_export_libraries(tf2_kdl REQUIRED)

add_subdirectory(rx160_kinematics)
