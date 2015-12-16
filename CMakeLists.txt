PROJECT(efence)
cmake_minimum_required(VERSION 2.8)

set(CMAKE_C_FLAGS "-std=c11")
ADD_LIBRARY(efence efence.c page.c print.c)

ADD_EXECUTABLE(tstheap tstheap.c)
TARGET_LINK_LIBRARIES(tstheap efence)

ADD_EXECUTABLE(eftest eftest.c)
TARGET_LINK_LIBRARIES(eftest efence)

IF(APPLE)
    target_compile_definitions(efence PUBLIC PAGE_PROTECTION_VIOLATED_SIGNAL=SIGBUS)
ENDIF()
