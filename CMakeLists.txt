cmake_minimum_required(VERSION 3.25)

# The DualSlide game SDK, from the DualSlide release this game is built for.
# The "local" preset uses a DualSlide checkout beside this repository instead,
# for working on the game and the SDK together.
set(DUALSLIDE_VERSION v1.0.0)

include(FetchContent)

FetchContent_Declare(DualSlide
    GIT_REPOSITORY https://github.com/uSolder/DualSlide.git
    GIT_TAG        ${DUALSLIDE_VERSION}
    GIT_SHALLOW    TRUE
    SOURCE_SUBDIR  software/sdk
)

FetchContent_MakeAvailable(DualSlide)

if(NOT CMAKE_TOOLCHAIN_FILE)
    set(CMAKE_TOOLCHAIN_FILE "${dualslide_SOURCE_DIR}/software/sdk/cmake/toolchain.cmake")
endif()

project(CanalTug LANGUAGES C)

include("${dualslide_SOURCE_DIR}/software/sdk/cmake/DualSlideGame.cmake")

file(GLOB GAME_SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_LIST_DIR}/src/*.c")

dualslide_add_game(canal_tug
    APP         CanalTug_App
    ID          dualslide.canal-tug
    NAME        "Canal Tug"
    VERSION     1.0.0
    AUTHOR      "Jack Herron"
    DESCRIPTION "Tow cargo along English countryside canals."
    SOURCES     ${GAME_SOURCES}
    INCLUDES    "${CMAKE_CURRENT_LIST_DIR}/inc"
)
