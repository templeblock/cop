cmake_minimum_required(VERSION 2.8 FATAL_ERROR)

if (NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message(STATUS "Setting CMAKE_BUILD_TYPE type to 'Release' as none was specified.")
  set(CMAKE_BUILD_TYPE Release CACHE STRING "Choose the type of build." FORCE)

  # Set the possible values of build type for cmake-gui
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release")
endif()

project(app_cop_vec_test)

if (NOT WIN32)
  set(CMAKE_C_FLAGS_DEBUG "-Wall -O0 -g -fsanitize=address")
  set(CMAKE_C_FLAGS_RELEASE "-Wall -DNDEBUG=1 -O3 -g")
endif (NOT WIN32)

add_executable(cop_vec_test cop_vec_test.c)
target_include_directories(cop_vec_test PUBLIC "../..")
add_subdirectory("../../cop" "${CMAKE_CURRENT_BINARY_DIR}/cop_dep")
