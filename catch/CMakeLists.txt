include(ExternalProject)
ExternalProject_Add(project_catch
        URL https://github.com/catchorg/Catch2/archive/v1.12.2.tar.gz
        URL_HASH SHA256=27bf01d20692e534a8963f96c6ca797df2b4ba6551db0379510c376558d75e3c
        PREFIX ${CMAKE_CURRENT_BINARY_DIR}/catch
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        )

ExternalProject_Get_Property(project_catch SOURCE_DIR)

add_library(catch INTERFACE)
add_dependencies(catch project_catch)
target_compile_definitions(catch
        INTERFACE LIBRARY_HEADER_ONLY)
target_include_directories(catch INTERFACE ${SOURCE_DIR}/include)