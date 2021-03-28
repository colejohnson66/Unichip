cmake_minimum_required(VERSION 3.14)

# This MUST come before `project()`
# It will fail if the submodule is not downloaded
include(pico-sdk/pico_sdk_init.cmake)

project(unichip
    LANGUAGES C CXX ASM
)

# Update all submodules
include(cmake/InitGitSubmodules.cmake)

pico_sdk_init()

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(unichip
    src/main.cpp
)

target_include_directories(unichip
    PRIVATE include
)

target_link_libraries(unichip
    pico_stdlib
)

# Creates additional files besides only ELF
pico_add_extra_outputs(unichip)
