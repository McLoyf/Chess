cmake_minimum_required(VERSION 3.10.0)
project(Chess VERSION 0.1.0 LANGUAGES C CXX)
cmake_policy(SET CMP0072 NEW)

find_package(OpenGL REQUIRED)

add_executable(Chess 
    src/main.cpp 
    src/glad.c
)
target_include_directories(Chess PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/glad/include)

include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

target_link_libraries(Chess 
    glfw
    OpenGL::GL
)
