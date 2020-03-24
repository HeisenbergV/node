### 什么是gdb

#### GDB（GNU Debugger）是GCC的调试工具。其功能强大，现描述如下： 
    GDB主要帮忙你完成下面四个方面的功能： 
    1.启动你的程序，可以按照你的自定义的要求随心所欲的运行程序。 
    2.可让被调试的程序在你所指定的调置的断点处停住。（断点可以是条件表达式） 
    3.当程序被停住时，可以检查此时你的程序中所发生的事。 
    4.动态的改变你程序的执行环境。
    
    
    
### 基本命令

命令 | 简写形式| 说明
---|---|---
list | l| 查看源码
backtrace|	bt、where|	打印函数栈信息
next	|n	|执行下一行
step	|s	|一次执行一行，遇到函数会进入
finish	|	|运行到函数结束
continue	|c	|继续运行
break	|b	|设置断点
info breakpoints|	info b	|显示断点信息
delete	|d	|删除断点
print	|p|	打印表达式的值
run	|r	|启动程序
until	|u|	执行到指定行
info	|i|	显示信息
help	|h|	帮助信息


### 案例

```
#include <stdio.h>  
  
int iterate(int value)  
{  
    if(1 == value)  
        return 1;  
  
    return iterate(value - 1) + value;  
}  
  
int main()  
{  
    printf("%d\n", iterate(10));  
    return 1;  
}

编译： gcc test.c -g -o test  //-g表示使用gdb调试
```


### 断点
1. 断点的设置 ：b 行号; b 函数名; b 文件名: 行号or函数名; 三种方式
2. info b查看断点信息
    #### 每一项代表： 
        Num 列代表断点编号，该编号可以作为 delete/enalbe/disable 等控制断点命令的参数
        Type 列代表断点类型，一般为 breakpoint
        Disp 列代表断点被命中后，该断点保留(keep)、删除(del)还是关闭(dis)
        Enb 列代表该断点是 enable(y) 还是 disable(n)
        Address 列代表该断点处虚拟内存的地址
        What 列代表该断点在源文件中的信息

3. 删除断点: d 无参数 表示删除所有断点; d 断点编号(Num字段，并非行号) 删除指定断点
4. enable disable 关闭启动所有断点， 加参数(断点编号)表示关闭启动指定断点
5. enable once Num(断点编号) 命中一次后关闭此断点 ， enable delete Num 命中后删除；
### 调试
1. 启动 GDB:
    #### 方法有以下几种:
        1、gdb <program> 
        program也就是你的执行文件，一般在当然目录下。 
        
        2、gdb <program> core 
        用gdb同时调试一个运行程序和core文件，core是程序非法执行后core dump后产生 
        的文件。 
        
        3、gdb <program> <PID> 
        如果你的程序是一个服务程序，那么你可以指定这个服务程序运行时的进程ID。gd 
        b会自动attach上去，并调试他。program应该在 PATH环境变量中搜索得到。 
2. set args 设置启动参数比如：set args 11 10传入11和10；set args /home/config传入文件。show args 查看参数信息
3. run启动执行


### GDB 函数栈
1. info proc mappings

###  观察点
1. watch 为表达式（变量）expr设置一个观察点。当表达式值有变化时，马上停住程序。
2. rwatch 表达式（变量）expr被读时，停住程序。
3. awatch 表达式（变量）的值被读或被写时，停住程序。
4. info watchpoints 列出当前所设置了的所有观察点。

### 更改变量值
1. p 变量 = 新值 or set var 变量 = 新值
2. 如果变量只定义未赋值，在gdb调试的时候就不能进行设置值，gdb只能修改不能赋值操作

### 其他命令
1. 在gdb中 使用 !+shell命令 可以执行shell命令： !ls 列出本目录下文件
2. 在gdb中输入 ctrl+x+a 可以进入tui界面，再次输入会退出

### 输出
1. 可使用set进行配置print修改输出样式
2. 如果输出指针指向的数据 按照c的写法：*a 输出a指针指向的数据
3. [参考格式化输出](http://blog.csdn.net/unix21/article/details/9991925)







[参考](http://www.cnblogs.com/ggjucheng/archive/2011/12/14/2288004.html#_Toc311658086)