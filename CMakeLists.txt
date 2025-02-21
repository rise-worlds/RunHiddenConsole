cmake_minimum_required(VERSION 3.10)
project(RunHiddenConsole)

set(CMAKE_EXPORT_COMPILE_COMMANDS "ON")

if(CMAKE_CXX_STANDARD EQUAL 98 OR CMAKE_CXX_STANDARD LESS 14)
   message(FATAL_ERROR "app requires c++14 or newer")
elseif(NOT CMAKE_CXX_STANDARD)
   set(CMAKE_CXX_STANDARD 14)
   set(CMAKE_CXX_STANDARD_REQUIRED ON)
endif()

add_definitions(-D_CRT_SECURE_NO_WARNINGS)
add_executable(RunHiddenConsole RunHiddenConsole.cpp)

find_package(Git REQUIRED)

if(EXISTS ${CMAKE_SOURCE_DIR}/.git AND GIT_FOUND)
  configure_file(${CMAKE_CURRENT_SOURCE_DIR}/version.cmake.in ${CMAKE_CURRENT_BINARY_DIR}/version.cmake @ONLY)
  include("${CMAKE_CURRENT_BINARY_DIR}/version.cmake")
else()
  set(VERSION_STRING "Unknown")
  configure_file(${CMAKE_CURRENT_SOURCE_DIR}/version.cpp.in ${CMAKE_CURRENT_BINARY_DIR}/version.cpp @ONLY ESCAPE_QUOTES)
endif()

target_sources(RunHiddenConsole PRIVATE ${CMAKE_CURRENT_BINARY_DIR}/version.cpp)
