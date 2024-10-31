cmake_minimum_required(VERSION 3.10)
project(server)

set(CMAKE_TOOLCHAIN_FILE
	"/home/paul/client-server_labs/scripts/buildsystems/vcpkg.cmake" CACHE STRING "Vcpkg toolchain file")

set(CMAKE_PREFIX_PATH "${PROJECT_BINARY_DIR}/vcpkg_installed/x64-linux/share/libhv" CACHE STRING "Path to vcpkg installed packages")

find_package(libhv CONFIG REQUIRED)
get_cmake_property(all_targets GLOBAL PROPERTY TARGETS)

include_directories("vcpkg_installed/x64-linux/include/hv")

message(STATUS "Available targets: ${all_targets}")
add_executable(server src/server.cpp)
target_link_libraries(server PRIVATE hv_static)
