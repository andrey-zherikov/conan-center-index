cmake_minimum_required(VERSION 3.15)
project(semver.c LANGUAGES C)

include(GNUInstallDirs)

add_library(semver.c ${SEMVER_C_SRC_DIR}/semver.c)
set_target_properties(semver.c PROPERTIES
    PUBLIC_HEADER ${SEMVER_C_SRC_DIR}/semver.h
    WINDOWS_EXPORT_ALL_SYMBOLS ON
)

install(TARGETS semver.c
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)
