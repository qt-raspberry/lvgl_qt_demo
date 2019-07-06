cmake_minimum_required(VERSION 2.8)

project(lvgl-sim)

file(GLOB_RECURSE LVGL_SRC lvgl/ *.c)
include_directories(lgvl)
add_library(lvgl ${LVGL_SRC})
add_executable(${PROJECT_NAME} "main.c")
