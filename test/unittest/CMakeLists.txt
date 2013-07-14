# Copyright (c) 2011 Milo Yip (miloyip@gmail.com)
# Copyright (c) 2013 Rafal Jeczalik (rjeczalik@gmail.com)
# Distributed under the MIT License (see license.txt file)

add_subdirectory("${CMAKE_SOURCE_DIR}/thirdparty/gtest" "${CMAKE_BINARY_DIR}/gtest")

include("${CMAKE_SOURCE_DIR}/thirdparty/gtest/cmake/internal_utils.cmake")
fix_default_compiler_settings_()

include_directories("." "${CMAKE_SOURCE_DIR}/thirdparty/gtest/include")

set(
  TEST_SRC documenttest.cpp
           encodedstreamtest.cpp
           encodingstest.cpp
           filestreamtest.cpp
           jsoncheckertest.cpp
           readertest.cpp
           unittest.cpp
           valuetest.cpp
           writertest.cpp
)

add_executable(rapidjson_unittest ${TEST_SRC})
target_link_libraries(rapidjson_unittest gtest)

# It should be
#
#  include(<path to CMake Modules>/FindGTest.cmake)
#
# instead to get rid of gtest-not-found warning.

enable_testing()
find_package(GTest)
GTEST_ADD_TESTS(rapidjson_unittest "" ${TEST_SRC})
