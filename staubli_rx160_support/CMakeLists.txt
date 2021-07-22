cmake_minimum_required(VERSION 3.5)

project(staubli_rx160_support)

find_package(ament_cmake REQUIRED)


#if (BUILD_TESTING)
#  find_package(roslaunch REQUIRED)
#  roslaunch_add_file_check(tests/roslaunch_test.xml)
#endif()

foreach(dir config launch meshes urdf)
  install(
    DIRECTORY ${dir}/
    DESTINATION share/${PROJECT_NAME}/${dir})
endforeach()

ament_package()
