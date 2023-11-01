cmake_minimum_required(VERSION 3.0.2)
project(path_generator)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)


set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} -O2  -Wall")

find_package(OpenCV REQUIRED)

include_directories(
        /usr/include/eigen3
        ${OpenCV_INCLUDE_DIRS}
)
include_directories(include)
include_directories(/home/juchunyu/20231013/globalPlanner/AStar-ROS/include/path_generator)

###########
## Build ##
###########
#ADD_EXECUTABLE(test test.cpp)  
#include_directories(src)
# 找到src目录及其子目录下的所有c文件和h文件
#file(GLOB_RECURSE PROJECT_SOURCES "src/*.cpp" "src/*.c" "src/*.cc")
#file(GLOB_RECURSE PROJECT_HEADERS "src/*.hpp" "src/*.h" "src/*.hh")


add_executable(path_generation src/path_generator.cpp src/a_star.cpp)

target_link_libraries(
        path_generation
        -lboost_system -lboost_thread -lboost_graph
        ${OpenCV_LIBS}
        
)

