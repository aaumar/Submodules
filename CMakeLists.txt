cmake_minimum_required(VERSION 3.15)

project(ipopt)

add_library(mylib STATIC src/hello.cpp include/hello.h)
target_include_directories(mylib PUBLIC "include/")

add_executable(app app/main.cpp)
target_link_libraries(app PRIVATE mylib) 