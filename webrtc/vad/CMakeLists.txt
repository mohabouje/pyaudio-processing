SET(HEADERS
        include/vad.h
        include/webrtc_vad.h)

set(SOURCE
        src/vad_core.h
        src/vad_core.c
        src/vad_filterbank.h
        src/vad_filterbank.c
        src/vad_gmm.h
        src/vad_gmm.c
        src/vad_sp.h
        src/vad_sp.c
        src/webrtc_vad.c)

add_library(webrtc-vad SHARED ${HEADERS} ${SOURCE})
target_include_directories(webrtc-vad PRIVATE src)
target_include_directories(webrtc-vad PUBLIC include)
target_link_libraries(webrtc-vad PRIVATE webrtc-dsp)
set_target_properties(webrtc-vad PROPERTIES PUBLIC_HEADER include/vad.h)

include(GNUInstallDirs)
install(TARGETS webrtc-aec
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/pyaudio-processing/")