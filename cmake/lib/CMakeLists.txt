cmake_minimum_required( VERSION 3.18 )

project( EAQUAL )

if( ${STATIC_BUILD} )
   add_library( ${PROJECT_NAME} STATIC )
else()
   add_library( ${PROJECT_NAME} SHARED )
endif()

file( GLOB_RECURSE EAQUAL_HEADERS
   ../../src/libEAQUAL/*.h
   ../../src/GlobalHeaders/*.h
)

target_sources( ${PROJECT_NAME} PRIVATE
   ../../src/libEAQUAL/AvgBlock.cpp
   ../../src/libEAQUAL/AvgTime.cpp
   ../../src/libEAQUAL/CalcTables.cpp
   ../../src/libEAQUAL/FBModel.cpp
   ../../src/libEAQUAL/Fft.cpp
   ../../src/libEAQUAL/FFTModel.cpp
   ../../src/libEAQUAL/FileIO.cpp
   ../../src/libEAQUAL/KogModel.cpp
   ../../src/libEAQUAL/libEAQUAL.cpp
   ../../src/libEAQUAL/MOVBlock.cpp
   ../../src/libEAQUAL/PreProc.cpp
   ../../src/libEAQUAL/PsychoModel.cpp
   ../../src/libEAQUAL/RunAnalysis.cpp

   ${EAQUAL_HEADERS}
)

target_include_directories( ${PROJECT_NAME} PRIVATE
   ../../src/GlobalHeaders
)

set_target_properties( ${PROJECT_NAME} PROPERTIES
   CXX_STANDARD 17
)

if( OS_UNIX )
   target_compile_options( ${PROJECT_NAME} PRIVATE "-fvisibility=hidden" )
   target_link_options( ${PROJECT_NAME} PRIVATE "-fvisibility=hidden" )
endif()

if( ${STATIC_BUILD} )
   target_compile_definitions( ${PROJECT_NAME} PRIVATE -DSTATIC_EAQUAL )
   set_property( TARGET ${PROJECT_NAME} PROPERTY
      MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
   )
endif()
