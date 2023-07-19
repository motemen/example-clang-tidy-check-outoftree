cmake_minimum_required(VERSION 3.0)
project(AwesomeFunctionNames VERSION 0.1.0)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Clang REQUIRED CONFIG)

add_library(AwesomeFunctionNames MODULE AwesomeFunctionNamesCheck.cpp)

set_target_properties(AwesomeFunctionNames PROPERTIES OUTPUT_NAME AwesomeFunctionNamesCheck_${LLVM_VERSION_MAJOR})

target_include_directories(AwesomeFunctionNames PRIVATE ${CLANG_INCLUDE_DIRS})

target_link_libraries(AwesomeFunctionNames PRIVATE
    clangTidy
    clangTidyUtils
)
