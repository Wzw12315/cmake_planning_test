cmake_minimum_required(VERSION 3.31.3)    
project(planning)
set(CMAKE_CXX_STANDARD 11)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin) #动态库和exe都指定到bin文件目录下面
#CMAKE_RUNTIME_OUTPUT_DIRECTORY  windows平台
#CMAKE_LIBARY_OUTPUT_DIRECTORY  linux平台
#set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib) #静态库指定到lib文件目录下面

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)

add_library(common SHARED ${SRC_LISTS})

target_include_directories(common PUBLIC ${PROJECT_SOURCE_DIR}/include)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
add_executable(planning_main planning_main.cpp)

target_include_directories(planning_main PUBLIC ${PROJECT_SOURCE_DIR}/include)

target_link_libraries(planning_main PUBLIC common)