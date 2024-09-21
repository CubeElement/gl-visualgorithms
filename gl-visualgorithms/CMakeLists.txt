cmake_minimum_required(VERSION 3.2)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find and include GLEW
find_package(GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})

# Find and include GLFW
find_package(glfw3 3.3 REQUIRED)
include_directories(${GLFW_INCLUDE_DIRS})

# Find and include OpenGL
find_package(OpenGL REQUIRED)

# Add the main executable
add_executable(visualgorithms main.cpp)

# Link libraries to the executable
target_link_libraries(visualgorithms PRIVATE glfw OpenGL::GL GLEW::GLEW)

# Add subdirectory for glad
add_subdirectory(lib/glad)
target_link_libraries(visualgorithms PRIVATE glad ${CMAKE_DL_LIBS})
