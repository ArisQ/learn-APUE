# 《UNIX环境高级编程》学习笔记

## 1. Unix基础知识

* 内核（kernel）/操作系统
  * 系统调用（system call）：内核的接口
* 登录
  * 口令文件 /etc/passwd
    * 登录名、加密口令、数字用户ID、数字组ID、注释字段、起始目录（/home/sar)、shell程序（/bin/ksh）
    * 加密口令
  * shell
    * sh bash csh ksh tcsh
* 文件与目录
  * 文件系统
    * 根（root) /
    * 目录（directory）：包含目录项的文件
    * 目录项：文件名+文件属性（文件类型、文件大小、文件所有者、文件权限、最后修改时间）
    * stat fstat
  * 文件名（filename）
    * 只有斜线``/``（分隔）和空字符（终止）不能出现在文件名中
    * POSIX.1推荐限制在字母(a-zA-Z)、数字(0-9)、句点(.)、短横线(-)、下划线(_)内
    * 为新目录自动创建的两个文件名当前目录``.`` 父目录 ``..``
  * 路径名：以斜线分隔的一个或多个文件名组成的序列
    * 绝对路径名：以斜线开头的路径名称
    * 相对路径名：不以斜线开头的路径名称，相对于当前目录的文件
  * 工作目录（working directory）/当前工作目录（current working directory）
    * chdir更改工作目录
  * 起始目录（home directory）
* 输入输出
  * 文件描述符 file descriptor
  * 标准输入、标准输出、标准错误
  * 不带缓冲的I/O：``open write read lseek close``
    * ``unistd.h`` 常量STDIN_FILENO STDOUT_FILENO
  * 标准I/O
    * ``getc putc stdin stdout EOF``  stdio.h

