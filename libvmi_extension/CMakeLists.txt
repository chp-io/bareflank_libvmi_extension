cmake_minimum_required(VERSION 3.6)

if(ENABLE_BUILD_VMM)
    set(VMI_BFVMM bfvmm CACHE STRING "The hypervisor libvmi extends")

    if(DEFINED BOXY_SOURCE_BFVMM_DIR)
        set(VMI_BFVMM boxy_bfvmm)
    endif()

    add_subproject(bareflank_libvmi_extension vmm
        DEPENDS ${VMI_BFVMM}
        SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/exit_handler
    )
endif()