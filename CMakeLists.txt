cmake_minimum_required(VERSION 3.22)
project(rogue C CXX)
set(CMAKE_CXX_STANDARD 20)

# Halt on the first error
set(CMAKE_POLICY_CONFIGURE_EARLY_OUT_FOR_FATAL_ERRORS ON)

# System OpenGL
find_package(OpenGL REQUIRED)

# Local GLFW
add_subdirectory(glfw)

add_executable(rogue main.cc)
target_link_libraries(rogue ${OPENGL_LIBRARIES} glfw)
