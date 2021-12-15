cmake_minimum_required(VERSION 3.5)

project(catch2_vendor)

find_package(ament_cmake REQUIRED)

macro(build_catch2)
  include(ExternalProject)

  externalproject_add(boost_ext_sml
    URL https://github.com/catchorg/Catch2/archive/refs/tags/v2.13.7.tar.gz
    URL_HASH SHA256=3cdb4138a072e4c0290034fe22d9f0a80d3bcfb8d7a8a5c49ad75d3a5da24fae
    BUILD_IN_SOURCE True
    DOWNLOAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}
    SOURCE_DIR source
    CONFIGURE_COMMAND ""
    BUILD_COMMAND ""
    INSTALL_COMMAND ""
  )

  install(
    DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/source/include/
    DESTINATION include/catch2/
  )
endmacro()

build_catch2()

ament_export_include_directories(include)
# this ensures that the package has an environment hook setting the PATH
ament_package()
