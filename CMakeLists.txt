cmake_minimum_required(VERSION 3.15)
project(dm_api_c VERSION 1.2.0 LANGUAGES C)

add_library(dm_api_c INTERFACE)
add_library(dm::api_c ALIAS dm_api_c)

target_include_directories(dm_api_c
    INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
        $<INSTALL_INTERFACE:include>
)

include(CMakePackageConfigHelpers)

write_basic_package_version_file(
    "${CMAKE_CURRENT_BINARY_DIR}/dm_api_cConfigVersion.cmake"
    VERSION ${PROJECT_VERSION}
    COMPATIBILITY SameMajorVersion
)

configure_package_config_file(
    "${CMAKE_CURRENT_SOURCE_DIR}/dm_api_cConfig.cmake.in"
    "${CMAKE_CURRENT_BINARY_DIR}/dm_api_cConfig.cmake"
    INSTALL_DESTINATION "lib/cmake/dm_api_c"
)

install(FILES dm_api.h DESTINATION include)

install(TARGETS dm_api_c EXPORT dm_api_cTargets)

install(
    EXPORT dm_api_cTargets
    FILE dm_api_cTargets.cmake
    NAMESPACE dm::
    DESTINATION lib/cmake/dm_api_c
)

install(
    FILES
        "${CMAKE_CURRENT_BINARY_DIR}/dm_api_cConfig.cmake"
        "${CMAKE_CURRENT_BINARY_DIR}/dm_api_cConfigVersion.cmake"
    DESTINATION lib/cmake/dm_api_c
)
