cmake_minimum_required(VERSION 3.0.0)

get_filename_component( basename ${CMAKE_CURRENT_SOURCE_DIR} NAME )
project( ${basename} LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(EXEC ${basename})

set( CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${OUTPUT_DIR} )
set( CMAKE_LIBRARY_OUTPUT_DIRECTORY ${OUTPUT_DIR} )
set( CMAKE_RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR} )

message( "Searching for glut/freeglut..." )
find_package( GLUT REQUIRED )
message( "Searching for glut/freeglut done." )
#if( glut_FOUND )
#    message( "glut found: ${glut_INCLUDE_DIR}" )
#endif( glut_FOUND )

include_directories(".")
add_executable( ${EXEC} main.cpp )

if (MSVC)
    set_target_properties(
        ${EXEC}
        PROPERTIES
            OUTPUT_NAME ${EXEC}
            SUFFIX ".exe"
    )
else()
    set_target_properties(
        ${EXEC}
        PROPERTIES
            OUTPUT_NAME ${EXEC}
            SUFFIX ".bin"
    )
endif()

set( DEPS
freeglut )

if( MSVC )
    target_link_libraries( ${EXEC} ${DEPS} )
else()
    target_link_libraries( ${EXEC} ${DEPS} )
endif()