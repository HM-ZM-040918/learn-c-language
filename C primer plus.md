***
# one day（3.21.2025）
## 第三章数据和C
### 整数类型与浮点数类型
1. 案例
```c
/*案例*/
#include <stdio.h> 
int main() {
	float weight; //声明一个名为weight（重量）的浮点型变量
	float value; //声明一个名为value（价格）的浮点型变量
	printf("Are you worth your weight in platinum?\n"); //打印上述文本
	printf("Let's check it out.\n"); //打印上述文本
	
	printf("Please ebter your weight in pounds: "); //提示输入weight变量参数
	scanf("%f”, &weight); //读取用户输入参数并存储在weight变量中
	value = 1700.0 * weight * 14.5833; //将参数带入计算并将结果存储到value变量中

	printf("Your weight in platinum is worth $%.2f.\n", value); //将变量value输出到屏幕上，并将结果保留两位
	printf("You are easily worth that! If platinum prices drop,\n");
	printf("eat more to maintain your value.\n");

	return 0;
}
运行结果如下
Are you worth your weight in platinum?
Let's check it out.
Please ebter your weight in pounds:213.2 //此处假设用户输入为213.2
Your weight in platinum is worth $5285571.00. //此处保留两位小数
You are easily worth that! If platinum prices drop,
eat more to maintain your value.
//上述运行结果来源于QT,如果输入后程序消失就在return 0，前面加getchar();用来接收scanf输入数字后的enter
```

***
2. 常量与变量数据
	* 常量：数据在程序运行前到结束一直没有变化的量； eg：10；
	* 变量：数据在程序运行过程中被赋予某一个值，或者改变原数值 value = 10；
3. 数据类型与关键词
	* 整数类型：short、int 、long int、long long int、unsigned int 、unsignet long int、unsigned long long int；其中long int 、long long int 中int 可以省略，unsigned则表示为无符号只能是正数；
	* 字符类型：char；
	* 浮点数类型：float、double、long double、unsigned double、unsigned long double；
	* 位、字节、字
	* 位（bit）：是存储单元中最小的计数单位，只能存储0和1；
	* 字节：是常用的计数单位，1个字节（byte）= 8位（bit），存储的可能为2^8 = 256种可能 0~255的组合0与1的方式；
	* 字：是计算机给定的自然存储单位，与计算机位数有关，例如1字长32位计算机就等于4个字节，1字长64位计算机就等于8个字节；
4. 整数
	* 整数：不带小数位的正整数、负整数、0都是整数；
	* 数字8用下述表示

| byte |   7   |   6   |   5   |   4   |   3   |   2   |   1   |   0   |
| :--: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| bit  |   0   |   0   |   0   |   0   |   1   |   0   |   0   |   0   |
|      | 0*2^7 | 0*2^6 | 0*2^5 | 0*2^4 | 1*2^3 | 0*2^2 | 0*2^1 | 0*2^0 |
数字8的值就为0`*2^0+0`*2^1+1`*2^2+0`*2^3 = 8

|  +  | .314159 |  1  |
| :-: | :-----: | :-: |
| 符号位 |   小数位   | 指数位 |
Π的小数存储形式，浮点数的存储形式是以指数方式存储，将浮点数分为小数部分和指数部分，也就是10的幂指数，0.314159`* 10^1，而7为整数，7.00为浮点数可也写成0.7`* 10^1
5. 数据类型的详细介绍
	* int类型
	* int为有符号整数类型可以是正整数、负整数、零，一个int类型占1个字长，根据操作系统位数，32位操作系统1字长就是=32位=4个字节，64位操作系统1字长=64位=8个字节；
	* 如何使用int：首先要在程序中声明
```c
	#include <stdio.h>
	int main() {
		int cows; //此处就是在程序中声明一个int的整型变量，名称位cows
		int erns, dogs, hogs; //声明时也可以声明多个变量名
		return 0;
	}
```
	赋值:分为直接赋值和间接赋值
```c
		int cows = 10;
		int erns = 14, dogs = 20, hogs = 100;
		int goars;
		goats = 11; //以上三种都是可以使用的，但是不能使用未先赋值的变量进行计算，否则会出现许多问题，他将会显示存储中存放的随机数；
		//上面是直接赋值法，将事先的数直接赋值给变量
		//间接赋值法通过scanf函数进行赋值，将变量通过用户输入的方式进行赋值，这样更具有交互性
		int value；
		scanf("%d", &value); //通过用户输入将数值赋值给value变量
```
	那么如何验证int在计算机中的占字节数呢可以通过以下程序
