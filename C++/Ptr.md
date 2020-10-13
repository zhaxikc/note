```c++
#ifndef ND_H
#define ND_H
class ND
{
public:
	ND(int =2000, int =1, int =1);            //初始化变量
	ND& setyear(int);                         //返回变量的引用
	ND& setmonth(int);                        //返回变量的引用
	ND* setday(int);                           //返回变量的指针
	ND setND(int,int,int);                     //临时变量的赋值
	void display();
private:
	int y,m,d;
};
#endif

#include<iostream>
using namespace std;
#include"ND.h"
ND::ND(int newy,int newm,int newd)
{
	y=newy;                          //this->y=newy
	m=newm;                          //this->m=newm
	d=newd;                          //this->d=newd
}
ND& ND::setyear(int year)             //返回当前对象的引用（本身）？
{
	y=year;
	return *this;                   //这里返回当前对象本身，返回的是y的值，y原地址储存值是2000，这里把year值赋给y，this依旧指向y的地址。
}
ND& ND::setmonth(int month)         //
{
	m=month;                  
    return *this;             
}
ND* ND::setday(int day)              //返回的是当前对象的指针（地址）
{
	d=day;                         
	return this;
}
ND ND::setND(int x,int y,int z)
{
	ND tmp;                          //定义的是临时变量
	tmp.y=x;                           //?????????
	tmp.m=y;
	tmp.d=z;                         
	return tmp;                       //这里return前面是到copy函数里进行备份
}
void ND::display()
{
	cout<<"address is:"<<this<<"\t"<<y<<":"<<m<<":"<<d<<endl; //这里的this是地址  
}

#include<iostream>
using namespace std;
#include"ND.h"
int main()
{
	ND x1,x2;          //这里x1,x2是初始化变量里的值
	cout<<"x1";
	x1.display();       //地址不同，这是肯定的！
	cout<<"x2";
	x2.display();
x1.setyear(2007).setmonth(3).setday(30);       //
cout<<"x1";
x1.display();

x1.setND(2000,1,10).setday(30);                 //？？？？？？？？？？										cout<<"x1";
x1.display();
	
x1.setND(2000,1,10).setday(15);                 //？？？？？？？？？？
cout<<"x1";
x1.display();

ND *p;                                         //   ?
p=x1.setday(21);
cout<<"p";
p->display();                                 //    ?

ND x3=x2.setyear(2006).setmonth(4);
cout<<"x3";
x3.display();
getchar();
return 0;
}
```

![image-20201013095650809](https://raw.githubusercontent.com/privking/king-note-images/master/img/note/image-20201013095650809-1602554211-d4c6a5.png)