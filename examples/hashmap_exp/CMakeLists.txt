function(set_all_properties target)
    target_link_libraries(${target} PRIVATE Open3D)
    open3d_link_3rdparty_libraries(${target})
    open3d_show_and_abort_on_warning(${target})
    open3d_set_global_properties(${target})
    if (BUILD_CUDA_MODULE)
        target_include_directories(${target} SYSTEM PRIVATE
            ${CMAKE_CUDA_TOOLKIT_INCLUDE_DIRECTORIES}
        )
    endif()
endfunction()

add_executable(StdGPUDemo StdGPUDemo.cu)
set_all_properties(StdGPUDemo)
