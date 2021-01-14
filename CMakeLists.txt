cmake_minimum_required(VERSION 3.0.0)

project( freeglut_test_proj )

if (MSVC)
    set( OUTPUT_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Build-Windows )
else()
    set( OUTPUT_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Build-Linux )
endif()

add_subdirectory( deps/freeglut-3.2.1 )
add_subdirectory( testApp )