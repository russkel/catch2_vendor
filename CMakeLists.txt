cmake_minimum_required(VERSION 3.5)

project(catch2_vendor)

find_package(ament_cmake REQUIRED)

macro(build_catch2)
  include(ExternalProject)

  externalproject_add(catch2
    URL https://github.com/catchorg/Catch2/archive/refs/tags/v2.13.9.tar.gz
    URL_HASH SHA256=06dbc7620e3b96c2b69d57bf337028bf245a211b3cddb843835bfe258f427a52
    BUILD_IN_SOURCE True
    DOWNLOAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}
    SOURCE_DIR source
    CONFIGURE_COMMAND ""
    BUILD_COMMAND ""
    INSTALL_COMMAND ""
  )

  install(
    DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/source/single_include/
    DESTINATION include
  )
endmacro()

build_catch2()

ament_export_include_directories(include)
# this ensures that the package has an environment hook setting the PATH
ament_package()
