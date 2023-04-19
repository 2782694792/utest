cmake_minimum_required(VERSION 3.0.0)
project(CMGCC7.3.0 VERSION 0.1.0)

set(CMAKE_C_COMPILER "gcc")
set(CMAKE_CXX_COMPILER "g++")
set(CMAKE_CXX_STANDARD 14)

set(UTEST ./utest)
include_directories(./include)
include_directories(${UTEST})
SET(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS} -O3 -Wall -fexec-charset=UTF8")
link_directories(./lib)
set(EXECUTABLE_OUTPUT_PATH  ${PROJECT_SOURCE_DIR})

aux_source_directory(${PROJECT_SOURCE_DIR}/src DIR_SRCS)
set(OUTPUT ${PROJECT_NAME}_main)
add_executable(${OUTPUT} ${DIR_SRCS} )

target_link_libraries(${OUTPUT} libgtest.a libgtest_main.a libgmock.a libgmock_main.a)
