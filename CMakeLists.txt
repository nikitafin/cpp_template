cmake_minimum_required(VERSION 3.20)

#
# Project details
#

project(
  "Project"
  VERSION 0.1.0
  LANGUAGES CXX)

#
# Set project options
#

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE "Debug")
endif()
message(STATUS "Started CMake for ${PROJECT_NAME} v${PROJECT_VERSION}...\n")

#
# Prevent building in the source directory
#

if(PROJECT_SOURCE_DIR STREQUAL PROJECT_BINARY_DIR)
  message(
    FATAL_ERROR
      "In-source builds not allowed. Please make a new directory (called a build directory) and run CMake from there.\n"
  )
endif()

set_target_properties(
  ${PROJECT_NAME}
  PROPERTIES ARCHIVE_OUTPUT_DIRECTORY
             "${CMAKE_BINARY_DIR}/lib/${CMAKE_BUILD_TYPE}"
             LIBRARY_OUTPUT_DIRECTORY
             "${CMAKE_BINARY_DIR}/lib/${CMAKE_BUILD_TYPE}"
             RUNTIME_OUTPUT_DIRECTORY
             "${CMAKE_BINARY_DIR}/bin/${CMAKE_BUILD_TYPE}")
#
# Enable Doxygen
#

include(cmake/Doxygen.cmake)
