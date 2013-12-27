# Copyright (c) 2011 Milo Yip (miloyip@gmail.com)
# Copyright (c) 2013 Rafal Jeczalik (rjeczalik@gmail.com)
# Distributed under the MIT License (see license.txt file)

find_package(GTest REQUIRED)
find_package(Threads REQUIRED)

include_directories("${GTEST_INCLUDE_DIRS}")

set(
    TEST_SRC
    documenttest.cpp
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
target_link_libraries(rapidjson_unittest ${GTEST_BOTH_LIBRARIES})
target_link_libraries(rapidjson_unittest ${CMAKE_THREAD_LIBS_INIT})

enable_testing()
add_test(RapidJSON rapidjson_unittest)
