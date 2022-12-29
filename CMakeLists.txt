cmake_minimum_required(VERSION 3.10)
project(Framework)
set(LIB_NAME Framework)
set(FRAMEWORK_SOURCE OpenGL)
# Force static library.
add_library(${LIB_NAME} STATIC src/Rendering/OpenGL/openglhelper.hpp)

add_subdirectory(src)

# Add include path.
target_include_directories(${LIB_NAME}
  PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/src
  PRIVATE
    ${RENDER_INCLUDE_PATH}
)

# Deprecated functions
# The following expressions are written for compatibility
# and will be removed in a future release.

# Add core include.
target_include_directories(${LIB_NAME}
  PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/Core/include
)
# Add definitions.
target_compile_definitions(${LIB_NAME}
  PRIVATE
    ${FRAMEWORK_DEFINITIOINS}
)
