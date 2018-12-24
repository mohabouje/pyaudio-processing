SET(HEADERS
        include/noise_suppression.h
        include/noise_suppression_x.h)

set(SOURCE
        src/defines.h
        src/noise_suppression.c
        src/noise_suppression_x.c
        src/ns_core.h
        src/ns_core.c
        src/nsx_core_c.c
        src/nsx_core.h
        src/nsx_core.c
        src/nsx_defines.h
        src/windows_private.h)

add_library(webrtc-ns SHARED ${HEADERS} ${SOURCE})
target_include_directories(webrtc-ns PRIVATE src)
target_include_directories(webrtc-ns PUBLIC include)
target_link_libraries(webrtc-ns PRIVATE webrtc-dsp)
set_target_properties(webrtc-ns PROPERTIES PUBLIC_HEADER include/noise_suppression.h)

include(GNUInstallDirs)
install(TARGETS webrtc-ns
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/pyaudio-processing/")