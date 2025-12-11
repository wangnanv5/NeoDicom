cmake_minimum_required(VERSION 3.18)
project(nnUNet CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CUDA_FLAGS "${CMAKE_CUDA_FLAGS} --allow-unsupported-compiler")

if(MSVC)
    add_compile_options("/utf-8")
endif()

find_package(ITK REQUIRED)
include(${ITK_USE_FILE})


set(SOURCES
)
 
set(HEADERS
)

add_executable(NeoDicom main.cpp ${SOURCES} ${HEADERS})