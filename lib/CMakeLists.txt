cmake_minimum_required(VERSION 3.12)
project(apue C)

set(CMAKE_C_STANDARD 99)

file(GLOB APUE_SRC "*.c")

include_directories(../include)
add_library(apue ${APUE_SRC})