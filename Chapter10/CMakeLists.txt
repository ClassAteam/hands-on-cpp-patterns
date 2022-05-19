
cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

project(chapter10 LANGUAGES CXX)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

find_library(benchmark benchmark)
list(APPEND OPTIMIZATION_FLAGS "-g" "-O4" "-Wall" "-Wextra" "-Werror" "-pedantic" "--std=c++14")

add_executable(malloc1 malloc1.C)
add_executable(malloc2 malloc2.C)

target_link_libraries(malloc1 PRIVATE Threads::Threads benchmark)
target_link_libraries(malloc2 PRIVATE Threads::Threads benchmark)

target_compile_options(malloc1 PRIVATE ${OPTIMIZATION_FLAGS})
target_compile_options(malloc2 PRIVATE ${OPTIMIZATION_FLAGS})
