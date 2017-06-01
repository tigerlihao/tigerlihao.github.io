---
title: Dev C++中配置glfw编译环境
date: 2014-06-19 00:00:00 Z
categories:
- study
tags:
- Dev C++
- glfw
- C
- mingw
- OpenGL
layout: post
---

### 问题

最近用学习OpenGL，在Windows 7下用Dev C++作为开发环境、Mingw32做编译器、用glfw库，但编译时一直提示
`.../libglfw.a(win32_window.o):win32_window.c:(.text+0x6f0)：对‘_imp__wglMakeCurrent@8’未定义的引用`
`.../libglfw.a(win32_window.o)win32_window.c:(.text+0xe70): undefined reference to 'wglCreateContext@4'`
`bad reloc address 0x0 in section '.rdata'。`
确认已经把glfw的lib目录加入到编译参数中去了，也按要求加了“-opengl32”，而且将glfw的libglfw.a文件放到Mingw32的lib目录下也一样。

### 解决
看了下glfw的源代码中例子的make文件，发现它们是直接把libglfw.a文件的路径放进编译参数中去的，这样可以编译通过。
所以解决办法就是在Dev C++的Project options中，在Parameters选项卡的linker中，加入libglfw.a文件的路径。注意是文件的路径不是-L“所在文件夹”。