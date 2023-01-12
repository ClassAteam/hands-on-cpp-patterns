

cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

project(chapter10 LANGUAGES CXX)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

find_library(benchmark benchmark)
list(APPEND OPTIMIZATION_FLAGS "-g" "-O4" "-Wall" "-Wextra" "-Werror" "-pedantic" "--std=c++14")

add_executable(01_bad 01_bad.C)
add_executable(02a_trycatch_cleanup 02a_trycatch_cleanup.C)
add_executable(13_scopeguard_te 13_scopeguard_te.C)
add_executable(11a_scopeguard_on_exit_named 11a_scopeguard_on_exit_named.C)

target_link_libraries(01_bad PUBLIC Threads::Threads benchmark)
target_link_libraries(02a_trycatch_cleanup PUBLIC Threads::Threads benchmark)
target_link_libraries(13_scopeguard_te PUBLIC Threads::Threads benchmark)
target_link_libraries(11a_scopeguard_on_exit_named PUBLIC Threads::Threads benchmark)

target_compile_options(01_bad PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(02a_trycatch_cleanup PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(13_scopeguard_te PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(11a_scopeguard_on_exit_named PUBLIC ${OPTIMIZATION_FLAGS})
