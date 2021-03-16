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

### 9강
```
#include <iostream>


class Point  // class 는 기본적으로 default = private :외부참조 불가
{
public:    //: 외부참조 가능
	int x, y;
	Point(int a, int b) : x(a), y(b) {}
	Point() {} // null 생성자
	int GetX() { return x; }
	int GetY() { return y; }
	void SetX(int a) { x = a; }
	void SetY(int a) { y = a; }
	// p1=p+n; p1,p:Point n:int => p1.x=p.x+n; p1.y=p.y+n;
	Point operator+(int n)
	{
		Point p1;
		p1.x = x + n; p1.y = y + n;
		return p1;
	}

	Point operator+(Point p) //Point + Point operation
	{
		Point p1;
		p1.x = x + p.x; p1.y = y + p.y;
		return p1;
	}


};

class Rect
{
private: // 없어도 기본적으로 private 이다
	Point p1, p2;  //멤버 변수
public:
	Rect(Point pp1, Point pp2) :p1(pp1), p2(pp2)
	{// 함수의 local변수와 같으므로 ' Point pp1, Point pp2 ' 멤버변수가 아니다 
//		p1 = pp1, p2 = pp2 ; // class변수의 대입문
	}
	Rect() :p1(0, 0), p2(0, 0) {} //Rect(Point &pp1,Point &pp2)


	//int GetX() { return p1.x; }
	//int GetY() { return p1.y; }
	//void SetX(int a) { p1.x=a; }
	//void SetY(int a) { p1.y=a; }

	void SetP1(Point p) { p1 = p; }
	void SetP2(Point p) { p2 = p; }

	int GetX() { return abs(p1.x - p2.x); }
	int GetY() { return abs(p1.y - p2.y); }


	int area()
	{
		int x = p1.x - p2.x;                //멤버 변수가 아니다.
		int y = p1.y - p2.y;
		return abs(x * y); // abs 절댓값
	}
};

//Point 클래스와 Rect 클래스는 은닉되어 있음.
//공개된 정보는 Point 생성자와 Rect 생성자가 알려져 있음.
// Rect  클래스에는 사각형의 면적을 구하는 area 함수가 존재
// 
// ----> Rect의 대각선 길이를 구하는 Distance 함수가 필요함
// dist = sqrt(x*x + y*y)

class RectEx : public Rect // Rect class를 상속 private
{
	int a;
public:
	RectEx(Point pp1, Point pp2) : Rect(pp1, pp2)
	{
		//SetP1(pp1); SetP2(pp2);
	}
	double Distance()
	{
		int x = GetX();
		int y = GetY();
		return sqrt(x * x + y * y);
	}
};
// Circle 클래스를 정의 하고 멤버 함수를 구현하세요.
// Member Function : 지름(diameter) , 원둘레(CLen) , 원면적(Carea)
// *******단 , Rect 클래스를 상속받아서 구현하세요 *****
// Rect 의 두 점을 지름으로 하는 원(Circle) 정의
#define PI 3.14159265
class Circle : public Rect
{
private:
	Point cp;
	double rad;
public:  // 위에 private 부분이 주어져서 초기화하는 작업이 필요하다.
	Circle(Point pp1, Point pp2, Point pp = { 0,0 }) : Rect(pp1, pp2), cp(pp)
	{
		cp.SetX((pp1.x + pp2.y) / 2);
		cp.SetY((pp1.x + pp2.y) / 2);
		int x = GetX();
		int y = GetY();
		rad = sqrt(x * x + y * y) / 2;
	}
	double dia()
	{
		return rad * 2;
	}
	double CLen()
	{
		return rad * 2 * PI; // dia()*PI 랑 똑같지만 좀더 느리다
	}
	double Carea()
	{
		return rad * rad * PI;
	}




};
/* //내가한거 고쳐야함
class Circle : public Rect
{
public:

	Circle(Point pp1, Point pp2) : Rect(pp1, pp2)
	{

	}
	double diameter()
	{
		int x = GetX();
		int y = GetY();
		return sqrt(x * x + y * y);
	}

	double CLen()
	{
		int x = GetX();
		int y = GetY();
		return 2 * pi * sqrt(x * x + y * y);

	}

	double Carea()
	{
		int x = GetX();
		int y = GetY();
		return pi * sqrt(x * x + y * y) * sqrt(x * x + y * y);
	}

}; */

int func1(Rect* r);
int func2(Rect& r);
int func3(Circle& c1);
int main()
{
	int n1 = 10, n2 = 20;
	Point p1(n1, n1), p2(n2, n2);


	//	Rect r1 = { {10,10},{20,20} }; //struct type 초기화
	Rect r1(p1, p2);  //Rect class 생성자 이용 초기화
	Rect r2;


	Circle c1(p1, p2);

	func1(&r1); // func1(r1) 로 하면안된다 포인터 변수 전달을 위해 변수(클래스)의 주소 전달

	func2(r1); // reference 타입은 그냥 변수명 전달


	printf("main 함수 r1: 두점 p1(10, 10), p2(20,20)로 구성되는 사각형의 면적은 %d 입니다.\n"
		, r1.area());
	printf("main 함수 r2: 두점 p1(10, 10), p2(20,20)로 구성되는 사각형의 면적은 %d 입니다.\n"
		, r2.area());

	func3(c1);


	p1.SetX(15); p1.SetY(15);
	Point p3 = p1 + 10;

	printf("Point 클래스의 연산자 오버로딩 테스트1 (+) : p1(%d,%d) + %d ---> (%d,%d) \n", p1.x, p1.y, 10, p3.x, p3.y);

	Point p4 = p1 + p3;
	Point* p5= &p4;
	printf("Point 클래스의 연산자 오버로딩 테스트2 (+) : p1(%d,%d) + p3(%d,%d) ---> (%d,%d) \n", p1.x, p1.y, p3.x, p3.y,p4.x,p4.y);

	printf("Point 클래스의 연산자 오버로딩 테스트2 (+) : p1(%d,%d) + p3(%d,%d) ---> (%d,%d) \n", p1.x, p1.y, p3.x, p3.y, p5->x, p5->y);

}

int func1(Rect* r)
{
	printf("*r 을 이용: 두점 p1(10, 10), p2(20,20)로 구성되는 사각형의 면적은 %d 입니다.\n"
		, r->area());  // 포인터를 이용했으므로 r1.area()로 하면 안된다.

	return 0;
}

int func2(Rect& r)
{
	printf("&r 을 이용: 두점 p1(10, 10), p2(20,20)로 구성되는 사각형의 면적은 %d 입니다.\n"
		, r.area());  // 포인터를 이용했으므로 r1.area()로 하면 안된다.

	return 0;
}

int func3(Circle& c1)
{
	printf("--------------원-----------------\n");
	printf(" 두점 p1(10, 10), p2(20,20)로 구성되는 원의 면적은 %.2lf 입니다.\n", c1.Carea());
	printf(" 두점 p1(10, 10), p2(20,20)로 구성되는 원의 지름은 %.2lf 입니다.\n", c1.dia());
	printf(" 두점 p1(10, 10), p2(20,20)로 구성되는 원의 둘레는 %.2lf 입니다.\n", c1.CLen());

	return 0;
}


[ Reference ]

num1;
&num2=num1;
num2=500;
--> num1=500 , num2=500 이 된다.

[ call by value  VS  call by reference ]

void swap(int n1,int n2)
{
  int temp = n1;
  n1 = n2;
  n2 = temp;
} // value  오류

void swap(int *n1,int *n2)
{
  int temp = *n1;  // ?
  *n1 = *n2;
  *n2 = temp;
} // reference

[ Reference 를 이용한 call by reference ]

적용
int main()
{
  int val1=10, val2=20;
  swap(val1,val2);
}
void swap(int &n1,int &n2)
{
  int temp = n1;
  n1 = n2;
  n2 = temp;
} //call by reference

---> * 대신 & 로 바꿔주면 ,  *(a+1) 대신 a 를 써준다.


[ c++ 에서의 구조체 ]

SoSimple ( int n1, int n2) : num1(n1) , num2(n2)  //--> num1=n1 ,num2=n2; 랑 같은거다.
{ }







```


