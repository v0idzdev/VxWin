cmake_minimum_required(VERSION 3.25)

# Add sources
set(SOURCES
  util.cpp
  window_manager.cpp)

# Find headers
file(GLOB HEADERS CONFIGURE_DEPENDS ../include/*.hpp)

# Find external libraries
find_package(PkgConfig REQUIRED)
pkg_check_modules(X11 REQUIRED IMPORTED_TARGET "x11")
pkg_check_modules(GLOG REQUIRED IMPORTED_TARGET "libglog")

# Add internal library
add_library(vx_lib ${SOURCES} ${HEADERS})
target_include_directories(vx_lib PUBLIC ../include)
target_link_libraries(vx_lib PRIVATE PkgConfig::X11 PkgConfig::GLOG)#
target_compile_features(vx_lib PUBLIC cxx_std_17)

# For organisation in various IDEs
source_group(
  TREE "${PROJECT_SOURCE_DIR}/include"
  PREFIX "Header Files"
  FILES ${HEADERS}
)
