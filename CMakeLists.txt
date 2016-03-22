PROJECT(efence)
cmake_minimum_required(VERSION 2.8)


ADD_LIBRARY(efence efence.c page.c print.c)
TARGET_LINK_LIBRARIES(efence pthread)


ADD_EXECUTABLE(tstheap tstheap.c)
TARGET_LINK_LIBRARIES(tstheap efence)

ADD_EXECUTABLE(eftest eftest.c)
TARGET_LINK_LIBRARIES(eftest efence)

IF(APPLE)
    target_compile_definitions(efence PUBLIC PAGE_PROTECTION_VIOLATED_SIGNAL=SIGBUS)
ENDIF()

