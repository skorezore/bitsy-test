cmake_minimum_required(VERSION 3.1.0)
project(bitsy-test)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU")
    set(CMAKE_CXX_FLAGS "-std=c++17 -Wall -Wextra -pedantic -static")
elseif("${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
    set(CMAKE_CXX_FLAGS "-std=c++1z -Wall -Wextra -pedantic -static")
endif()

file(GLOB_RECURSE bitsy-test_source ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp ${CMAKE_CURRENT_SOURCE_DIR}/include/bitsy-test/*.hpp)
add_executable(bitsy-test ${bitsy-test_source})

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/deps/bitsy)
target_link_libraries(bitsy-test bitsy)
