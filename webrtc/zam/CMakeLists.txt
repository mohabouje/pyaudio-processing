SET(HEADERS
        include/filters.h)

set(SOURCE
        src/filters.c)

add_library(webrtc-zam SHARED ${HEADERS} ${SOURCE})
target_include_directories(webrtc-zam PRIVATE src)
target_include_directories(webrtc-zam PUBLIC include)
set_target_properties(webrtc-zam PROPERTIES PUBLIC_HEADER include/filters.h)

include(GNUInstallDirs)
install(TARGETS webrtc-zam
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/pyaudio-processing/")