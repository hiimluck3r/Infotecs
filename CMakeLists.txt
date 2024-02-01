cmake_minimum_required(VERSION 3.8)

project(sqlite3)

set(SOURCES provisioning/src/*)

set(CMAKE_OUT ../lib)

add_library(sqlite SHARED ${SOURCES})

set_target_properties(sqlite PROPERTIES
    OUTPUT_NAME sqlite
    SUFFIX ".so"
)