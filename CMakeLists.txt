cmake_minimum_required(VERSION 3.14)

project(stb)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(DEBUG_COMPILE_FLAGS -g)
set(RELEASE_COMPILE_FLAGS -Ofast)

add_definitions(-DSTB_IMAGE_IMPLEMENTATION)

add_library(stb ${CMAKE_CURRENT_SOURCE_DIR}/stb_image.cpp)

if(DEFINE_DEBUG)
    target_compile_options(imgui PUBLIC ${DEBUG_COMPILE_FLAGS})
elseif(DEFINE_RELEASE)
    target_compile_options(imgui PUBLIC ${RELEASE_COMPILE_FLAGS})
endif()