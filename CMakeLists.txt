cmake_minimum_required(VERSION 3.0)
project(Musashi VERSION 3.4.1)

add_executable(m68kmake m68kmake.c)

add_custom_command(
    OUTPUT  m68kops.c m68kops.h
    COMMAND m68kmake ${CMAKE_CURRENT_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/m68k_in.c
    DEPENDS m68k_in.c
)

add_library(musashi
    m68kcpu.c
    m68kcpu.h
    m68kdasm.c
    ${CMAKE_CURRENT_BINARY_DIR}/m68kops.c
    ${CMAKE_CURRENT_BINARY_DIR}/m68kops.h
)

target_include_directories(musashi PUBLIC ${CMAKE_CURRENT_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR})
