cmake_minimum_required(VERSION 3.0.0)
project(sic VERSION 0.1.0)

include(CTest)
enable_testing()

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -O2")
set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
set(src-dir "${PROJECT_SOURCE_DIR}/src")

# GL
find_package(glfw3 3.3 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})
link_libraries(${GLEW_LIBRARIES})

file(GLOB src-dir "${src-dir}/*.cpp")

add_executable(sic "${src-dir}")

# GL
target_link_libraries(sic glfw)
target_link_libraries(sic OpenGL::GL)
