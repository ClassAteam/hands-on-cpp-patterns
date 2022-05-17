cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

project(chapter09 LANGUAGES CXX)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

find_library(benchmark benchmark)

add_executable(city city.C)
add_executable(named_args named_args.C named_args_extra.C)
add_executable(poly_chain2 poly_chain2.C)
add_executable(poly_chain3 poly_chain3.C)
# add_executable(poly_chain1 poly_chain1.C)
add_executable(cout_chaining cout_chaining.C)

target_link_libraries(named_args PRIVATE Threads::Threads benchmark)

target_compile_options(named_args
  PRIVATE
  "-g"
  "-O4"
  "-Wall"
  "-Wextra"
  "-Werror"
  "-pedantic"
  "--std=c++14")
