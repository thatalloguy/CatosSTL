cmake_minimum_required(VERSION 3.28)
project(CatosSTL)

set(CMAKE_CXX_STANDARD 17)

add_library(catos-stl INTERFACE)

file(GLOB_RECURSE CATOS_STL_SOURCE

    src/*.h
    src/*.cpp

)

add_library(catos-stl-static STATIC ${CATOS_STL_SOURCE})

add_executable(CatosSTL test.cpp ${CATOS_STL_SOURCE})

