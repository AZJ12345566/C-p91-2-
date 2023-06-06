# C-p91-2-
C语言学习笔记 p91 函数与递归(2)
#include<stdio.h>
#include<string.h>
//函数递归：一个过程或函数在其定义或说明中有直接或间接调用自身的一种方法,它通常把一个大型复杂的问题层层转化为一个与原问题相似的小问题来求解，将大事化小
int main()
{
    printf("hehe\n");
    main();
    return 0;
}//这种递归走着走着就挂了，因为会栈溢出，这种错误非常常见，因为栈内存被耗干了

//内存会划分几个区域：栈区(局部变量、函数形参)，堆区(动态开辟的malloc，calloc)，静态区(全局变量，static修饰的变量)

void print(int n)
{
    if(n>9)
        {
            print(n/10);
        }
        printf("%d",n%10);
}
int main()
{
    unsigned int num=0;
    scanf("%d",&num);
    //递归
    print(num);
    return 0;
}

//因此，递归必须满足两个条件：
//1.存在限制条件，当满足这个限制条件的时候，递归不再继续
//2.每次递归调用之后越来越接近这个限制条件

int my_strlen(char* str)
{
    int count=0;
    while(*str!='\0')//这个*str的意思是通过char* str找到的一个字符
    {
        count++;
        str++;
    }
    return count;
}
//递归方法将大事化小法，不用临时变量来解决
int my_strlen(char* str)
{
    if(*str!='\0')
        return 1+my_strlen(str+1);
    else
        return 0;
}
//思维
//my_strlen("bit");
//1+my_strlen("it");
//1+1+my_strlen("t");
//1+1+1+my_strlen("\0");
int main()
{
    char arr[]="bit";
    int len=my_strlen(arr);//arr是数组，数组传参，传去的不是整个数组的地址，而是第一个元素得地址
    printf("len=%d\n",len);
    return 0;
}







