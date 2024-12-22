cmake_minimum_required(VERSION 3.15.7)
project(
        myproject
        VERSION 0.0.1
        LANGUAGES CXX C)
add_subdirectory(src)
OPTION(BUILD_TESTS "enable tests" OFF)
IF (BUILD_TESTS)
    enable_testing()
    add_subdirectory(test)
ENDIF (BUILD_TESTS)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
add_custom_target(copy_compile_commands_json ALL
                  DEPENDS ${CMAKE_SOURCE_DIR}/compile_commands.json)

add_custom_command(
  DEPENDS ${CMAKE_BINARY_DIR}/compile_commands.json
  OUTPUT ${CMAKE_SOURCE_DIR}/compile_commands.json
  COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_BINARY_DIR}/compile_commands.json
          ${CMAKE_SOURCE_DIR}/compile_commands.json
  COMMENT
    "copy compile_commands.json build to compile_commands.json project root so tools can find it more easily"
)
