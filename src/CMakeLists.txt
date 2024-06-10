set(GBA_PROG_INTRO_SOURCES
	main.c
)

set(GBA_PROG_INTRO_HEADERS
)

target_sources(gba-prog-intro
	PRIVATE
		${GBA_PROG_INTRO_SOURCES}
		${GBA_PROG_INTRO_HEADERS}
)

target_include_directories(gba-prog-intro
	PRIVATE
		${CMAKE_CURRENT_SOURCE_DIR}
		${CMAKE_BINARY_DIR}/assets
)
