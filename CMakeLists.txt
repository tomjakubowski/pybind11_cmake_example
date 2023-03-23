cmake_minimum_required(VERSION 3.4...3.18)
project(cmake_example)

set(Boost_DEBUG ON)
find_package(Boost REQUIRED)
message("Boost include dirs :: ${Boost_INCLUDE_DIRS}")

add_subdirectory(pybind11)
pybind11_add_module(cmake_example src/main.cpp)

# EXAMPLE_VERSION_INFO is defined by setup.py and passed into the C++ code as a
# define (VERSION_INFO) here.
target_compile_definitions(cmake_example
                           PRIVATE VERSION_INFO=${EXAMPLE_VERSION_INFO})
