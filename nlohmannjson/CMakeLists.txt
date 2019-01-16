cmake_minimum_required(VERSION 3.5.1)
project(nlohmannjson)

set(CMAKE_CXX_STANDARD 14)

include(ExternalProject)
ExternalProject_Add(project_nlohmannjson
        URL https://github.com/nlohmann/json/releases/download/v3.5.0/include.zip
        URL_HASH SHA256=3564da9c5b0cf2e032f97c69baedf10ddbc98030c337d0327a215ea72259ea21
        PREFIX ${CMAKE_CURRENT_BINARY_DIR}/nlohmanjson
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        )

ExternalProject_Get_Property(project_nlohmannjson SOURCE_DIR)

add_library(nlohmannjson INTERFACE)
add_dependencies(nlohmannjson project_nlohmannjson)
target_compile_definitions(nlohmannjson
        INTERFACE LIBRARY_HEADER_ONLY)
target_include_directories(nlohmannjson INTERFACE ${SOURCE_DIR})
