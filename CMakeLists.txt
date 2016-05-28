# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(ikfast_pr2)
# Load catkin and all dependencies required for this package
# TODO: remove all from COMPONENTS that are not catkin packages.
find_package(catkin REQUIRED COMPONENTS orocos_kdl angles roscpp)
find_package(Boost REQUIRED COMPONENTS thread)

#uncomment if you have defined messages
#add_message_files(
  FILES
  # TODO: List your msg files here
)
#uncomment if you have defined services
#add_service_files(
  FILES
  # TODO: List your msg files here
)
## Generate added messages and services with any dependencies listed here
generate_messages(
    #TODO DEPENDENCIES geometry_msgs std_msgs
)

# catkin_package parameters: http://ros.org/doc/groovy/api/catkin/html/dev_guide/generated_cmake_api.html#catkin-package
# TODO: fill in what other packages will need to use this package
catkin_package(
    DEPENDS kdl angles roscpp
    CATKIN_DEPENDS # TODO
    INCLUDE_DIRS # TODO include
    LIBRARIES # TODO
)
# include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})
# CATKIN_MIGRATION: removed during catkin migration
# cmake_minimum_required(VERSION 2.4.6)

# CATKIN_MIGRATION: removed during catkin migration
# include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
set(ROS_BUILD_TYPE Release)

add_definitions(-DIKFAST_NO_MAIN=1)

#add_definitions(-DUSE_HARD_JOINT_LIMITS=1)
add_definitions(-DUSE_SOFT_JOINT_LIMITS=1)

# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_init()

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#common commands for building c++ executables and libraries
add_library(${PROJECT_NAME} src/ikfast61.Transform6D.27_28_30_31_32_33_f29.cpp
                                     src/ikfast61.Transform6D.15_16_18_19_20_21_f17.cpp
                                     src/ik_interface.cpp)
#target_link_libraries(${PROJECT_NAME} another_library)

# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_add_boost_directories()
include_directories(${Boost_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES})

#add_executable(testarm src/armtest.cpp src/arm.cpp)
#target_link_libraries(testarm ${PROJECT_NAME})
#add_executable(testIK src/test.cpp)
#target_link_libraries(testIK ${PROJECT_NAME})
#add_executable(computeIK src/computeIK.cpp)
#target_link_libraries(computeIK ${PROJECT_NAME})
#

