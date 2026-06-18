if(NOT DEFINED NMBS_LIB_MODE)
    set(NMBS_LIB_MODE "${ACLASS_LIB_MODE}")
endif()

add_library(nanomodbus ${NMBS_LIB_MODE}
    nanomodbus.c
)

target_include_directories(nanomodbus PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
)

target_compile_definitions(nanomodbus PRIVATE
    NMBS_SERVER_DISABLED
)

set_target_properties(nanomodbus PROPERTIES
    C_VISIBILITY_PRESET hidden
)

install(TARGETS nanomodbus
    LIBRARY   DESTINATION lib
    ARCHIVE   DESTINATION lib
    FILE_SET HEADERS DESTINATION include
)
