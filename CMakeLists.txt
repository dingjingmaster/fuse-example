cmake_minimum_required(VERSION 3.30)
project(fuse_example C)

set(CMAKE_C_STANDARD 11)

find_package(PkgConfig)

pkg_check_modules(FUSE fuse REQUIRED)

add_executable(fuse-example main.c)
target_link_libraries(fuse-example PUBLIC ${FUSE_LIBRARIES})
target_include_directories(fuse-example PUBLIC ${FUSE_INCLUDE_DIRS})
target_compile_definitions(fuse-example PRIVATE -D_FILE_OFFSET_BITS=64)
