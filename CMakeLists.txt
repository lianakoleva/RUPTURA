cmake_minimum_required(VERSION 3.14)

project(ruptura LANGUAGES CXX)

# Set the C++ standard to C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include directories
include_directories(src)

# Compiler flags
set(COMPILE_FLAGS
    /W4
    /permissive-
    /MP
    /MT
)
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

# Collect source files
set(SOURCES
    src/breakthrough.cpp
    src/component.cpp
    src/fitting.cpp
    src/inputreader.cpp
    src/isotherm.cpp
    src/mixture_prediction.cpp
    src/multi_site_isotherm.cpp
    src/random_numbers.cpp
    src/special_functions.cpp
)

# -------------------------------
# Build the ruptura executable
# -------------------------------
add_executable(ruptura src/main.cpp ${SOURCES})

target_compile_options(ruptura PRIVATE ${COMPILE_FLAGS})

# -------------------------------
# Doxygen Documentation
# -------------------------------
# add_subdirectory(docs)
