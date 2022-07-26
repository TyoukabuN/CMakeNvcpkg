cmake_minimum_required(VERSION 3.10)

add_subdirectory(Lib)

# set the project name
project(Ex002)

# add the executable
add_executable(Ex002 Main.cpp)

target_link_libraries(Ex002 PUBLIC Lib)