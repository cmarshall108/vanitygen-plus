list(APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake)

cmake_minimum_required(VERSION 3.8)
project(vanitygen)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Debug)
endif()

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS OFF)

set(CMAKE_C_FLAGS "-Wall -Wno-unused-variable")
set(CMAKE_C_FLAGS_DEBUG "-g")
set(CMAKE_C_FLAGS_RELEASE "-O3")

find_package(Threads QUIET)
if(NOT Threads_FOUND)
  message(FATAL_ERROR "Failed to find pthreads dependency!")
endif()

find_package(OpenSSL QUIET)
if(NOT OpenSSL_FOUND)
  message(FATAL_ERROR "Failed to find openssl dependency!")
endif()

find_package(PCRE QUIET)
if(NOT PCRE_FOUND)
  message(FATAL_ERROR "Failed to find pcre dependency!")
endif()

include_directories(${OPENSSL_INCLUDE_DIR})
include_directories(${PCRE_INCLUDE_DIR})

add_subdirectory(src)
