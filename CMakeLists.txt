cmake_minimum_required(VERSION 3.9)
project(opencv_example_project)

find_package(GTest)
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

enable_testing()

add_executable(
  test-example
  ../tests/test-example.cpp
)
target_link_libraries(
  test-example
  GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(test-example)

