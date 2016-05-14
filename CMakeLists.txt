project(game.libretro.scummvm)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(kodi REQUIRED)
find_package(libretro-scummvm REQUIRED)

set(SCUMMVM_CUSTOM_BINARY ${SCUMMVM_LIB}
                          ${PROJECT_NAME}${CMAKE_SHARED_LIBRARY_SUFFIX})

build_addon(game.libretro.scummvm SCUMMVM "")
