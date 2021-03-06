cmake_minimum_required(VERSION 2.8.9)
project(realsense_samples_time_sync)

#------------------------------------------------------------------------------------
#Include
include_directories(
    .
    ..
    include
    ${ROOT_DIR}/include/rs/core
)

#Source Files
set(SOURCE_FILES_BASE samples_time_sync_zr300.cpp samples_time_sync_impl.cpp
                      samples_time_sync_base.cpp
                      samples_time_sync_ds5.cpp
                      samples_time_sync_external_camera.cpp)

#Building Library
add_library(${PROJECT_NAME} ${SDK_LIB_TYPE}
    ${SOURCE_FILES_BASE}
)

#------------------------------------------------------------------------------------
#LINK_LIBRARIES
target_link_libraries(${PROJECT_NAME}
    realsense_log_utils
)

#------------------------------------------------------------------------------------
#Dependencies
add_dependencies(${PROJECT_NAME}
    realsense_log_utils
)

#------------------------------------------------------------------------------------
#Versioning
set_target_properties(${PROJECT_NAME} PROPERTIES VERSION "${LIBVERSION}" SOVERSION "${LIBSOVERSION}")

#------------------------------------------------------------------------------------
#Install
install(TARGETS ${PROJECT_NAME} DESTINATION lib)
