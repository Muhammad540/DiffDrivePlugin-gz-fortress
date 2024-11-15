cmake_minimum_required(VERSION 3.10.2 FATAL_ERROR)

find_package(ignition-cmake2 REQUIRED)

project(DiffDriveNoise)

find_package(ignition-plugin1 REQUIRED COMPONENTS register)

set(IGN_PLUGIN_VER ${ignition-plugin1_VERSION_MAJOR})
include_directories(/usr/include/ignition/math6/ignition/math)
find_package(ignition-gazebo6 REQUIRED)
add_library(DiffDriveNoise SHARED DiffDriveNoise.cc)

set_property(TARGET DiffDriveNoise PROPERTY CXX_STANDARD 17)
target_link_libraries(DiffDriveNoise
  PRIVATE ignition-plugin${IGN_PLUGIN_VER}::ignition-plugin${IGN_PLUGIN_VER}
  PRIVATE ignition-gazebo6::ignition-gazebo6)
