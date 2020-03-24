### 程序的编译过程
##### 编译与链接->可执行程序
 1.生成预处理后的文件 hello.i

     $ gcc -E hello.c -o hello.i

  2 .生成汇编语言文件 hello.s

      $ gcc -s hello.i -o hello.s

   3.生成目标文件 hello.o

      $ gcc -c hello.i
      $ gcc -c hello.s

   4. 生成可执行文件

      $ gcc -o hello hello.o

   5. 运行及结果


### makefile规则
    $ target(目标): prerequisites(所需条件)
              (Tab) command(命令)

### makefile案例
    $  main: main.o other.o
             cc -o main.o other.o
       main.o: main.c main.h
             cc -c main.c
       other.o: other.c other.h
             cc -c other.c
       clean:
             -rm *.o main

### 如何工作
    1. 读入所有的Makefile。
    2. 读入被include的其它Makefile。
    3. 初始化文件中的变量。
    4. 推导隐晦规则，并分析所有规则。
    5. 为所有的目标文件创建依赖关系链。
    6. 根据依赖关系，决定哪些目标要重新生成。
    7. 执行生成命令。
    
### 自动推导
##### make会根据.o文件默认关联相应的.c文件
    $   main.o: main.h
        other.o: other.h

### 引用其他makefile
    1. 使用 include <filename>引用其他 mk文件
    2. 寻找：
        1）如果文件都没有指定绝对路径或是相对路径的话
        2）make会在当前目录下首先寻找
        3）make还会在下面的几个目录下找：如果make执行时，有“-I”或“--include-dir”参数，那么make就会在这个参数所指定的目录下去寻找。如果目录<prefix>/include（一般是：/usr/local/bin或/usr/include）存在的话，make也会去找。

### 通配符


### 文件搜索
    1. VPATH变量
    2. vpath关键字
### 伪目标

    clean:
         rm *.o
##### 其中clean并不是要生成的目标文件，只是一个标签，所以make无法生成它的依赖关系和决定它是否要执行。我们只有通过显示地指明这个“目标”才能让其生效。所以为了避免和文件重名的这种情况，我们可以使用一个特殊的标记“.PHONY”来显示地指明一个目标是“伪目标”，向make说明，不管是否有这个文件，这个目标就是“伪目标”
    .PHONY : clean
    
### 静态模式

### 变量

1. a = foo
2. a := foo
3. a ?= foo
4. a += foo
[makefile教程](http://blog.csdn.net/Sun_Jianhua/article/details/494002)