cmake_minimum_required(VERSION 3.0)
project(SQLite)

# Set the source files
set(SOURCES sqlite3.c sqlite3.h shell.c sqlite3ext.h)

# Set the include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

# Set the output directory
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)

# Windows specific settings
if(WIN32)
    # Set the compiler flags
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /D_CRT_SECURE_NO_WARNINGS")

    # Set the output name and type
    set(OUTPUT_NAME sqlite3)
    set(OUTPUT_TYPE SHARED)

    # Set the output directory
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)
endif()

# Linux specific settings
if(UNIX)
    # Set the compiler flags
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fPIC")

    # Set the output name and type
    set(OUTPUT_NAME sqlite3)
    set(OUTPUT_TYPE MODULE)
endif()

# Create the library target
add_library(${OUTPUT_NAME} ${OUTPUT_TYPE} ${SOURCES})