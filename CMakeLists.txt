cmake_minimum_required(VERSION 3.22)
project(rogue C CXX)
set(CMAKE_CXX_STANDARD 20)

set(OpenGL_GL_PREFERENCE GLVND)
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

set(GLFW_BUILD_DOCS OFF CACHE BOOL "GLFW lib only")
set(GLFW_INSTALL OFF CACHE BOOL "GLFW lib only")
set(GLAD_GL "")

add_subdirectory(glfw)
include_directories("${GLFW_SOURCE_DIR}/deps")
set(GLAD_GL "${GLFW_SOURCE_DIR}/deps/glad/gl.h")

set(rogue-SRC main.cc)

add_executable(rogue ${rogue-SRC} ${GLAD_GL})
target_link_libraries(rogue ${OPENGL_LIBRARIES} glfw)
