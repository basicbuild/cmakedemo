.
├── CMakeLists.txt
├── CMakeLists.txt.user
├── README.md
├── main.cpp
└── multidir
    ├── CMakeLists.txt
    ├── multi.cpp
    └── multi.h


1 multidir 用于演示，把子目录添加到主目录中，并在IDE中显示子目录中的文件
./CMakeLists.txt
# multidir-1 添加子目录到编译路径
add_subdirectory(multidir)
# multidir-2 包含子目录中的头文件
include_directories(./multidir)
# multidir-3 子目录显示在IDE中， 但是只能显示空文件夹
target_link_libraries(cmakedemo multidirbuild)

./multidir/CMakeLists.txt
# multidir-4 把源文件和头文件添加到子目录中
add_library(${PROJECT_NAME} multi.cpp multi.h)
# multidir-5 添加Qt的模块，缺少的话找不到头文件
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::Core)