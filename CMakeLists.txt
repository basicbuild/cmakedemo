cmake_minimum_required(VERSION 3.14)

project(cmakedemo LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core)

add_executable(cmakedemo
  main.cpp
)
target_link_libraries(cmakedemo Qt${QT_VERSION_MAJOR}::Core)

# 1 主目录包含子目录，并在IDE中显示子目录文件
# multidir-1 添加子目录到编译路径
add_subdirectory(multidir)
# multidir-2 包含子目录中的头文件
include_directories(./multidir)
# multidir-3 子目录显示在IDE中， 但是只能显示空文件夹
target_link_libraries(cmakedemo multidirbuild)
#target_link_libraries(appbasicdemo PRIVATE multidirbuild)

install(TARGETS cmakedemo
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
