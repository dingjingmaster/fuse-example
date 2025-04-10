cmake_minimum_required(VERSION 3.30)
project(fuse_example C)

set(CMAKE_C_STANDARD 11)

find_package(PkgConfig)

pkg_check_modules(FUSE fuse REQUIRED)
pkg_check_modules(FUSE3 fuse3 REQUIRED)

add_executable(fuse21-example fuse21.c)
target_link_libraries(fuse21-example PUBLIC ${FUSE_LIBRARIES})
target_include_directories(fuse21-example PUBLIC ${FUSE_INCLUDE_DIRS})
target_compile_definitions(fuse21-example PRIVATE -D_FILE_OFFSET_BITS=64)

add_executable(fuse25-example fuse25.c)
target_link_libraries(fuse25-example PUBLIC ${FUSE_LIBRARIES})
target_include_directories(fuse25-example PUBLIC ${FUSE_INCLUDE_DIRS})
target_compile_definitions(fuse25-example PRIVATE -D_FILE_OFFSET_BITS=64)

add_executable(fuse30-example fuse30.c)
target_link_libraries(fuse30-example PUBLIC ${FUSE3_LIBRARIES})
target_include_directories(fuse30-example PUBLIC ${FUSE3_INCLUDE_DIRS})
target_compile_definitions(fuse30-example PRIVATE -D_FILE_OFFSET_BITS=64)
