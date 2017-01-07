cmake_minimum_required (VERSION 3.7.1 FATAL_ERROR)

# Only interpret if() arguments as variables or keywords when unquoted.
cmake_policy(SET CMP0054 NEW) 

# Project name and version
project(catch VERSION 1.5.9 LANGUAGES CXX)


# Library definition
set(CATCH_PUBLIC_HEADERS
    include/catch/catch.hpp
)

add_library(catch INTERFACE)
    
# Define headers for this library.
target_include_directories(catch INTERFACE
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

# Installation instructions
install(TARGETS catch EXPORT catchConfig 
    INCLUDES DESTINATION "include"
)

install(EXPORT catchConfig 
   DESTINATION "lib/cmake/catch")

install(FILES ${CATCH_PUBLIC_HEADERS} DESTINATION "include/catch")


