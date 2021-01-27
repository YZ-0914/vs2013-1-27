# vs2013-1-27
//操作符
#define _CRT_SECURE_NO_WARNINGS 1
#include<stdio.h>
//操作符详解
//算数操作符
//1.除了%操作符之外，其他的几个操作符可以作用于整数和浮点数。
//2.对于/操作符如果两个操作数都为整数，执行整数除法。而只要有浮点数执行的就是浮点数除法。
//3.%操作符的两个操作数必须为整数，返回的是整除之后的余数。
int main()
{
	int a = 5 / 2;//商2余1
	printf("a=%d\n", a);
	return 0;
}

int main()
{
	int a = 5 % 2;//商2余1
	printf("a=%d\n", a);
	return 0;
}

int main()
{
	double a = 5 / 2.0;//商2余1
	printf("a=%d\n", a);
	return 0;
}

//移位操作符
//<<左移操作符
//>>右移操作符

int main()
{
	int a = 16;
	//>>--右移操作符
	//移动的是二进制位
	//00000000000000000000000000010000
	int b = a >> 1;
	printf("%d\n", b);
	return 0;
}

int main()
{
	int a = -1;
	//
	//整数的二进制表示有：原码、反码、补码
	//存储到内存的是补码
	//10000000000000000000000000000001 - 原码
	//11111111111111111111111111111110 - 反码
	//11111111111111111111111111111111 - 补码
	int b = a >> 1;
	printf("%d\n", b);
	return 0;
}

int main()
{
	int a = 5;
	int b = a << 1;
	//0000000000000000000000000000101
	printf("%d\n", b);
	return 0;
}


//警告：对于移位运算符，不要移动负数位，这个是标准未定义的。
int main()
{
	int num = 10;
	num >> -1;//error
	return 0;
}

//位操作符
// & 按位与
// | 按位或
// ^ 按位异或
//注：他们的操作数必须是整数。
int main()
{
	int num1 = 1;
	int num2 = 2;
	num1 & num2;
	num1 | num2;
	num1 ^ num2;
	return 0;
}

int main()
{
	//& - 按2进制位与
	int a = 3;
	int b = 5;
	int c = a&b;
	//000000000000000000000000000000011
	//000000000000000000000000000000101
	//000000000000000000000000000000001
	printf("%d\n", c);
	return 0;
}

int main()
{
	//| - 按2进制位或
	int a = 3;
	int b = 5;
	int c = a|b;
	//000000000000000000000000000000011
	//000000000000000000000000000000101
	//000000000000000000000000000000111
	printf("%d\n", c);
	return 0;
}
int main()
{
	//| - 按2进制位异或
	int a = 3;
	int b = 5;
	int c = a ^ b;
	//000000000000000000000000000000011
	//000000000000000000000000000000101
	//000000000000000000000000000000110
	printf("%d\n", c);
	return 0;
}

int main()
{
	//异或的方法
	int a = 10;
	int b = 20;
	a = a^b;
	b = a^b;
	a = a^b;
	printf("a=%d b=%d\n", a, b);
	return 0;
}

int main()
{
	int a = 3;
	int b = 5;
	int tmp = 0;
	printf("before:a=%d b=%d\n", a, b);
	tmp = a;
	a = b;
	b = tmp;
	printf("after:a=%d b=%d\n", a, b);
	return 0;
}


int main()
{
	//加减法-可能会溢出
	int a = 3;
	int b = 5;
	a = a + b;
	b = a - b;
	a = a - b;
	printf("after:a=%d b=%d\n", a, b);
	return 0;
}

//编写代码实现：求一个整数存储在内存中的二进制中1的个数。
int main()
{
	int num = 10;
	int count = 0;//计数
	while (num)
	{
		if (num % 2 == 1)
			count++;
		num = num / 2;
	}
	printf("二进制中1的个数=%d\n", count);
	return 0;
}

int main()
{
	int num = 0;
	int count = 0;
	scanf("%d", &num);//3-011
	//统计num的补码中有几个1
	while (num)
	{
		if (num % 2 == 1)
			count++;
		num = num / 2;
	}
	printf("%d\n", count);
	return 0;
}

//32bit
//num&1==1
//000000000000000000000000000011
//000000000000000000000000000001
//000000000000000000000000000000
//统计num的补码中有几个1
int main()
{
	int num = 0;
	int count = 0;
	scanf("%d", &num);//-1
	int i = 0;
	for (i = 0; i < 32; i++)
	{
		if (1 == ((num >> i) & 1))
			count++;
	}
	printf("%d\n", count);
	return 0;
}

int main()
{
	int num = -1;
	int i = 0;
	int count = 0;//计数
	while (num)
	{
		count++;
		num = num&(num - 1);
	}
	printf("二进制中1的个数=%d\n", count);
	return 0;
}


//赋值操作符
int main()
{
	int weight = 120;//体重
	weight = 89;//不满意就赋值
	double salary = 10000.0;
	salary = 20000.0;//使用赋值操作符赋值
	return 0;
}

int main()
{
	int a = 0;
	int x = 10;
	int y = 20;
	a = x = y + 1;//连续赋值
	return 0;
}

//复合赋值符
int main()
{
	int x = 10;
	x = x + 10;
	x += 10;//复合赋值
	//其他运算符一样的道理。这样写更加简洁。
	return 0;
}

int main()
{
	int a = 10;
	a = a + 2;
	a += 2;

	a = a >> 1;
	a >>= 1;

	a = a & 1;
	a &= 1;
	return 0;
}

//单目操作符
int main()
{
	int a = 0;
	if (a)
	{
		printf("hehe\n");
	}
	if (!a)
	{
		printf("hehe\n");
	}
	printf("%d\n", !a);
	return 0;
}

int main()
{
	int a = -5;
	a = -a;
	return 0;
}

int main()
{
	int a = 10;
	int* p = &a;//取地址操作符
	*p = 20;//解引用操作符
	return 0;
}

int main()
{
	int a = 10;
	char c = 'r';
	char* p = &c;
	int arr[10] = { 0 };
	//sizeof计算的变量所占内存空间的大小，单位是字节
	
	printf("%d\n", sizeof(a));//4
	printf("%d\n", sizeof(int));//4
	printf("%d\n", sizeof(c));//1
	printf("%d\n", sizeof(p));//4
	printf("%d\n", sizeof(arr));//40
	return 0;
}



