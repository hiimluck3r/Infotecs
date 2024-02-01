cmake_minimum_required(VERSION 2.8)
project(sqlite3)

# Установка версии SQLite, которую вы хотите собрать
set(SQLITE_VERSION 3260000)

# Определение исходных файлов SQLite
set(SQLITE_SOURCES
    source/sqlite3.c
)

# Определение заголовочных файлов SQLite
set(SQLITE_HEADERS
    include/sqlite3.h
    include/sqlite3ext.h
)

# Добавление библиотеки sqlite3
add_library(sqlite3 SHARED ${SQLITE_SOURCES} ${SQLITE_HEADERS})

# Определение вывода файла, включая расширения для разных операционных систем
set_target_properties(sqlite3 PROPERTIES
    OUTPUT_NAME "sqlite3"
    VERSION ${SQLITE_VERSION}
    SOVERSION ${SQLITE_VERSION}
)

# Установка определений для компилятора
target_compile_definitions(sqlite3 PRIVATE
    SQLITE_ENABLE_COLUMN_METADATA=1
    SQLITE_ENABLE_FTS3=1
    SQLITE_ENABLE_RTREE=1
    SQLITE_ENABLE_UNLOCK_NOTIFY
    SQLITE_THREADSAFE=1
    SQLITE_USE_URI=1
)

# Установка опций компиляции для разных компиляторов
if(WIN32)
    target_compile_options(sqlite3 PRIVATE /W4 /WX)
else()
    target_compile_options(sqlite3 PRIVATE -Wall -Wextra -pedantic -Werror)
endif()