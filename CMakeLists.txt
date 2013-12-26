# Copyright (c) 2011 Milo Yip (miloyip@gmail.com)
# Copyright (c) 2013 Rafal Jeczalik (rjeczalik@gmail.com)
# Distributed under the MIT License (see license.txt file)

cmake_minimum_required(VERSION 2.8)
project(rapidjson)

option(RAPIDJSON_BUILD_EXAMPLES "Build rapidjson examples." ON)
option(RAPIDJSON_BUILD_TESTS "Build rapidjson perftests and unittests." ON)
option(RAPIDJSON_USE_SSE2 "Configure rapidjson to use SSE2." OFF)
option(
    RAPIDJSON_USE_SSE42
    "Conifgure rapidjson to use SSE4.2, overwrites SSE2."
    OFF
)

if(RAPIDJSON_USE_SSE42)
  add_definitions("-DRAPIDJSON_SSE42")
  if(MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /arch:SSE4.2")
  else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -msse4.2")
  endif()
else()
  if(RAPIDJSON_USE_SSE2)
    add_definitions("-DRAPIDJSON_SSE2")
    if(MSVC)
      set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /arch:SSE2")
    else()
      set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -msse2")
    endif()
  endif()
endif()

include_directories(${RAPIDJSON_INCLUDE_DIRS})

if(RAPIDJSON_BUILD_EXAMPLES)
  add_subdirectory(example)
endif()

if(RAPIDJSON_BUILD_TESTS)
  add_subdirectory(test)
endif()

install(DIRECTORY include/rapidjson DESTINATION include)
