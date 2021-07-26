
find_package(rclcpp)
find_package(std_msgs)
#find_package(${Boost_LIBRARIES})
#find_package(${LAPACK_LIBRARIES})

include_directories(include)

set(IKFAST_LIBRARY_NAME staubli_rx160_manipulator_moveit_ikfast_plugin)

add_library(${IKFAST_LIBRARY_NAME} src/staubli_rx160_manipulator_ikfast_moveit_plugin.cpp)


target_link_libraries(${IKFAST_LIBRARY_NAME}
  rclcpp
  std_msgs
  ${Boost_LIBRARIES}
  ${LAPACK_LIBRARIES})

install(
  TARGETS ${IKFAST_LIBRARY_NAME} 
  LIBRARY DESTINATION lib)

install(
  FILES staubli_rx160_manipulator_moveit_ikfast_plugin_description.xml 
  DESTINATION share/${PROJECT_NAME}/rx160_kinematics)
