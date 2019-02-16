cmake_minimum_required(VERSION 3.12)
project(learn-APUE)

if (CMAKE_SYSTEM_NAME MATCHES "Linux")
    add_definitions(-DLINUX)
elseif (CMAKE_SYSTEM_NAME MATCHES "FreeBSD")
    add_definitions(-DBSD)
elseif (CMAKE_SYSTEM_NAME MATCHES "Darwin")
    add_definitions(-DMACOS)
elseif (CMAKE_SYSTEM_NAME MATCHES "SunOS")
    add_definitions(-DSOLARIS)
endif ()

add_subdirectory(lib)

include_directories(include)

add_executable(000_ls 000_ls.c)
add_executable(001_file_io 001_file_io.c)
add_executable(002_buffered_file_io 002_buffered_file_io.c)
target_link_libraries(000_ls apue)
target_link_libraries(001_file_io apue)
target_link_libraries(002_buffered_file_io apue)
