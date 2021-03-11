# IoT
IoT
### WEEK2 8강

```
//CR : carriage return [Enter] 이용한 프로그램
// ".........." 문자열을 출력하고 숫자키를 이용하여
// 해당 위치의 문자만 ' |' (vertical bar) 문자로 출력하는 프로그램 (동일라인에 출력)
// ex)  '3' 입력 -> ..|.....   피아노 프로그램 
 

#include <stdio.h>
#include <conio.h>

int main()
{
	
	int i,j,k;
	
	char *str= "............";    
    char line = '|';
	
	while(1)
	{
		k=getch()-48; // 0~9 : 30h~39h  = 48~57
		if(k<0 || k>9) break;
		for(i=0;i<10;i++)
		{
			if(i==k) printf("%c",line);
			else printf("%c",*(str+i));
		}
		printf("\r");
		
	}
	
 } 








[ c++ ]

c ++ : class
c : struct

#include <iostream> 

std::cout <<;출력대상1'<<'출력대상2'<<'출력대상3';
->> c++ console 프로그램 할때 쓴다.

std::endl 을 출력하면 개행이 이뤄진다.

F11 F10 핫키를 이용해 디버깅 하는게 유용하다

Ctrl + k + c 주석처리
Ctrl + k + u 주석처리 빼기


함수 오버로딩
예시
int MyFunc(char c)   ----> O
int MyFunc(int n)

int MyFunc(int n)     ----> O
int MyFunc(int n1,n2)

void MyFunc(int n)   ----> X
int MyFunc(char c)


int MyFuncTwo(int n1=5, int n2=7)
{
   return n1+n2;                             
}                                                    


 int MyFuncTwo( );
 int MyFuncTwo(5,7);   같은거다

하지만 부분적 디폴트 값 설정에 의해서
생략가능 부분은 뒤로 가야한다.
ex) int MyFuncTwo(int c, int d, int a=5, int b=7); O
    int MyFuncTwo(int a=5, int b=7, int c, int d); X


[namespace]

namespace BestCom
{
	void Simple(void)
	{
		std::cout<<"BestCom"<<std::endl;
	}
}

namespace ProCom
{
	void Simple(void)
	{
		std::cout<<"ProCom"<<std::endl;
	}
}

BestCom::Simple();

ProCom::Simple();    둘이 아예 다른것이다

프로젝트의 진행에 있어서 발생할수있는 이름의 충돌을 막을 목적으로 존재하는것이 namespace다.

[using 을 이용한 namespace]

using namespace std;


c++ 의 표준헤더: c를 더하고 h를 빼라

#include <stdio.h> -> #include <cstdio>


생성자
  : 클래스의 이름과 동일한 이름의 함수이면서 반환형이 선언되지않았고 
    실제로 반환하지 않는 함수를 가리켜 생성자라한다.



#include <stdio.h>
#include <iostream>


class Point{          //stuct Point 처음에 썻엇음
public:
    Point(int a, int b)
    {
        x = a; y = b;
    }
    ~Point() { delete ppp; }  // 소멸자 : 동적할당후에는 지워줘야한다.
private:
    int* ppp;
public:  // class 외부 참도 가능하도록 해주는 명령어   // public: 있는 위치부터 적용 
    int x;
    int y;
    int* Pointfunc()
    {
        ppp= (int*)malloc(100);
        return ppp;
    }
};

class Rect {
private:
public:
    Rect(Point pp1, Point pp2)
    {
        p1.x = pp1.x;
        p1.y = pp1.y;
        p2.x = pp2.x;
        p2.y = pp2.y;
        p13.x = pp1.x;
        p13.y = pp2.y;
    }
    Point p1;
    Point p2;
    Point p13;
    int area() // x*y : 두점으로 이루어진 사각형의 넓이
    {
        int x = p2.x - p1.x;
        int y = p2.y - p1.y;
        return x * y;
        
    }
    
    double distance(); //distance : 두점사이의 거리
    /*{
        int a = p2.x - p1.x;
        int b = p2.y - p1.y;
        int A = a * a;
        int B = b * b;
        return sqrt(A + B);
    }*/
};

class RectEx :Rect  // Rect 의 모든내용을 가져오겠다.
{
    /*
    class Rect의 모든 내용
    */
    Point p3 = { p1.x,p2.y };  // (p1.x,p2.y)
    Point p4 = { p2.x,p1.y };  // (p2.x,p1.y)  p1,p2의 값을 이용
public:
    int tLength()
    {
        int x = p1.x - p2.x;
        int y = p1.y - p2.y;
        return (x * 2 + y * 2);
    }
};


double Rect::distance() //distance : 두점사이의 거리
{
    int x = p2.x - p1.x;
    int y = p2.y - p1.y;

    return sqrt(x*x + y*y);
}



int main()
{
    /*std::cout << "Hello World!\n";
    printf("printf 문자\n");*/

    Point p1(10,10), p2(20, 20);

    Rect r1 = { p1, p2 }; //Rect r1 = { {10,10}, {20,20} };


 //   RectEx r2 = { {10,10}, {20,20} };
    //r1.p1.x = 15;
    //r1.p1.y = 15;
    printf("두점 p1(10, 10), p2(%d,%d)로 구성되는 사각형의 면적은 %d 입니다\n."
    ,r1.p2.x,r1.p2.y,r1.area());

    printf("두점 p1(%d, %d), p2(%d,%d) 사이의 거리는 %.2f 입니다.\n"
       ,r1.p1.x, r1.p1.y , r1.p2.x, r1.p2.y, r1.distance());

 //   printf("두점 p1(%d, %d), p2(%d,%d) 로 구성되는 사각형의 둘레는 %.2f 입니다.\n"
 //       , r2.p3.x, r2.p3.y, r2.p4.x, r2.p4.y, r2.tLength);

}
```
