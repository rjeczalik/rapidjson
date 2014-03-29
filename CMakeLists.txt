# Copyright (c) 2011 Milo Yip (miloyip@gmail.com)
# Copyright (c) 2013 Rafal Jeczalik (rjeczalik@gmail.com)
# Distributed under the MIT License (see license.txt file)

cmake_minimum_required(VERSION 2.8)
project(rapidjson CXX)

option(RAPIDJSON_BUILD_EXAMPLES "Build rapidjson examples." ON)
option(RAPIDJSON_BUILD_TESTS "Build rapidjson perftests and unittests." ON)
option(RAPIDJSON_USE_SSE2 "Configure rapidjson to use SSE2." OFF)
option(RAPIDJSON_USE_SSE42 "Conifgure rapidjson to use SSE4.2, overwrites SSE2." OFF)

set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib")
set(RAPIDJSON_INCLUDEDIR "${CMAKE_CURRENT_SOURCE_DIR}/include")

find_package(rapidjson REQUIRED)

include_directories(${RAPIDJSON_INCLUDE_DIRS})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${RAPIDJSON_CXX_FLAGS}")

if(RAPIDJSON_BUILD_EXAMPLES)
  add_subdirectory(example)
endif()

if(RAPIDJSON_BUILD_TESTS)
  add_subdirectory(test)
endif()

install(DIRECTORY include/rapidjson DESTINATION include)
