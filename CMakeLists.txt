cmake_minimum_required(VERSION 3.11)

project(test CXX)
set(CMAKE_CXX_STANDARD 20)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

#set(Boost_INSTALL_DIR ${CONAN_BOOST_ROOT})
find_package(Boost 1.78.0 REQUIRED COMPONENTS)
if(Boost_FOUND)
  include_directories(${Boost_INCLUDE_DIRS})
  link_directories(${Boost_LIBRARY_DIRS})
endif()

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

add_executable(test src/main.cpp)

target_link_libraries(test PRIVATE Threads::Threads)
