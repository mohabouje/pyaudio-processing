SET(HEADERS
        include/echo_cancellation.h)

set(SOURCE
        src/aec_common.h
        src/aec_core.h
        src/aec_core.c
        src/aec_core_internal.h
        src/aec_core_sse2.c
        src/aec_rdft.h
        src/aec_rdft.c
        src/aec_rdft_sse2.c
        src/aec_resampler.h
        src/aec_resampler.c
        src/echo_cancellation.c
        src/echo_cancellation_internal.h)

add_library(webrtc-aec SHARED ${HEADERS} ${SOURCE})
target_include_directories(webrtc-aec PRIVATE src)
target_include_directories(webrtc-aec PUBLIC include)
target_link_libraries(webrtc-aec PRIVATE webrtc-dsp)
set_target_properties(webrtc-aec PROPERTIES PUBLIC_HEADER include/echo_cancellation.h)

include(GNUInstallDirs)
install(TARGETS webrtc-aec
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/pyaudio-processing/")