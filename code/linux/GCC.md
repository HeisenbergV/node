### 动态库：

1. 类库的名字一般是 libxxx.so
2. 共享：多个应用程序可以使用同一个动态库，启动多个应用程序的时候，只需要将动态库加载到内存一次即可；
3. 开发模块好：要求设计者对功能划分的比较好。
4. 动态函数库的改变并不影响你的程序，所以动态函数库的升级比较方便。


### 静态库：

1. 类库的名字一般是libxxx.a
2. 代码的装载速度快，执行速度也比较快，因为编译时它只会把你需要的那部分链接进去。
3. 应用程序相对比较大，如果多个应用程序使用的话，会被装载多次，浪费内存。
4. 如果静态函数库改变了，那么你的程序必须重新编译。


#### 如果你的系统上有多个应用程序都使用该库的话，就把它编译成动态库，这样虽然刚启动的时候加载比较慢，但是多任务的时候会比较节省内存；如果你的系统上只有一到两个应用使用该库，并且使用的API比较少的话，就编译成静态库吧，一般的静态库还可以进行裁剪编译，这样应用程序可能会比较大，但是启动的速度会大大提高。

### 库文件链接
#### 开发软件时，完全不使用第三方函数库的情况是比较少见的，通常来讲都需要借助许多函数库的支持才能够完成相应的功能。从程序员的角度看，函数库实际上就是一些头文件（.h）和库文件（so、或lib、dll）的集合
#### 虽然Linux下的大多数函数都默认将头文件放到/usr/include/目录下，而库文件则放到/usr/lib/目录下；Windows所使用的库文件主要放在Visual Stido的目录下的include和lib，以及系统文件夹下。但也有的时候，我们要用的库不再这些目录下，所以GCC在编译时必须用自己的办法来查找所需要的头文件和库文件

#### 当借助第三方时 编译(假设为mysql地址)

gcc –c –I /usr/dev/mysql/include test.c –o test.o

#### 链接
gcc –L /usr/dev/mysql/lib –lmysqlclient test.o –o test

### 静态链接库和动态链接库的创建

### 实例参考
问题： 程序test实现了：c调用lua函数库，创建Lua_State变量。lua路径为 /home/lua

1. 编译lua,在/home/lua/下 生成静态链接库 liblua.a文件
2. 编译test程序
   
        $   LUA_INC ?= /home/lua
        export C_INCLUDE_PATH=$(LUA_INC)

        main: main.o
        	gcc main.o -llua -lm -ldl -o main
        
        main.o:
        	gcc -c main.c 
        
        clean:
        	-rm *.o
        	-rm main

其中： 
1. export C_INCLUDE_PATH 表示 编译所需文件的目录
2. -l 表示用来指定程序要链接的库，-l参数紧接着就是库名(一般命名为liblua.a,简写 去掉lib和.a 为 lua)


[参考](http://www.cnblogs.com/ggjucheng/archive/2011/12/14/2287738.html)