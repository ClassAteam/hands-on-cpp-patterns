
cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

project(chapter10 LANGUAGES CXX)

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

find_library(benchmark benchmark)
list(APPEND OPTIMIZATION_FLAGS "-g" "-O4" "-Wall" "-Wextra" "-Werror" "-pedantic" "--std=c++14")

add_executable(malloc1 malloc1.C)
add_executable(malloc2 malloc2.C)
add_executable(malloc3 malloc3.C)
add_executable(string1 string1.C)
add_executable(string2 string2.C)
add_executable(vector1 vector1.C)
add_executable(vector2 vector2.C)
add_executable(smartptr smartptr.C)

target_link_libraries(malloc1 PUBLIC Threads::Threads benchmark)
target_link_libraries(malloc2 PUBLIC Threads::Threads benchmark)
target_link_libraries(malloc3 PUBLIC Threads::Threads benchmark)
target_link_libraries(string1 PUBLIC Threads::Threads benchmark)
target_link_libraries(string2 PUBLIC Threads::Threads benchmark)
target_link_libraries(vector1 PUBLIC Threads::Threads benchmark)
target_link_libraries(vector2 PUBLIC Threads::Threads benchmark)
target_link_libraries(smartptr PUBLIC Threads::Threads benchmark)

target_compile_options(malloc1 PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(malloc2 PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(malloc3 PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(string1 PUBLIC "-g" "-O4" "--std=c++14")
target_compile_options(string2 PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(vector1 PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(vector2 PUBLIC ${OPTIMIZATION_FLAGS})
target_compile_options(smartptr PUBLIC ${OPTIMIZATION_FLAGS})
