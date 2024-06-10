cmake_minimum_required(VERSION 3.21)

project(gba-prog-intro LANGUAGES C)

if(NOT CMAKE_SYSTEM_NAME STREQUAL AdvancedGameBoy)
    message(FATAL_ERROR "System is not AdvancedGameBoy (got ${CMAKE_SYSTEM_NAME}). Did you remember to download gba-toolchain?")
endif()

add_executable(gba-prog-intro)

set(GBA_LIBS librom tonclib agbabi)
find_package(librom REQUIRED)
find_package(tonclib REQUIRED)
find_package(agbabi REQUIRED)

add_subdirectory(assets)
add_subdirectory(src)

target_compile_features(gba-prog-intro
	PRIVATE
		c_std_23
)
target_compile_options(gba-prog-intro PRIVATE -mthumb -fconserve-stack -fomit-frame-pointer)
target_link_libraries(gba-prog-intro PRIVATE ${GBA_LIBS} tilemap_assets)

set_target_properties(gba-prog-intro PROPERTIES
    ROM_TITLE "GBAProgIntro"
    ROM_ID AABE
    ROM_MAKER CD
    ROM_VERSION 1
)

install_rom(gba-prog-intro)
