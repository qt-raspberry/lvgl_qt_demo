cmake_minimum_required(VERSION 2.8)

project(lvgl-sim)


file(GLOB_RECURSE LVGL_SRC "lvgl/*.c" )

include_directories(${CMAKE_SOURCE_DIR})

include_directories(lgvl)
add_library(lvgl ${LVGL_SRC})

file(GLOB_RECURSE LVGL_DVR_SRC "lv_drivers/*.c" )
add_library(lvgl_drv ${LVGL_DVR_SRC})

file(GLOB_RECURSE DEMO_SRC  "lv_examples/lv_apps/demo/*.[ch]")
#file(GLOB CONF_HEADERS "*.h")

#file(GLOB DEMO_SRC "*.h")

file(GLOB_RECURSE DEMO_SRC2  "lv_examples/lv_apps/benchmark/*.[ch]")
file(GLOB_RECURSE DEMO_SRC4  "lv_examples/lv_tests/lv_test_group/*.[ch]")
file(GLOB_RECURSE DEMO_SRC3  "lv_examples/lv_tests/lv_test_theme/*.[ch]")
file(GLOB_RECURSE DEMO_SRC5  "lv_examples/lv_tests/lv_test_objx/lv_test_imgbtn/*.[ch]")
#add_library(lvgl_con_inc ${LV_CONF_INCLUDE_SIMPLE})

include_directories(${LV_CONF_INCLUDE_SIMPLE})


#add_executable(demo  "main.c" ${CONF_HEADERS} ${DEMO_SRC})
add_executable(demo ${DEMO_SRC5} ${DEMO_SRC3} ${DEMO_SRC4} ${DEMO_SRC2} ${DEMO_SRC} "main.c" "lv_conf.h" "lv_ex_conf.h" "lv_drv_conf.h" "mouse_cursor_icon.c")


find_package(SDL2)
include_directories(${SDL2_INCLUDES})
target_link_libraries(demo  lvgl lvgl_drv ${SDL2_LIBRARIES})
