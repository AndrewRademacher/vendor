include(ExternalProject)
ExternalProject_Add(project_date
        URL https://github.com/HowardHinnant/date/archive/v2.4.1.tar.gz
        URL_HASH SHA256=98907d243397483bd7ad889bf6c66746db0d7d2a39cc9aacc041834c40b65b98
        PREFIX ${CMAKE_CURRENT_BINARY_DIR}/date
        CONFIGURE_COMMAND ""
        BUILD_COMMAND ""
        INSTALL_COMMAND ""
        )

ExternalProject_Get_Property(project_date SOURCE_DIR)

add_library(date INTERFACE)
add_dependencies(date project_date)
target_compile_definitions(date
        INTERFACE LIBRARY_HEADER_ONLY)
target_include_directories(date INTERFACE ${SOURCE_DIR}/include)