cmake_minimum_required(VERSION 3.0)

add_executable(sim osd_linux.c osd.h sim.c sim.h)

target_link_libraries(sim musashi)