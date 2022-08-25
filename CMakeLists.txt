cmake_minimum_required(VERSION 3.14)
project(googletest)

set(CMAKE_CXX_STANDARD 20)

include(FetchContent)
FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG release-1.12.1
)
FetchContent_MakeAvailable(googletest)


enable_testing()

file(GLOB SOURCES ${CMAKE_CURRENT_LIST_DIR}/*.cpp)

add_executable(main ${SOURCES})

target_link_libraries(main GTest::gtest_main)

include(GoogleTest)
gtest_discover_tests(main)