```c
#include <stdio.h>
int main() {
	printf("int: %d\n",sizeof(int)); //此处使用siezof()函数将所要求的占字节数变量类型放入，siezof int后面是变量类型可以不加括号，如果是变量名必须加括号；
	return 0;
}
```
	那么如何验证1个字节的取值范围呢？此处是在无符号的基础上编写的代码
```c
#include <stdio.h>
int main() {
	int value, t; //t作为最后输出变量，value变量为初始设置值
	value = t = 1; //value 取代了第一位2的0次幂
	for (int i = 1; i < 8 i++) { //此处使用for循环，循环七次
	value *= 2; //2的幂指数就是乘2
	t += value; //将最后的数值累加
	}
	printf("%d\n", t);
	return 0;
}
//最终的结果为255，也就是说1个字节的取值范围是0~255
```
* 示例
```c
#include <stdio.h>
int main () {
	int ten = 10;
	int two = 2;
	printf("Doing it right: "); //正确代码
	printf("%d minus %d is %d\n", ten, two, ten - two); //此处是%d分别代替“，”后面的变量，第一个是代替ten以此类推
	
	printf("Doing it wrong: "); //错误代码
	printf("%d minus %d is %d\n", ten); //此处缺少2个变量
	return 0;
}
//打印结果一：
Doing it right: 10 minus 2 is 8
Doing it wrong: 10 minus 23298679 is 236507653 //显示的是错误数值
//出现第二个的原因主要是在代码中，缺乏对应变量的写入，导致内存中的任意值直接打印出来
```
* 八进制与十六进制
	* 八进制
	* 八进制为2^3 ，转化为2进制则每一位转换为3位
	* 八进制5为005，每一位是从0-7的数字，每一位都是8的幂指数从0开始
	* 十六进制
	* 十六进制为2^4，转化为2进制则每一位转化为4位
	* 十六进制5位0X5，每一位是从0-F的数字，从9之后由A~F代替到15，每一位都是16的幂指数

|      | 15  | 14  | 13  | 12  | 11  | 10  |  9  |  8  |  7  |  6  |  5  |  4  |  3  |  2  |  1  |  0  |
| ---- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 十六进制 |  F  |  E  |  D  |  C  |  B  |  A  |  9  |  8  |  7  |  6  |  5  |  4  |  3  |  2  |  1  |  0  |
***
* 显示八进制与十六进制
	* 十进制使用%d用来替代变量并以十进制显示整数
	* 八进制使用%o用来代替变量并显示八进制显示整数，如果使其显示符号则在前面加#，%#o，或%#O，大小O不影响最后的结果
	* 十六进制使用%x用来代替变量并显示十六进制显示整数，如果使其显示符号则在前面加#，%#x，或者%#X，大小X只是显示十六进制符号大小写的区别0X与0x
	```c
	#include <stdio.h>
	int main() {
		int x = 100;
		printf("dec = %d; octal = %o; hex = %x\n", x, x, x);
		printf("dec = %d; octal = %#o; hex = %#x\n", x, x, x); //带符号的八进制与十六进制
		return 0;
	}
	```
* 其他整数类型
	* short int (short)占用比int空间小，短整数类型数%hd
	* long int(long)占用与int相同或大，长整整数类型数
	* long long int(long long)占用空间比long大%lld、%llu
	* 上述都是由符号类型整数
	* unsigned int(unsigned)用与非负数的变量既无符号整数，也有unsigned short、unsigned long 、unsigned long long
	* 注意转换类型与转化符要匹配，如果不匹配大数转换符小则会与原数值对应不上；
* 示例
```c
#include <stdio.h>
int main() {
	unsigned int un = 3000000000; //声明无符号un变量
	short end = 200; //声明短整型有符号end变量
	long big = 65537; //声明长整型有符号big变量
	long long verybig = 12345678908642; //声明长长整型有符号verybig变量
	printf("un = %u and not %d\n", un, un); //用有符号和无符号输出
	printf("end = %hd and %d\n", end, end); //用短整型与整型输出
	printf("big = %ld and not %hd\n", big, big); //用长整型与短整型输出
	printf("verybig = %lld and not %ld\n", verybig, verybig); //用长长整型与长整型输出

	return 0;
}
//p1：输出位无符号的un原数值，而有符号因为超过了原本的正值变换为最小值加上剩余值
//p2：输出值end不大没有出现结余
//p3：hd输出出现结余只存储后十六位有效数字
//p4：ld出现结余只存储后32位有效数字
```
6. char字符类型
	* char实际是整数类型，主要原因char类型存储的是整数而不是字符，利用ASCII码，进行转化65~96从A~、97~127位为a~、，平常使用最好不要用数字代替整数，char字符由1byte组成8bit,0-255，转义字符为%c；
	```c
	#include <stdio.h>
	int main() {
		char grade = 'A';
		char grade_n = 65;
		printf("%c\n", grade); //给grade赋值A
		printf("%c\n", grade_n); //通过ASCII表给grade_n赋值
		return 0;
	}
```

