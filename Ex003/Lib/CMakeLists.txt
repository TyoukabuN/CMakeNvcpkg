cmake_minimum_required(VERSION 3.10)

project(Lib)

# set(search_src_include src/tmath.cpp include/tmath.h)
# add_library(Lib ${search_src_include})

# file(GLOB_RECURSE search_src_include 
# "src/*.cpp" 
# "include/*.h")
# add_library(Lib "${search_src_include}")

# message("---------------------------------------------------------")
# message( ${CMAKE_CURRENT_SOURCE_DIR})
# message( ${PROJECT_SOURCE_DIR})
# message("---------------------------------------------------------")

file(GLOB_RECURSE search_src_include 
"src/*.cpp" 
"include/*.h")
foreach(FILE ${search_src_include})
    get_filename_component(PARENT_DIR "${FILE}" PATH)
    file(RELATIVE_PATH PARENT_DIR ${CMAKE_CURRENT_SOURCE_DIR} ${PARENT_DIR})
    string(REPLACE "/" "\\" GROUP "${PARENT_DIR}")
    set(GROUP "${GROUP}")
    source_group("${GROUP}" FILES "${FILE}")
endforeach()

add_library(Lib ${search_src_include})

# PUBLIC 会帮link到这个lib的project设置include_directories
target_include_directories(Lib PUBLIC 
"${CMAKE_CURRENT_SOURCE_DIR}"
"${CMAKE_CURRENT_SOURCE_DIR}/include"
)