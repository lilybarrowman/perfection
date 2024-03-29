cmake_minimum_required(VERSION 3.0.0)
project(perfection)
enable_language(CXX)
set(CMAKE_CXX_STANDARD 17)

set (CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

# Declare main executable
file(GLOB perfection_SOURCES src/*.cpp)
add_executable(perfection ${perfection_SOURCES})

# Compiler specific
if(CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
  # Hide Console
  #set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /SUBSYSTEM:WINDOWS /ENTRY:mainCRTStartup")
  set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /wd\"4307\"" )
endif()

# Interface libraries with main executable
target_include_directories(perfection PUBLIC src)
target_link_libraries(perfection)