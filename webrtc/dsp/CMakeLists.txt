SET(HEADERS
        include/signal_processing_library.h
        include/stack_alloc.h
        include/spl_inl.h
        include/delay_estimator.h
        include/fft4g.h
        include/real_fft.h
        include/ring_buffer.h
        include/speex_resampler.h
        include/arch.h
        include/delay_estimator_wrapper.h)

set(SOURCE
        src/complex_fft.c
        src/complex_bit_reverse.c
        src/complex_fft_tables.h
        src/copy_set_operations.c
        src/cross_correlation.c
        src/delay_estimator.c
        src/delay_estimator_internal.h
        src/delay_estimator_wrapper.c
        src/division_operations.c
        src/dot_product_with_scale.c
        src/downsample_fast.c
        src/energy.c
        src/fft4g.c
        src/float_util.c
        src/get_scaling_square.c
        src/high_pass_filter.c
        src/min_max_operations.c
        src/randomization_functions.c
        src/real_fft.c
        src/resample_48khz.c
        src/resample_by_2.c
        src/resample_by_2_internal.h
        src/resample_by_2_internal.c
        src/resample_fractional.c
        src/resample_sse.h
        src/ring_buffer.c
        src/speex_resampler.c
        src/spl_init.c
        src/spl_sqrt.c
        src/spl_sqrt_floor.c
        src/splitting_filter.c
        src/vector_scaling_operations.c)

add_library(webrtc-dsp SHARED ${HEADERS} ${SOURCE})
target_include_directories(webrtc-dsp PRIVATE src)
target_include_directories(webrtc-dsp PUBLIC include)
set_target_properties(webrtc-dsp PROPERTIES PUBLIC_HEADER include/signal_processing_library.h)

include(GNUInstallDirs)
install(TARGETS webrtc-aec
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/pyaudio-processing/")