| 转义序列 | \a  | \b  | \f  | \n  | \r  |  \t   |  \v   |  \\\   | \\' | \\" | \\? |     \0oo      |      \xhh      |
| :--: | :-: | :-: | :-: | :-: | :-: | :---: | :---: | :----: | :-: | :-: | :-: | :-----------: | :------------: |
|  含义  | 警报  | 退格  | 换页  | 换行  | 回车  | 水平制表符 | 垂直制表符 | 反斜杠（\） | 单引号 | 双引号 | 问号  | 八进制值（oo表示0-7） | 十六进制值（hh表示0-f） |
* \b就是backpack键，删除键，\f与\n、\v相似都是换行没有区别，\t就是tab键，\r是清除当前行；
* 代码中可以用八进制16进制来代替字符
```c
#include <stdio.h>
int main() {
	char beep = '\007'; //用八进制来代替\a
	printf("%c", beep);
	printf("%c\n", '\x41'); //与'A'一样用十六进制转换65字符'A'八进制也可以
	printf("%c\n", '\101'); //八进制的'A'
	printf("beep_num = %d\n", beep);
	return 0;
}
```
char也分有符号sign与无符号unsigned，sign：-127~128；unsigned：0~255；
* bool数值类型
* 0代表true、1代表false，空间仅占1bit
7. float double long double
	 *   float有效数字至少为6位，占用4byte=32bit，8bit表示符号与指数，其余位24位为表示非指数部分
	 * double有效数字至少为12位，占用8byte=64bit，32bit表示符号与指数，其余位32位为表示非指数部分
	 * long double的精度最小与double一致
	 * 浮点数声明
```c
#include <stdio.h>
int main() {
	float noah, jonah; //声明多个变量
	float planck; //声明单个变量
	double truble; //声明单个变量
	float = planck = 6.63e-34f; //声明变量时赋给初始值，无论'E'或'e'都表示10的指数幂
	float some = 7.0f * 9.0f; //系统默认浮点数存储为double类型，需要在常量后面加f表示float常量
	long double tk = .2e4L; //表示存储类型为long double初始值后面加L或l
	double P = 0Xa.1fp10; //C99新增p以2为指数幂，用16进制表示（10+1/16+15/256）* 1024
	//a = 10，.1 = 1/16^1，.1f = 15/16^2，p10 = 2^10 = 1024，小数位的进制数与小数点前不一样，小数点后的分16^-1,16^-2,16^-3.....输出为%a
	return 0;
}
```
示例
```c
#include <stdio.h>
int main() {
	float aboat = 32000.0;
	double abet = 2.14e9;
	long double dip = 5.32e-5;
	float dt = 3.4e39f * 100.0f; //此处输出会超过最大值，输出会显示inf或infinity表示上溢
	printf("%f can be written %e\n", aboat, aboat);
	printf("And it's %a in hexadecima, powers of 2 notation\n", aboat); //十六进制p
	printf("%f can be written %e\n", abet, abet);
	printf("%Lf can be written %Le\n", dip, dip);
	return 0;
}
```
8. 类型大小
	* 使用sizeof函数，转义字符%zd
```c
#include <stdio.h>
int main() {
	printf("type int has a size if %zd bytes.\n", sizeof(int)); // 4
	printf("type char has a size if %zd bytes.\n", sizeof(char)); // 1
	printf("type long has a size if %zd bytes.\n", sizeof(long)); // 4
	printf("type long long has a size if %zd bytes.\n", sizeof(long long)); // 8
	printf("type double has a size if %zd bytes.\n", sizeof(double)); // 8
	printf("type float has a size if %zd bytes.\n", sizeof(float)); // 4
	printf("type long double has a size if %zd bytes.\n", sizeof(long double)); // 16
	return 0;
}
```
9. 使用数据类型
	* 声明变量时赋予初始值应当匹配否则会出现数据丢失
	```c
	#include <stdio.h>
	int main() {
		int apple = 3;
		int oranges = 12.99; //使用double类型初始化int类型将会失去小数部分；
		float pi = 3.1415926536; //使用double类型初始化float类型将会失去部分精度
		int i_oranges = 12; //程序变量命名可以加上类型简写来表明变量的数据类型i_表示int类型
		double d_pi = 3.1415926536; //d_表示double类型
		return 0;
	}
```

