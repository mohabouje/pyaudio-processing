SET(HEADERS
        include/gain_control.h)

set(SOURCE
        src/analog_agc.h
        src/analog_agc.c
        src/digital_agc.h
        src/digital_agc.c)

add_library(webrtc-agc SHARED ${HEADERS} ${SOURCE})
target_include_directories(webrtc-agc PRIVATE src)
target_include_directories(webrtc-agc PUBLIC include)
target_link_libraries(webrtc-agc PRIVATE webrtc-dsp)
set_target_properties(webrtc-agc PROPERTIES PUBLIC_HEADER include/gain_control.h)

include(GNUInstallDirs)
install(TARGETS webrtc-agc
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/pyaudio-processing/")