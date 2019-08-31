---
layout: post
title:  "Unix基础知识"
date:   2019-08-27 23:00:00 +0800
---

本章介绍了Unix相关的基础知识，包括基本概念和全书的概括。

## Unix体系结构

* 内核（kernel）/操作系统

* 系统调用（system call）：内核的接口

## 登录

* 口令文件 /etc/passwd
    * 登录名、加密口令、数字用户ID、数字组ID、注释字段、起始目录（/home/sar)、shell程序（/bin/ksh），如``sar:x:205:105:Stephen Rago:/home/sar:/bin/ksh``

* 加密口令 ``/etc/shadow``

* shell
    * ``sh bash csh ksh tcsh``
   
## 文件与目录

* 文件系统
    * 根（root) /
    * 目录（directory）：包含目录项的文件
    * 目录项：文件名+文件属性（文件类型、文件大小、文件所有者、文件权限、最后修改时间）
    * ``stat fstat``

* 文件名（filename）
    * 只有斜线``/``（分隔）和空字符（终止）不能出现在文件名中
    * POSIX.1推荐限制在字母(a-zA-Z)、数字(0-9)、句点(.)、短横线(-)、下划线(_)内
    * 为新目录自动创建的两个文件名当前目录``.``，父目录 ``..``

* 路径名：以斜线分隔的一个或多个文件名组成的序列
    * 绝对路径名：以斜线开头的路径名称
    * 相对路径名：不以斜线开头的路径名称，相对于当前目录的文件

* 工作目录（working directory）/当前工作目录（current working directory）
    * chdir更改工作目录

* 起始目录（home directory）

## 输入输出

* 文件描述符 file descriptor

* 标准输入、标准输出、标准错误(Standard input/output/error)

* 不带缓冲的I/O：``open write read lseek close``
    * ``unistd.h`` 常量``STDIN_FILENO`` ``STDOUT_FILENO``

* 标准I/O
    * ``getc putc stdin stdout EOF``  stdio.h

## 程序与进程

* 程序 Program

* 进程process  进程ID process ID  任务task

* 进程控制 ``fork exec waitpid``
    * exec函数7种变体

* 线程（thread） 线程ID
 
## 出错处理

* ``errno``
    * ``<error.h>``定义了errno常量
    * ``extern int errno;``
    * 线程局部``errno​``
        * ```c
            extern int *__errno_location(void);
            #define errno (*__errno_location())
          ```
    * C标准定义了两个函数
        * ``<string.h>``定义了``char *strerror(int errnum);``
        * ``<stdio.h>``定义了``void perror(const char *msg);``
        
* 出错恢复
    * 致命错误
    * 非致命错误
        * 与资源相关：``EAGAIN ENFILE ENOBUFS ENOLCK ENOSPC EWOULDBLOCK``，可视为非致命错误``ENOMEM EBUSY EINTR``
        
## 用户标识

* 用户ID（user ID）
    * 超级用户（superuser）或根用户（root): ID为0的用户
* 组ID（group ID）
    * 组文件``/etc/group``
* 附属组ID（supplementary group ID)

## 信号

* 信号（signal）
    * 浮点异常 SIGFPE
    * 终端键盘两种产生信号的方式
        * 中断键（interrupt key） ``Delete``或``Ctrl+C``
        * 退出键（quit key） ``Ctrl+\``
    * 调用kill函数产生信号

* 三种信号处理方式
    * 忽略信号
    * 按系统默认方式处理
    * 提供一个函数
    
## 时间值

* 两种不同的时间
    * 日历时间：自协调世界时（Coordinated Universal Time, UTC) 1970年1月1日00:00:00以来的秒数，系统基本数据类型``time_t``
    * 进程时间/CPU时间，系统基本数据类型``clock_t``
    
* 度量进程执行时间，执行time命令进行度量
    * 时钟时间：墙上时钟时间（wall clock time）
    * 用户CPU时间：执行用户指令所用时间量
    * 系统CPU时间
    
## 系统调用和库函数

* 系统调用通常提供一种最小接口，库函数通常提供比较复杂的功能