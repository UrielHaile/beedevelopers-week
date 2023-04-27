cmake_minimum_required(VERSION 2.8)
project(opencv_example_project)

find_package(OpenCV 4 REQUIRED)
message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

set(CMAKE_EXPORT_COMPILE_COMMANDS ON )
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")

include_directories(${OpenCV_INCLUDE_DIRS})

add_executable(example ../src/example.cpp)
target_link_libraries(example ${OpenCV_LIBS})
