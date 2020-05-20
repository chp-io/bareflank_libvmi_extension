cmake_minimum_required(VERSION 3.6)
project(bareflank_libvmi_extension C CXX)

init_project(bareflank_libvmi_extension BINARY)

target_sources(bareflank_libvmi_extension PRIVATE exit_handler.cpp)
target_link_libraries(bareflank_libvmi_extension PUBLIC vmm::${VMI_BFVMM})

if("${VMI_BFVMM}" STREQUAL "boxy_bfvmm")
    target_compile_definitions(bareflank_libvmi_extension PUBLIC ENABLE_BOXY)
    target_include_directories(bareflank_libvmi_extension PUBLIC
        ${BOXY_SOURCE_BFSDK_DIR}/include
    )
endif()

fini_project()