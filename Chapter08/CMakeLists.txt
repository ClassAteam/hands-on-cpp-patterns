cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

project(chapter08 LANGUAGES CXX)


set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

# set(CMAKE_PREFIX_PATH "home/benchmark/build/src")

find_library(benchmark benchmark)

add_executable(function_call function_call.C)

add_executable(visitor visitor.C)
add_executable(not_equal not_equal.C)
add_executable(registry registry.C)

target_link_libraries(function_call PRIVATE Threads::Threads benchmark)

target_compile_options(function_call
  PRIVATE
  "-g"
  "-O4"
  "-Wall"
  "-Wextra"
  "-Werror"
  "-pedantic"
  "--std=c++14")
