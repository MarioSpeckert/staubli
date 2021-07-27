cmake_minimum_required(VERSION 3.5)
project(staubli_rx160_moveit_plugins)

if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
add_subdirectory(rx160_kinematics)

ament_package()
