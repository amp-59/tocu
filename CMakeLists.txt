cmake_minimum_required(FATAL_ERROR VERSION 3.10)

project(toc_updater C)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Debug)
endif()

add_executable(tocu main.c)

set(CMAKE_C_FLAGS_DEBUG -fsanitize=address)

target_compile_options(tocu PRIVATE
    -Wall
    -Wextra
    -Wpedantic
    -Wformat=2
    -Wuninitialized
    -Wstrict-overflow=5
    -Wstringop-overflow=4
    -Walloc-zero
    -Wshadow
    -Wwrite-strings
    -Wcast-qual
    -Wconversion
)

set_target_properties(tocu PROPERTIES
    C_EXTENSIONS OFF
    C_STANDARD 99
    C_STANDARD_REQUIRED ON
    LINK_FLAGS_RELEASE -s
)
