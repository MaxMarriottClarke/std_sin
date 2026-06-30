cmake_minimum_required(VERSION 3.14)
project(Exercises)

include(FetchContent)

set(BENCHMARK_ENABLE_TESTING OFF CACHE BOOL "" FORCE)
FetchContent_Declare(benchmark
  GIT_REPOSITORY https://github.com/google/benchmark.git
  GIT_TAG v1.9.1   # pin a release tag instead of `main` for reproducibility
  GIT_SHALLOW ON)
FetchContent_MakeAvailable(benchmark)

find_package(Threads REQUIRED)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 26)   # use 26 only if your compiler supports it
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS_RELEASE "-O2")

add_executable(sin_lut sin_lut.cpp)
target_link_libraries(sin_lut PRIVATE benchmark::benchmark_main Threads::Threads)
