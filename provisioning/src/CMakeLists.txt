cmake_minimum_required(VERSION 2.8)
project(sqlite3)

# Set the source files
set(SOURCES source/sqlite3.c)

# Set the include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# Set the output directory
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)
set(OUTPUT_NAME sqlite3)

# Windows specific settings
if(WIN32)
    # Set the compiler flags
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /D_CRT_SECURE_NO_WARNINGS")

    # Set the type
    set(OUTPUT_TYPE SHARED)

    # Set the output directory
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)
endif()

# Linux specific settings
if(UNIX)
    # Set the compiler flags
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fPIC")

    # Set the type
    set(OUTPUT_TYPE MODULE)
endif()

# Create the library target
add_library(${OUTPUT_NAME} ${OUTPUT_TYPE} ${SOURCES})