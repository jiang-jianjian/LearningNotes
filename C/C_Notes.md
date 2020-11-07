# 存储类
	* `auto存储类`是所有局部变量默认存储类-`auto存储类`只能用在函数内，修饰局部变量。
	* `register存储类`用于定义存储在寄存器中而不是RAM中的局部变量。这意味变量尺寸等于寄存器大小，
	  能进行取地址`&`操作，因为它没有内存地址
	* `static存储类`修饰变量为静态变量。
	* `extern存储类`修饰变量为外部变量或对外部模块可见。

# 位域
	* C语言提供的一种更好利用内存空间的方式，定义变量时同时定义变量宽度，告诉编译器将只使用这些字节。
	* 声明形式：
	  struct
	  {
	    type(int\signed int\unsigned int) [member_name] : width;
	  }struct_name;
	* 使用实例：
		enum
		{
		  struct 
		  {
		    uint8_t fh_err   : 1; //帧头接收错误-fh(frame head)
		    uint8_t add_err  : 1; //地址接收错误
		    uint8_t cmd_err  : 1; //命令码接收错误
		    uint8_t data_err : 1; //数据接收错误
		    uint8_t crc_err  : 1; //校验码接收错误
		    uint8_t ack_err  : 1; //应答接收错误
		    uint8_t ft_err   : 1; //帧尾接收错误-ft(frame tail)
		    uint8_t send_err : 1; //发送错误
		  }bits;
		  uint8_t communicate_errs;
		}

# 预处理器
	
# 错误处理
	* `errno`函数库设置的错误代码，全局变量，在头文件`errno.h`中有各式各样的错误代码。
	* `perro()`该函数将显示用户传参的字符串，后跟一个冒号及一个空格和当前`errno`值的文本形式。
	* `strerro()`该函数返回一个指针，指针指向当前`errno`值得文本形式。

# 可变参数
	* 实现步骤：
		* 包含头文件`stdarg.h`。
		* 变参函数最后一个参数为省略号(...)，省略号前面可以设置自定义参数。
		* 变参(...)前最后一个参数必须为`int`,代表可变参数个数。
		* 在函数定义中创建一个`va_list`类型变量。并使用`int`参数和`va_start`宏初始化`va_list`变量。
		* 使用`va_arg`宏和`va_list`变量访问变参列表中每一个项。
		* 使用宏`va_end`来清理赋予`va_list`变量的内存。
	* 使用实例：
		#include<stdio.h>
		#include<stdarg.h>

		double average(int num,...)
		{
		  va_list valist;
		  double sum = 0.0;		  
		  int i = 0;

		  va_start(valist,num);
		  for(i = 0;i < num;i++)
		  {
		    sum += va_arg(valist,i);
		  }
		  va_end(valist);

		  return sum/num;
		}

