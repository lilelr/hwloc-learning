cmake_minimum_required(VERSION 3.8)
project(hwloc_map)

set(CMAKE_CXX_STANDARD 11)
include(cmake/FindHwloc.cmake)
message(${Hwloc_LIBRARIES})
set(SOURCE_FILES main.cpp)
set(Hwloc_INCLUDE_DIRS "/usr/local/include/hwloc")
message(${Hwloc_INCLUDE_DIRS})
include_directories(${Hwloc_INCLUDE_DIRS})
add_executable(hwloc_map ${SOURCE_FILES})
target_link_libraries(hwloc_map ${Hwloc_LIBRARIES})

add_executable(hwloc_memory cpu_bind.c)
target_link_libraries(hwloc_memory ${Hwloc_LIBRARIES})

add_executable(hwloc_gpu gpu.cpp)
target_link_libraries(hwloc_gpu ${Hwloc_LIBRARIES})