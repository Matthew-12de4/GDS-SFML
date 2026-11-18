cmake_minimum_required(VERSION 3.23)
project("GDS++") # Projects Name
set(CMAKE_CXX_STANDARD 20) # Sets C++ version to 20

include(FetchContent)
FetchContent_Declare(SFML
        GIT_REPOSITORY https://github.com/SFML/SFML.git
        GIT_TAG 3.1.0
        GIT_SHALLOW ON
        EXCLUDE_FROM_ALL
        SYSTEM)
FetchContent_MakeAvailable(SFML)

set(SOURCES # Sets source path to a variable
        "main.cpp"
)

add_executable(${CMAKE_PROJECT_NAME} ${SOURCES}) # Links sources to the project

set_target_properties(${CMAKE_PROJECT_NAME} # Tidies the build folder
        PROPERTIES
        ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib
        LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib
        RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
)
target_link_libraries(${CMAKE_PROJECT_NAME} PRIVATE SFML::Graphics)