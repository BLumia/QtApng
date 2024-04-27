cmake_minimum_required(VERSION 3.13)

file(GLOB ZLIB_SOURCE_FILES zlib/src/*.c)

file(GLOB LIBPNG_SOURCE_FILES libpng/src/*.c)
list(REMOVE_ITEM LIBPNG_SOURCE_FILES libpng/src/example.c)

add_library(vendored_libpng OBJECT ${ZLIB_SOURCE_FILES} ${LIBPNG_SOURCE_FILES})
target_include_directories(vendored_libpng
PUBLIC
    libpng/src
    zlib/src
)