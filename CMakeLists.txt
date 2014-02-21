project(gameclient.scummvm)

cmake_minimum_required(VERSION 2.6)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)

include(ExternalProject)

externalproject_add(scummvm
                    GIT_REPOSITORY https://github.com/libretro/scummvm
                    GIT_TAG 3229886
                    PREFIX scummvm
                    CONFIGURE_COMMAND ""
                    INSTALL_COMMAND ""
                    BUILD_COMMAND make -C backends/platform/libretro/build
                    BUILD_IN_SOURCE 1)

set(SCUMMVM_CUSTOM_BINARY ${PROJECT_BINARY_DIR}/scummvm/src/scummvm/backends/platform/libretro/build/scummvm_libretro${CMAKE_SHARED_LIBRARY_SUFFIX}
                        scummvm_libretro${CMAKE_SHARED_LIBRARY_SUFFIX} scummvm)

build_addon(gameclient.scummvm SCUMMVM DEPLIBS)
add_dependencies(gameclient.scummvm scummvm)
