cmake_minimum_required(VERSION 3.16)
set(CMAKE_C_COMPILER gcc)
project(ish VERSION 0.2 LANGUAGES C)

add_executable(ish src/main.c)
target_link_libraries(ish readline)

#install target
install(
	TARGETS ish
	DESTINATION /usr/local/bin
)

set(TARGET_ARCH ${CMAKE_HOST_SYSTEM_PROCESSOR})
if(NOT CPACK_GENERATOR)
       set(CPACK_GENERATOR "STGZ")
endif()
set(CPACK_PACKAGE_NAME "ish")
set(CPACK_PACKAGE_CONTACT "itainelken@gmail.com")
set(CPACK_PACKAGE_DESCRIPTION "A simple shell written in C")
set(CPACK_DEBIAN_PACKAGE_DEPENDS readline)
set(CPACK_VERSION_MAJOR ${CMAKE_PROJECT_VERSION_MAJOR})
set(CPACK_VERSION_MINOR ${CMAKE_PROJECT_VERSION_MINOR})
set(CPACK_VERSION_PATCH ${CMAKE_PROJECT_VERSION_PATCH})
set(CPACK_PACKAGE_VERSION ${CMAKE_PROJECT_VERSION})
set(CPACK_PACKAGE_FILE_NAME "${CPACK_PACKAGE_NAME}-${CPACK_PACKAGE_VERSION}_Linux-${TARGET_ARCH}")
include(CPack)
