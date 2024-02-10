cmake_minimum_required(VERSION 3.15)
project(abby)

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

if (NOT DEFINED ABBY_TEST)
    SET(ABBY_TEST 1)
endif ()


set(ABBY_ROOT_DIR ${PROJECT_SOURCE_DIR})
set(ABBY_INCLUDE_DIR ${ABBY_ROOT_DIR}/include)
set(ABBY_LIB_TARGET abby)
set(ABBY_TEST_TARGET abby-test)

set(SOURCE_FILES
    include/abby.hpp)

add_library(${ABBY_LIB_TARGET} INTERFACE)

target_include_directories(${ABBY_LIB_TARGET} INTERFACE
    $<BUILD_INTERFACE:${ABBY_INCLUDE_DIR}>
    $<INSTALL_INTERFACE:include>)
    
if (${ABBY_TEST})
    add_subdirectory(test)
endif()
