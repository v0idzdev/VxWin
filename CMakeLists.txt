# Configure project
cmake_minimum_required(VERSION 3.25)
project(vx_win)
set(CMAKE_CXX_STANDARD 20)

# Add sources
add_subdirectory(src)
# target_sources(vx_win PRIVATE main.cpp)

# Link sources
add_executable(vx_win main.cpp)
target_compile_features(vx_win PRIVATE cxx_std_17)
target_link_libraries(vx_win PRIVATE vx_lib)