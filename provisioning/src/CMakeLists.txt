cmake_minimum_required(VERSION 2.8)
project(sqlite3)

# Set the source files
set(SOURCES source/sqlite3.c)

# Set the include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)
set(OUTPUT_NAME sqlite3)

# Windows
if(WIN32)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} /D_CRT_SECURE_NO_WARNINGS")

    set(OUTPUT_TYPE SHARED)

    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/bin)
endif()

# Linux
if(UNIX)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -fPIC")

    set(OUTPUT_TYPE SHARED)
endif()

add_library(${OUTPUT_NAME} ${OUTPUT_TYPE} ${SOURCES})