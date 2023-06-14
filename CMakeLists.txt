cmake_minimum_required(VERSION 3.15)

project(journey)

add_subdirectory(external/cppad)

add_library(mylib STATIC src/hello.cpp include/hello.hpp)
target_include_directories(mylib PUBLIC "include/" PUBLIC external/cppad/include)

add_executable(${PROJECT_NAME} app/main.cpp)
target_link_libraries(mylib PRIVATE cppad_lib ipopt)
target_link_libraries(${PROJECT_NAME} PRIVATE mylib) 

# add submodule with this command in terminal
# can use any git repo
# git submodule add https://github.com/coin-or/CppAD.git external/cppad