cmake_minimum_required(VERSION 3.0)
project(multidirbuild)

# multidir-4 把源文件和头文件添加到子目录中
add_library(${PROJECT_NAME} multi.cpp multi.h)

# multidir-5 添加Qt的模块，缺少的话找不到头文件
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::Core)
