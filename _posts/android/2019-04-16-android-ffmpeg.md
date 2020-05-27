---
layout: post
title: FFmpeg 开发中的注意点
category: FFmpeg
tags: FFmpeg FFmpeg
keywords: FFmpeg 填坑
---


## ffmpeg 安装
 

brew install sdl2

git clone https://git.ffmpeg.org/ffmpeg.git ffmpeg

cd 到 ffmpeg目录下

./configure --disable-x86asm --enable-ffplay

make

make install


## FFmpeg android studio 3.6 编译
```

cmake_minimum_required(VERSION 3.4.1)

#找到包含所有的cpp文件
file(GLOB allCpp *.cpp)

add_library( # Sets the name of the library.
        native-lib

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        ${allCpp})

find_library( # Sets the name of the path variable.
        log-lib
        log)

# 引入FFmpeg的头文件
include_directories(${CMAKE_SOURCE_DIR}/include)

# 引入FFmpeg的库文件，设置内部的方式引入，指定库的目录是 -L  指定具体的库-l
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -L${CMAKE_SOURCE_DIR}/${CMAKE_ANDROID_ARCH_ABI}")


target_link_libraries( # Specifies the target library.
        native-lib

        # 先把有依赖的库，先依赖进来
        avformat avcodec avfilter avutil swresample swscale

        # Links the target library to the log library
        # included in the NDK.
        ${log-lib})
```


