
# set minimum cmake version
cmake_minimum_required(VERSION 3.9 FATAL_ERROR)

# project name and language
project(recipe-06 LANGUAGES CXX)

add_executable(list-swap list_swap.C)
add_executable(nonmember_swap_friend.C nonmember_swap_friend)
