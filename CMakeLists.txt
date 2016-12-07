cmake_minimum_required(VERSION 2.8)

project(dtoverlay)

if (NOT WIN32)
   add_definitions(-Wall -Werror)
endif ()

add_executable(dtoverlay dtoverlay_main.c utils.c)

target_link_libraries(dtoverlay dtovl efdt)

install(TARGETS dtoverlay RUNTIME DESTINATION bin)

add_custom_command(TARGET dtoverlay 
	POST_BUILD COMMAND ln;-sf;dtoverlay;dtparam)
install(FILES 
	${CMAKE_CURRENT_BINARY_DIR}/dtparam DESTINATION bin)
