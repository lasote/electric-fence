PROJECT(efence)
cmake_minimum_required(VERSION 2.8)

set(CMAKE_C_FLAGS "-std=c99")
ADD_LIBRARY(efence CHANGES  COPYING  efence.c  tstheap.c)


