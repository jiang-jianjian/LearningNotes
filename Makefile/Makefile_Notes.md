# Makefile命名
	* 文件命名: `makefile`或`Makefile` 

# Makefile规则
	* 三要素：  目标、依赖、命令
	* 基本格式:
	    目标:依赖
	    命令
	* 实际示例:
	    main.out:main.c
	    	gcc main.c -o main.out

# 多文件Makefile编写
	* 核心思想：最上面的规则目标是终极目标，生成最终终极目标文件的规则语句写在最上面。
	* 实际示例:
	    main.out:main.o add.o sub.o
	    	gcc main.o add,o sub.o -o main.out
	    
	    main.o:main.c
	    	gcc -c main.c
	    
	    add.o:add.c
	   	 gcc -c add.c
	    
	    sub.o:sub.c
	    	gcc -c sub.c
	* makefile可以同时书写多条规则语句，当第一个规则语句在执行命令时没有发现依赖文件时,就在下面寻找。
	  
# 自定义变量
	* 核心思想：使用自定义变量，大大简化Makefile文件书写及维护
	* 使用语法：无需提前定义、声明，直接赋值、使用。`变量名=变量值`，引用时通过`$(变量名)`使用指定变量
	* 实际示例：
	    target=main.out
	    object=main.c add.c sub.c
	    cc=gcc
	    
	    $(target):$(object)
	    	$(cc) $(object) -o $(target)
	* 当目标文件，依赖文件或所使用编译器(gcc)发生改变时，只需修改自定义变量的赋值即可完成makefile文件的修改、维护。

# 自动变量
	* `$<`规则语句中第一个依赖
	* `$^`规则语句中所有依赖
	* `$@`规则语句中的目标

# 模式自动匹配符
	* `%`:模式自动匹配符
	* 实际示例：
	    `./%.o`当前目录下所有后缀为`.o`的文件。`./%.c`当前目录下所有后缀为`.c`的文件

# 函数
	* wildcard:`src=$(wildcard ./*.c)`含义为查找当前目录下所有`.c`文件，并赋值给变量`src`
	* patsubst:`obj=$(patsubst ./%.c, ./%.o, $(src))`将变量`src`中所有`.c`替换为`.o`并赋值给变量`obj`

# 清理删除
	* clean：在`makefile`文件最后加入`clean`的目标，删除清理无用文件。
	* 实际示例：
	    clean:
	    	rm -rf main.o add.o sub .o

# 完整 makefile 示例
	src=$(wildcard ./*.c)
	obj=$(patsubst ./%.c, ./%.o, $(src))
	target=app.out
	CC=gcc
	
	$(target):$(obj)
		$(CC) $^ -o $@
	%.o:%.c
		$(CC) $< -o $@
	

