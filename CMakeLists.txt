cmake_minimum_required(VERSION 3.21)
project(mvm_tools)

set(CMAKE_C_STANDARD 11)

set(CMAKE_C_FLAGS "-Wall -Wextra -Wswitch-enum -Wmissing-prototypes -Wconversion -std=c11 -pedantic -fno-strict-aliasing ${CMAKE_C_FLAGS}")


add_executable(mvm src/mvm/mvm.c)
add_executable(masm src/masm/masm.c)
add_executable(demasm src/demasm/demasm.c)
