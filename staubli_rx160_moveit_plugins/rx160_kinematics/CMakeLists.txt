
find_package(moveit_core REQUIRED)
find_package(moveit_kinematics REQUIRED)
find_package(pluginlib REQUIRED)
find_package(rclcpp REQUIRED)
find_package(tf2_kdl REQUIRED)
find_package(tf2_kdl REQUIRED)

include_directories(include)

if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

set(IKFAST_LIBRARY_NAME staubli_rx160_manipulator_moveit_ikfast_plugin)

add_library(${IKFAST_LIBRARY_NAME} src/staubli_rx160_manipulator_ikfast_moveit_plugin.cpp)

ament_target_dependencies(${IKFAST_LIBRARY_NAME} rclcpp)
ament_target_dependencies(${IKFAST_LIBRARY_NAME} moveit_core)
ament_target_dependencies(${IKFAST_LIBRARY_NAME} moveit_kinematics)
ament_target_dependencies(${IKFAST_LIBRARY_NAME} pluginlib)
ament_target_dependencies(${IKFAST_LIBRARY_NAME} tf2_kdl)
ament_target_dependencies(${IKFAST_LIBRARY_NAME} geometry_msgs)

ament_export_libraries(rclcpp REQUIRED)
ament_export_libraries(moveit_core REQUIRED)
ament_export_libraries(moveit_kinematics REQUIRED)
ament_export_libraries(pluginlib REQUIRED)
ament_export_libraries(tf2_kdl REQUIRED)
ament_export_libraries(geomtry_msgs REQUIRED)

target_link_libraries(${IKFAST_LIBRARY_NAME}
#  rclcpp
#  std_msgs
#  pluginlib
#  moveit_core
#  moveit_kinematics
#  geometry_msgs
  ${Boost_LIBRARIES}
  ${LAPACK_LIBRARIES})

pluginlib_export_plugin_description_file(${IKFAST_LIBRARY_NAME} staubli_rx160_manipulator_moveit_ikfast_plugin_description.xml)

install(
  TARGETS ${IKFAST_LIBRARY_NAME} 
  LIBRARY DESTINATION lib)

install(
  FILES staubli_rx160_manipulator_moveit_ikfast_plugin_description.xml 
  DESTINATION share/${PROJECT_NAME}/rx160_kinematics)
