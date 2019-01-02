cmake_minimum_required(VERSION 2.8.3)
project(uc2mono)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++11 -march=native -DEIGEN_DONT_PARALLELIZE")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O3 -Wall")

find_package(catkin REQUIRED COMPONENTS
    sensor_msgs
    cv_bridge
    roscpp
    std_msgs
    image_transport
    )

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

find_package(Eigen3  REQUIRED)
include_directories(
    ${catkin_INCLUDE_DIRS}
    ${EIGEN3_INCLUDE_DIR}
    )

catkin_package(
    )

add_executable(uc2mono
    src/main.cpp
    )

target_link_libraries(uc2mono
    ${catkin_LIBRARIES}
)
