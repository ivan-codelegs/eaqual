cmake_minimum_required( VERSION 3.18 )

project( EAQUALCommon )

if( ${CMAKE_BUILD_TYPE} STREQUAL "Debug" )
   set( STATIC_BUILD FALSE CACHE BOOL "" )
else()
   set( STATIC_BUILD TRUE CACHE BOOL "" )
endif()

add_subdirectory( cmake/lib )
