#  Copyright (C) 2016 JDE Developers Team
#    Cmake template authors:
#      2016 Jan, Victor Arribas <v.arribas.urjc@gmail.com>
#  Authors:
#    put your name here

cmake_minimum_required(VERSION 2.8.4)

## PROJECT_NAME
# Define here your project name
project(skel_component)
# Sometimes output binary must have a custom name. Set it here:
set(binname ${PROJECT_NAME})


### Dependencies (@pre-job)
## use_package()
# You can use use_package for:
#   * JdeRobot libraries
#   * standard find_package() libraries

# JdeRobot + Ice deps
set(NOTFOUND_IS_ERROR 1)
use_package(JderobotInterfaces)
use_package(easyiceconfig)
use_package(ZeroCIce)

## custom dependencies
include_directories(
)
link_directories(
)
list(APPEND LIBRARIES
)


### Project
## Includes
# public headers MUST follow below standard:
#   include/
#     lib_project_name/
#       <your .h files or whatever additional directory>
# Example:
#   include/skel_component/skel_component.h
# Therefore, you can cleanly and safety include headers with
#   #include <skel_component/skel_component.h>
#
# Private headers can be placed under "source" tree and be referenced as:
#   #include "foo.h"
#   #include "../bar/bar.h"
include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/include
)
include(IDE_show_headers)

## Sources
# sources MUST be placed under "src/" directory
# in a flattened or tree structure
set(SOURCES

)

## Binary declaration
add_executable(${binname} ${SOURCES})
#add_library(${binname} SHARED ${SOURCES})

## Link libraries (@post-job)
target_link_libraries(${binname} ${LIBRARIES})


## Adding extras
# Tell compiler to show all possible warnings
set_target_properties(${binname} PROPERTIES COMPILE_FLAGS "-Wall -Wextra")


### Export package
# declare package to be used externally
#set(PROJECT_LIBRARIES
#	${binname}
#)
#declare_package(${PROJECT_NAME} ${PROJECT_LIBRARIES})