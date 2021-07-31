cmake_minimum_required(VERSION 3.13)

include(../pico-sdk/pico_sdk_init.cmake)

project(ssd1322 VERSION 0.1.0 LANGUAGES C CXX ASM)

add_library(ssd1322 STATIC
    src/ssd1327.cpp
)

target_include_directories(ssd1322
    PUBLIC
        $<INSTALL_INTERFACE:include>
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/src
)

target_compile_options(ssd1322 PUBLIC -Wall)
#target_compile_features(ssd1322 PRIVATE cxx_std_17)

# Dependencies 

pico_sdk_init()

target_link_libraries(ssd1322 PUBLIC
    hardware_spi
    hardware_resets
    hardware_clocks
    hardware_gpio
    pico_stdlib
    )

# find_package(pico_sdk REQUIRED)
# find_package(hardware_spi REQUIRED)

# target_link_libraries(
#     PRIVATE
#         pico_sdk
# )

## rest not needed:
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# add_subdirectory(src)