### WEEK3 10강 03/15

```
SDK 프로그램 동작원리

이벤트 발생
 : mouse ,KBD , network-> waiting , timer


파일  OPEN
속성 : ID : ID_FILEOPEN


switch ID_FILEOPEN:

dialog 삽입

캡션 Dialog 테스트

VISUAL 설치
ASP


C++
최신 MFC
밑에 빌드도구용 2개

만들기
MFC 애플케이션
-> 단일문서 , MFC standard  
오른쪽 리소스뷰 dialog 삽입 -> edit control  ,button ,static text

MSDN

안드로이드 앱 개발자
https://brunch.co.kr/@imagineer/94
```

### 11강 3/16

```
캡션: 이름을 바꿀수있다.


다이얼로그 테스트
메뉴에서 만들고
캡션 테스트(&T)
캡션 테스트(&T)\tCtrl+T

ID_MNU_Test1


이벤트 처리기 
CMFCAppl 3 app 
command
onmuu

클래스뷰에 있는
MFCApplication3
마법사 생산 OnInitDialog


IDD_DLG_DrawTest
IDD_CDrawTest

```
ai 전시회
http://www.aiexpo.co.kr/page/sub1_1

정보처리기사
https://blog.naver.com/iwebmania/222211324338

https://learnjs.vlpt.us/basics/05-function.html

