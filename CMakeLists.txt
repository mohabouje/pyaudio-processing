cmake_minimum_required(VERSION 3.5)
project(pyaudio-processing)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)


option(COMPILE_AEC "If enabled, it will compile the AEC module" ON)
option(COMPILE_AGC "If enabled, it will compile the AGC module" ON)
option(COMPILE_NS "If enabled, it will compile the NS module" ON)
option(COMPILE_VAD "If enabled, it will compile the VAD module" ON)
option(COMPILE_ZAM "If enabled, it will compile the ZAM module" ON)

if (COMPILE_AEC)
    add_subdirectory(webrtc/aec)
endif(COMPILE_AEC)

if (COMPILE_AGC)
    add_subdirectory(webrtc/agc)
endif(COMPILE_AGC)

if (COMPILE_NS)
    add_subdirectory(webrtc/ns)
endif(COMPILE_NS)

if (COMPILE_VAD)
    add_subdirectory(webrtc/vad)
endif(COMPILE_VAD)

if (COMPILE_ZAM)
    add_subdirectory(webrtc/zam)
endif(COMPILE_ZAM)

add_subdirectory(webrtc/dsp)