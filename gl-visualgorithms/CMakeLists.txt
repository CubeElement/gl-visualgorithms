cmake_minimum_required(VERSION 3.2)

set( PROJECT_NAME visualgorithms )

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

#include_directories( ${CMAKE_CURRENT_SOURCE_DIR}/lib )

find_package(GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})
link_libraries(${GLEW_LIBRARIES})

find_package( glfw3 3.3 REQUIRED )
add_executable( ${PROJECT_NAME} main.cpp )
target_link_libraries( ${PROJECT_NAME} PRIVATE glfw )

find_package(OpenGL REQUIRED)
target_link_libraries( ${PROJECT_NAME} PRIVATE OpenGL::GL )

find_package ( GLEW REQUIRED )
target_link_libraries( ${PROJECT_NAME} PRIVATE GLEW::GLEW )


add_subdirectory( ${CMAKE_CURRENT_SOURCE_DIR}/lib/glad )
target_link_libraries( ${PROJECT_NAME} PRIVATE glad ${CMAKE_DL_LIBS} )
