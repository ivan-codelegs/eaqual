cmake_minimum_required( VERSION 3.18 )

project( EAQUALCommon )

set( CMAKE_INCLUDE_CURRENT_DIR ON )
set( CMAKE_BINARY_DIR "${CMAKE_BINARY_DIR}/bin" )
set( EXECUTABLE_OUTPUT_PATH "${CMAKE_BINARY_DIR}" )
set( LIBRARY_OUTPUT_PATH "${CMAKE_BINARY_DIR}" )

if( ${CMAKE_BUILD_TYPE} STREQUAL "Debug" )
   set( STATIC_BUILD FALSE CACHE BOOL "" )
else()
   set( STATIC_BUILD TRUE CACHE BOOL "" )
endif()

add_subdirectory( cmake/lib )
