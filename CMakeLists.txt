cmake_minimum_required (VERSION 3.7.1 FATAL_ERROR)

# Only interpret if() arguments as variables or keywords when unquoted.
cmake_policy(SET CMP0054 NEW) 

# Project name and version
project(catch VERSION 1.5.9 LANGUAGES CXX)


# Library definition
set(CATCH_PUBLIC_HEADERS
    include/catch/catch.hpp
)

add_library(catch INTERFACE
    ${CATCH_PUBLIC_HEADERS}
)
    
# Target C++14
set_property(TARGET leveldb PROPERTY CXX_STANDARD 14)


# Define headers for this library. PUBLIC headers are contained in 
# ``/include/${LIBRARY_NAME}`` are used for compiling the library, 
# and will be added to consumers' include paths. While PRIVATE 
# headers are only used to be 
target_include_directories(catch PRIVATE
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

target_include_directories(catch PUBLIC
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

# Installation instructions
install(TARGETS leveldb EXPORT catchConfig 
    LIBRARY DESTINATION "lib"
    ARCHIVE DESTINATION "lib"
    RUNTIME DESTINATION "bin"
    INCLUDES DESTINATION "include"
)

install(EXPORT catchConfig 
   DESTINATION "lib/cmake/catch")

install(FILES ${CATCH_PUBLIC_HEADERS} DESTINATION "include/catch")


