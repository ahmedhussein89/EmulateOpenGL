# ${CMAKE_SOURCE_DIR}/CMakeLists.txt
cmake_minimum_required(VERSION 3.16)
project(
  EmulateOpenGL
  VERSION 0.1.0
  DESCRIPTION "Implement a software-rendering OpenGL backend."
  LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD          17)
set(CMAKE_CXX_EXTENSIONS        OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(renderer)

target_compile_options(
  renderer
  PRIVATE
  $<$<PLATFORM_ID:Linux>:
  -fno-exceptions
  -Wall
  >
  $<$<PLATFORM_ID:Window>:
  /EHs
  /Wall
  >
)

target_sources(
  renderer
  PRIVATE
  main.cpp
 "precompiled.hpp")

target_include_directories(
  renderer
  PRIVATE
  Source
)

target_precompile_headers(
  renderer
  PRIVATE
  ${CMAKE_SOURCE_DIR}/precompiled.hpp
)
