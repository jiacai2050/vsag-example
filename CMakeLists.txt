cmake_minimum_required(VERSION 3.11)

project (vsag-example)

set (CMAKE_CXX_STANDARD 11)

# download and compile vsag
include (FetchContent)
FetchContent_Declare (
  vsag
  GIT_REPOSITORY https://github.com/alipay/vsag
  GIT_TAG main
)
FetchContent_MakeAvailable (vsag)
include_directories (vsag-cmake-example PRIVATE ${vsag_SOURCE_DIR}/include)

# compile executable and link to vsag
add_executable (vsag-cmake-example src/main.cpp)
target_link_libraries (vsag-cmake-example PRIVATE vsag)

# add dependency
add_dependencies (vsag-cmake-example vsag)
