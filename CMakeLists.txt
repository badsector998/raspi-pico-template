# Set minimun cmake
cmake_minimum_required(VERSION 3.13)

# Include build functions from Pico SDK
include($ENV{PICO_SDK_PATH}/external/pico_sdk_import.cmake)

# Set name of project (as PROJECT_NAME) and C/C++ standards

project(blink C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Create pico-sdk sub dir in our project for the libs
pico_sdk_init()

# Tell CMAKE where to find the executable source file
add_executable(blink blink.c)

# Create map/bin/hex/uf2 files
pico_add_extra_outputs(blink)

# Link to pico_stdlib (gpio, time, etc functions)
target_link_libraries(blink pico_stdlib)
