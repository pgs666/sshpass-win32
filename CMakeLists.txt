cmake_minimum_required(VERSION 3.20)

project(sshpass)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(${PROJECT_NAME} main.c argparse.c)
target_compile_definitions(${PROJECT_NAME} PRIVATE
  _WIN32_WINNT=0x0A00
  WINVER=0x0A00)

if(MSVC)
  target_compile_options(${PROJECT_NAME} PRIVATE /W4 /utf8)
endif()

set_property(TARGET ${PROJECT_NAME} PROPERTY
  MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")


