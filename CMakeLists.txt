cmake_minimum_required(VERSION 3.9.0)
project(NVMAIN LANGUAGES CXX)


# disable in soure build
if ( ${CMAKE_SOURCE_DIR} STREQUAL ${CMAKE_BINARY_DIR}  )
        file(REMOVE test.txt)
        message( FATAL_ERROR "In-source builds not allowed. Please make a new
        directory (called a build directory) and run CMake from there. You may
        need to remove CMakeCache.txt."  )
endif()

file(GLOB_RECURSE nvmain_SRC
    "traceSim/traceMain.cpp"
    "include/*.cpp"
    "include/*.h"
    "src/*.cpp"
    "src/*.h"
    "Utils/*.cpp"
    "Utils/*.h"
    "SimInterface/NullInterface/*.cpp"
    "SimInterface/NullInterface/*.h"
    "Decoders/*.cpp"
    "Decoders/*.h"
    "DataEncoders/*.cpp"
    "DataEncoders/*.h"
    "Endurance/*.cpp"
    "Endurance/*.h"
    "traceReader/*.cpp"
    "traceReader/*.h"
    "traceWriter/*.cpp"
    "traceWriter/*.h"
    "Interconnect/*.cpp"
    "Interconnect/*.h"
    "Ranks/*.cpp"
    "Ranks/*.h"
    "Banks/*.cpp"
    "Banks/*.h"
    "NVM/*.cpp"
    "NVM/*.h"
    "Prefetchers/*.cpp"
    "Prefetchers/*.h"
    "MemControl/*.cpp"
    "MemControl/*.h"

    )

add_executable(nvmain ${nvmain_SRC})

target_include_directories(nvmain PRIVATE .)
target_compile_features(nvmain PRIVATE cxx_std_11)
