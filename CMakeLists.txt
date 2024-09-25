cmake_minimum_required(VERSION 3.29)
project(openglAdventure)

set(CMAKE_CXX_STANDARD 17)

# Add executable
add_executable(openglAdventure main.cpp)

# Add GLFW as a subdirectory
add_subdirectory(libs/glfw)

# Add GLAD as a library
add_library(glad libs/glad/src/glad.c)

# Ensure GLAD include directories are set correctly
target_include_directories(glad PUBLIC libs/glad/include)

# Include directories for GLFW and GLAD
target_include_directories(openglAdventure PUBLIC
        libs/glad/include
        libs/glfw/include
)

# Link GLFW, GLAD, and OpenGL libraries
find_package(OpenGL REQUIRED)
target_link_libraries(openglAdventure glfw glad OpenGL::GL)
