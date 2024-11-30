---
layout: post
title: "find_package()"
subtitle: "CMakeLists.txt 命令"
date: 2024-11-30 21:53:29
author: "WenXingming"
published: true
catalog: true
# header-img: "img/about-bg.png"
tags: [CMake]
---

## find_package()

***Q***：@workspace /explain Write an explanation for the active selection as paragraphs of text.

```cmake
find_package(OpenCV 3 REQUIRED) # 寻找 Opencv库
```

***A***：这段代码是一个CMake指令，用于在C++项目中查找和配置OpenCV库。CMake是一个跨平台的构建系统，广泛用于管理项目的编译过程。具体来说，`find_package(OpenCV 3 REQUIRED)`指令告诉CMake查找OpenCV库的版本3，并将其配置到项目中。以下是这条指令的详细解释：

- `find_package`是CMake的一个命令，用于查找外部库或包。
- `OpenCV`是要查找的库的名称。在这种情况下，是OpenCV，一个流行的计算机视觉库。
- `3`指定了所需的OpenCV库的最低版本号。在这里，要求至少是版本3。
- `REQUIRED`关键字表示这个库是必需的。如果CMake无法找到指定版本的OpenCV库，它将停止配置过程并报错。

通过使用`find_package(OpenCV 3 REQUIRED)`，CMake会在系统中搜索OpenCV库，并设置相应的变量（如`OpenCV_INCLUDE_DIRS`和`OpenCV_LIBS`），以便在项目中使用这些变量来包含头文件和链接库文件。

注释`# 寻找 Opencv库`进一步解释了这条指令的作用，即在项目中寻找并配置OpenCV库。

总结来说，这段代码的作用是确保CMake能够找到并配置至少版本3的OpenCV库，使得项目能够使用OpenCV提供的功能进行计算机视觉相关的开发。如果未找到指定版本的OpenCV库，CMake将会报错并停止配置过程，从而提醒开发者安装或更新OpenCV库。

----

***Q***：找的是库的头文件还是库文件？

***A***：`find_package(OpenCV 3 REQUIRED)`指令用于查找OpenCV库的头文件和库文件。具体来说，它会查找以下内容：

1. **头文件**：OpenCV库的头文件通常位于安装目录的`include`子目录中。CMake会找到这些头文件，并设置相应的变量（如`OpenCV_INCLUDE_DIRS`），以便在项目中包含这些头文件。

2. **库文件**：OpenCV库的二进制库文件（如`.so`、`.dll`或`.lib`文件）通常位于安装目录的`lib`子目录中。CMake会找到这些库文件，并设置相应的变量（如`OpenCV_LIBS`），以便在项目中链接这些库文件。

通过查找头文件和库文件，CMake确保项目能够正确编译和链接OpenCV库，从而使用其提供的功能进行计算机视觉相关的开发。

----

## 示例

```cmake
find_package(OpenCV 3 REQUIRED)	# 找库
include_directories(${OpenCV_INCLUDE_DIRS})	# 加入头文件
    
find_package(Pangolin REQUIRED)
include_directories(${Pangolin_INCLUDE_DIRS})

add_executable(stereoVision stereoVision.cpp)
target_link_libraries(stereoVision ${OpenCV_LIBS} ${Pangolin_LIBRARIES}) # 链接库
```

