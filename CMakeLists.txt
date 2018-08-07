cmake_minimum_required(VERSION 3.9)
project(dwm)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_C_STANDARD 11)

set(X11_INCLUDE /usr/X11R6/include)
set(X11_LIBRARY /usr/X11R6/include)
set(FREETYPE_INCLUDE /usr/include/freetype2)

set(INCLUDE_DIR	${CMAKE_CURRENT_SOURCE_DIR}/include)
set(SOURCE_DIR		${CMAKE_CURRENT_SOURCE_DIR}/src)

set(SOURCES_LIST ${SOURCE_DIR}/util.c ${SOURCE_DIR}/drw.c ${SOURCE_DIR}/dwm.c)

add_executable(${PROJECT_NAME} ${SOURCES_LIST})

set(CMAKE_C_FLAGS "${CMAKE_CXX_FLAGS} -pedantic -Wall -Wno-deprecated-declarations")

target_include_directories(${PROJECT_NAME} PUBLIC ${INCLUDE_DIR} ${FREETYPE_INCLUDE} ${X11_INCLUDE})
target_compile_definitions(${PROJECT_NAME} PUBLIC _DEFAULT_SOURCE _BSD_SOURCE _POSIX_C_SOURCE=2 VERSION=6.1 XINERAMA)
target_link_libraries(${PROJECT_NAME} PUBLIC fontconfig Xft X11 Xinerama)
