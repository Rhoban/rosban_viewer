cmake_minimum_required(VERSION 2.8.3)
project(rosban_viewer)

find_package(catkin REQUIRED COMPONENTS Eigen)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
    
set(EXTRA_LIBS ${EXTRA_LIBS} 
  sfml-graphics
  sfml-window
  sfml-system
  GL
  GLU
  )

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES rosban_viewer ${EXTRA_LIBS}
  CATKIN_DEPENDS Eigen
)

###########
## Build ##
###########

# Specify additional locations of header files
# Your package locations should be listed before other locations
include_directories(
  include
  ${catkin_INCLUDE_DIRS} 
)

# Declare a C++ library
add_library(rosban_viewer
  src/rosban_viewer/color.cpp
  src/rosban_viewer/viewer.cpp
)

target_link_libraries(rosban_viewer ${catkin_LIBRARIES})