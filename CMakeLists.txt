cmake_minimum_required(VERSION 3.0...3.25)
project(
  DawnTriangle
  VERSION 0.1.0
  LANGUAGES CXX C
)

add_executable(App ./src/main.cpp)

set_target_properties(App PROPERTIES
  CXX_STANDARD 20
  CXX_STANDARD_REQUIRED ON
  CXX_EXTENSIONS OFF
  COMPILE_WARNING_AS_ERROR ON
)

if(MSVC)
  target_compile_options(App PRIVATE /W4)
else()
  target_compile_options(App PRIVATE -Wall -Wextra -pedantic)
endif()

if(XCODE)
  set_target_properties(App PROPERTIES
    XCODE_GENERATE_SCHEME ON
    XCODE_SCHEME_ENABLE_GPU_FRAME_CAPTURE_MODE "Metal"
  )
endif()
