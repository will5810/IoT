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



###12강 3/17
```

[ C# ]
형식 안정 객체지향언어
기존 언어들의 생산성을 개선하고 성능이 좋아짐

닷넷 프레임워크( . NET Frame work)

기본자료형 
int (4) , long (8) , float (4) , double (8) 
, char (C# 에ㅅ는 2Byte) , string ,bool

자료형 변환 메서드
문자열 -> 숫자	int Parse() , double Parse()
다른 자료형 ->	ToString()
문자열 -> 불	bool.Parse()

키입력 메서드
ReadKey()


VISUAL

윈도우스 FORMS 앱
솔루션 탐색기
FORM1.Designer.cs
label , button t, textbox 만들고 ,속성 조절후
버튼 더블클릭후 코드작성

namespace WindowsFormsApp1
{
    public partial class Form1 : Form
    {
        int status = 0;
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            if(status==0)
            {
                button1.Text = "버튼 테스트1";
                status = 1;
            }
            else
            {
                button1.Text = "버튼 테스트2";
                status = 0;
            }

        }
        
    }
}


c++ 에서 status = !status; 하면 가능했지만 
c# 에서는 

namespace WindowsFormsApp1
{
    public partial class Form1 : Form
    {
        bool status = false;
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            if(status)
            {
                button1.Text = "버튼 테스트1";
          
            }
            else
            {
                button1.Text = "버튼 테스트2";
    
            }
            status = !status;
        }
        
    }
}
bool 을 붙여줘야한다

속성창에서 바꿔줘야한다. 그래야 다른것도 같이 수정되므로

도구창에서 OpenFileDialog 드래그해준다.
 
잘못 더블클릭했으면 속성창 번개 모양에서 지워주고 확인해주면 된다

도구창에 있는거 다른거 해보기

```


### 13강 3/18

```
[ C# ]

C++
MyClass dlg;
MyClass *dlg=new MyClass();
dlg->member;

C#
MyClass dlg=new MyClass();
dlg.meber


try , catch , finally


------------------------------------------
StreamReader sr; 할때는 빨간줄이 나오는데
이럴때 마우스를 위에올려놓고 using 을 누르면 위에 using System.IO; 부분이 활성화된다.

Anchor :  안에 텍스트 박스 사이즈를 Form 창하고 같이 비례로 조절할때 쓰인다

WordWrap : 자동 줄바꿈
```

### 14강 3/19

```

업로드 자료보기

```

### WEEK4 15강 3/22
```
1. Mouse 의 왼쪽 버튼 클릭시 그리기 Start
  -현재의 Point 값을 저장
2. Mouse 의 이동에 따라 발생하는 Move event 에서 Line Draw , 현재의 값을 재 저장
3. (2)번 동작을 반복
4. Mouse 의 왼쪽 버튼이 해제되면 그리기 stop



[SQL]
select 기본 구문

조건문에서 SQL 은 A와B가 같다라고 할때  ' = ' 하나만 쓴다.

DB 시작
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.IO;



namespace WindowsFormsDBManager
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void btnInput_Click(object sender, EventArgs e)
        {
            string str = tbInput.Text;
            dbGrid.Columns.Add(str, str); //먼저 열을 추가해야한다.
            dbGrid.Rows.Add();
        }

        private void btnValue_Click(object sender, EventArgs e)
        {
            string str = tbValue.Text;
            dbGrid.Rows[1].Cells[2].Value = str;
            
        }

        private void btnOpen_Click(object sender, EventArgs e)
        {
            DialogResult ret = openFileDialog1.ShowDialog();
            if (ret == DialogResult.OK)
            {

                string fName = openFileDialog1.FileName;



                StreamReader sr = new StreamReader(fName);
                string buf = sr.ReadToEnd();
                dbGrid.Text = buf;
                sr.Close();
            }
        }
    }
}


namespace myLibrary
{
    class myLib
    {
        public static int Count(char deli, string str) //str 문자열 deli 구분자의 개수 +1
        {
            string[] Strs = str.Split(deli);
            int n = Strs.Length;
            return n - 1;
        }
        public static string GetToken(int index, char deli, string str)
        {
            string[] Strs = str.Split(',');
            string ret = Strs[index];
            return ret;

        }

    }

}

```
###  16강 3/23

```
1. file select
2. open and read
3. grid header gen
4. record append
5. input to cell


Visual DB 만들기

서버탐색기 -> 데이터연결 우클릭 -> 연결추가 , Micro SQL Server 파일 클릭후 만들기

열 : field 행 : record

mnuStrip 에서 DB 열기 만들기
똑같이 OpenFileDialog 열기 하고
데이터베이스 연결 문자열 복사후에


 SqlConnection sqlCon;
sqlCon.ConnectionString = " " 안에 넣어준다.
근데 여기서 '\' 하나이기때문에 '\\' 처럼 두개만들어줘도 되고
@" " 이처럼 앞에 '@' 를 붙여줘도 된다.



update fStatus set Temp=13 where id=2

insert into fstatus values(100004,15,72,4)

```


###  17강 3/24

```

[ SQL ]

update fstatus set temp=23 where id=6
-> id=6 인곳에 temp=23 으로 바꿔라
만약 update fstatus set temp=23  이렇게 쓰면
-> 모든 temp=23 이 되고 복구가 안되므로 조심하자

### select * from fstatus   --> 데이터를 보여준다.

### insert into fstatus values(100004,15,72,4)  --> 삽입

### tbSql (텍스트박스) 안에 테이블 데이터를 나타내라

        public static string GetToken(int index, char deli, string str)
        {
            string[] Strs = str.Split(deli);
            //int n = Strs.Length;
            string ret = Strs[index];
            return ret;

        }

GetToken 을 만들고

        int RunSql(string sql)
        {
            try
            {
                sqlCmd.CommandText = sql; // insert into fstatus values (1,2,3,4) 
                if (GetToken(0,' ',sql).ToUpper()=="SELECT")  // ToUpper로 대문자로 만들어줬으므로 걱정 없다
                {

                    SqlDataReader sr = sqlCmd.ExecuteReader();

                    for (int i=0;sr.Read();i++)
                    {
                        string buf = "";
                        for(int j=0;j<sr.FieldCount;j++)
                        {                           
                            object str = sr.GetValue(j);
                            buf += $" {str}";                                               
                        }

                        tbSql.Text += $"\r\n{buf}";                                                                   
                    }

                    sr.Close();  //종료 시켜주어야한다
                }

	else
	{
	}
       }

추가해준다.


### GridView 안에 테이블 데이터를 나타내라

GetToken 을 이용하여

        int RunSql(string sql)
        {
            try
            {
                sqlCmd.CommandText = sql; // insert into fstatus values (1,2,3,4) 
                if (GetToken(0,' ',sql).ToUpper()=="SELECT")  // ToUpper로 대문자로 만들어줬으므로 걱정 없다
                {

                    dataGrid.Rows.Clear();   // 따로 행과열을 Clear 해줘야한다.
                    dataGrid.Columns.Clear();
                    SqlDataReader sr = sqlCmd.ExecuteReader();

                    for (int i = 0; i < sr.FieldCount; i++)   // Header 처리 프로세스 //
                    {
                        dataGrid.Columns.Add(sr.GetName(i), sr.GetName(i));
                    }


                    for (int i = 0; sr.Read(); i++)
                    {
                        int rIdx = dataGrid.Rows.Add();
                        for (int j = 0; j < sr.FieldCount; j++)
                        {
                            object str = sr.GetValue(j);
                            dataGrid.Rows[rIdx].Cells[j].Value = str;
                        }
                    }

                    sr.Close();
                }
	else
	{
	}
       }
     


### delete fstatus where id=3  --> id=3 인곳을 지워준다.


### 텍스트박스에서 키보드 Enter 눌러주면 바로바로 실행

        private void tbSql_KeyDown(object sender, KeyEventArgs e)
        {
            if (e.KeyCode != Keys.Enter) return;

            string str = tbSql.Text;
            string[] sArr = str.Split('\n'); // 줄바꿈문자 :\r\n
            int n = sArr.Length;
            string sql = sArr[n - 1].Trim();

            RunSql(sql);

        }


```


###  18강 3/25

```
과제1)
statusStrip 안에 sbPanel3 를 클릭하면
"select * from fstatus" 처럼 바로 나오게 만들어라

==>
        private void sbPanel3_Click(object sender, EventArgs e)
        {
            //string sql = s1.Trim(); 
            //sqlCmd.CommandText = sql;  
            //TableName = GetToken(3, ' ', sql);

            //sbPanel3.Text = TableName;
            string s = $"select * from {sbPanel3.Text}";

            RunSql(s);
        }


 string sql = s1.Trim(); // Trim : 앞뒤 공백을 없앤다. (중간 공백은 빼고)

[ DB 닫기 ]

        private void mnuDBClose_Click(object sender, EventArgs e)
        {
            sqlCon.Close();


            sbPanel1.Text = "DB File Name";
            sbPanel1.BackColor = Color.Gray;
            sbPanel2.Text = "DB Closed";

            // sqlCon
        }

[ Column , Row 추가 ]


Row는 상관없지만 Column 은 이름을 만들어줘야한다.


        private void PlusColumn_Click(object sender, EventArgs e)
        {
            frminput dlg = new frminput("input Column");
            DialogResult ret = dlg.ShowDialog();
            if (ret == DialogResult.OK)
            {
                string s = dlg.sinput;
                dataGrid.Columns.Add(s, s);
            }

        }

        private void PlusRow_Click(object sender, EventArgs e)
        {
            dataGrid.Rows.Add();
        }



[ create ]
create Table fTest
(
  id int,
  fCode nchar(10),
  fLoc nchar(20)
)

과제)
create 를 사용하여
값을 저장하고 새로운 테이블 만들기

새로운 테이블 생성하는 메뉴 만들기

        private void mnuNewTable_Click(object sender, EventArgs e)
        {
            frminput dlg = new frminput("신규 테이블 명");

            if (dlg.ShowDialog() != DialogResult.OK) return;
            string tableName = dlg.sinput;
            string sql = $"Create table {tableName}(";


            for (int i = 0; i< dataGrid.ColumnCount; i++) //dataGrid.ColumnCount == dataGrid.Columns.Count
            {
                sql += $"{dataGrid.Columns[i].HeaderText} nchar(20)";
                if (i < dataGrid.ColumnCount - 1) sql += ", ";
            }
            sql += ")";

            RunSql(sql); // 신규 테이블 생성 완료

            // insert into [TableName].values (
            // [col_val_1],[col_val_2],...
            // )

            for(int i=0;i<dataGrid.RowCount;i++)
            {
                sql = $"insert into {tableName} values (";
                for(int j=0;j<dataGrid.Columns.Count;j++)
                {
                    sql += $"'{dataGrid.Rows[i].Cells[j].Value}'";
                    if (j < dataGrid.ColumnCount - 1) sql += ",";
                }
                sql += ")";
                RunSql(sql);
            }

        }

```

### 5/3
```
MVC

데이터 테이블 만들고
Models -> 추가 -> 새항목 -> 클래스 추가

prob tab tab

WebApp 추가 -> 새폴더 -> context -> 
context추가 -> 클래스 생성

DbContext -> 잠재적 추가사항에서 업데이트해도 되고
               -> 도구 -> NuGet 패키지관리자-> 찾아보기 -> EntityFramework

Controllers 추가 ->컨트롤러 -> 뷰가 포함된 추가 
 -> user (WebApplication1.Models) -> userinfo (WebApplication1.Context)

Controllers 추가 -> Fac (WebApplication1.Models)


HomeController 코드에
        public ActionResult Login()
        {
            ViewBag.Message = "Your login page.";

            return View();
        }
추가

Views -> Home -> 추가 -> 레이아웃이있는 MVC 5뷰 Login 만들기
->코드 추가

<div class="jumbotron">
    <h1>Login</h1>
    <form asp-controller ="Home" asp-action="Login"
          <p>
              <input id="Text1" type="text" name="UID" /><input id="Submit1" type="submit" value="Login" />
          </p>
              <input id="Text2" type="password" name="PWD"/>
    </form>
</div>

(WebApplication 속성에서 특정페이지 선택)

비민번호는 원문을 비교하는게 아니라
암호문을 비교하는것이다.



```
### 5/4
```
암호화 과정

쿠키 
 :인터넷 웹 사이트의 방문 기록을 남겨 사용자와 웹 사이트 사이를 매개해 주는 정보.

account == 1 일때만
사용자관리 할수 있도록

데어터 연결

제어판>모든제어판 항목>프로그램 및 기능>
> Windows 기능 켜기 -> 인터넷정보서비스(안쪽 FTP서버 빼고) 다 켜기 2개 다

IIS(Internet Information Service)
```

### 5/13
```
cat config.txt
ifconfig

Vi editor : vi 편집기

# : root 권한
$ : user 권한

user 홈 디렉토리

sudo( Super User 로 do(실행))
apt 패키지 다운로드      // update,upgrade 가장최신버전
sudo apt-get update      
sudo apt-get upgrades

sudo apt-get upgrades
딸기-> 기본설정-> add/remove software(1)
검색창 korea -> korean font 선택
sudo apt-get install ibus ibus-hangul
reboot

sudo raspi-config  

sudo passwd : root

apt-get install samba samba-common-bin


d/rwx/rwx/rwx/ 
d: directory
7/7/7  = 111/111/111
권한을 나타내준다 


cd :current directoy

cd / : change directory root로
ls : 
ls -al : 전체적인 

[pi] 
  path=/home/pi/Work
  writeable=Yes
  create mask=0777
  directory mask=0777
  pubic=no
```

### 5/14 
```
RaspberryPi

$ : 일반 user을 나타냄
pwd : 현재 디렉토리가 어딘지
ls : 파일의 리스트를 볼수있음
ls -al : 더많은 파일의 정보를 볼수있음 권한등등..

sudo smbpasswd -a pi  : sudo 권한으로 smb 비밀번호 append한다.
ifconfig : 라즈베리파이에서 IP 보는법


sudo systemctl restart smbd        : d :demon
아무 대답없으면 잘나온거다

cd /etc/wpa_supplicant :
cat wpa_supplicant.conf :  네트워크 상태보기

.. : 상위 Folder 로 이동해라
.  : 현재 directory 

ls net*
cd network : network로 이동해라

sudo vi interfaces 

[ vi editor] 에서
i : insert 현재 캐럿에 문자삽입
a : append 현재문자 뒤에 붙여줌
작업을 한후 esc 를 무조건 눌러줘야한다
나갈때는 esc 누르고 shift+ :(콜론) 후 q! 입력
x : 한문자만 삭제
dd : 한줄 삭제


[ 라즈베이파이 초기 세팅 작업]

1. SD card format
2. raspbian - OS download
3. SD card에 OS porting
4. RaspberryPi 에 삽입
5. KBD/Mouse/Monitor 설치 (화면 입력으로 전환)
6. 전원인가

-VNC 활성화 : raspi-config (미설정시 최소 해상도 640 * 480)
  [terminal] sudo raspi-config 후 mode 4 60hz 로 바꿈 
-원격 제어 가능한 상태확보 
  raspberry pi configuration-> Interfaces -> SSH VNC 'Enable'로 설정
-Wifi 사용 가능 (고정 IP 미확보 -> 고정 IP설정)
  [terminal] ipconfig로 ip 확인 
 고정IP 설정 :  Wifi 우클릭후-> Wireless Setting -> Configure :SSID ,WIFI 설정
-> 첫번째 Address 192.0 , Router : 뒤에가 1 

7. PC에서 원격접속(VNC Viewer)
   최초 계정 : id=pi ,pwd= raspberry
8. update/upgrade --> 한글 입출력 모듈 설치(ibus)
[terminal]  sudo apt-get upgrade
  	  sudo apt-get upgrade
    	  딸기 -> 기본설정 -> add/remove software(1) -> korea -> 폰트선택
	  sudo apt-get install ibus ibus-hangul
              reboot  
9. samba 설치 --> PC에서 NAS 사용
 파일 Work 추가
[terminal]  apt-get install samba samba-common-bin
              sudo passwd 설정후 -> su  :수퍼유저 권한
              home pi etc samba 들어온후
              nano smb.conf  또는 vi smb.conf 입력
              sudo  
 [pi] 
  path=/home/pi/Work
  writeable=Yes
  create mask=0777
  directory mask=0777
  public=no             
                           
 편집후 -> ^o -> ^x

  sudo systemctl restart smbd
  후에 PC 가서 '\\ IP' 입력후 안에 파일넣기 ( id=pi ,pwd=1(자신이설정한것) )


sudo passwd : 암호설정
su : SuperUser로 들어오기
home pi etc samba 들어온후
nano smb.conf 에서 편집하기
sudo systemctl restart smbd

sudo apt-get remove samba : 모든 samba 지우는거 (에러떳을때 등등)
ibus 설치 했을때도 한글안될때 raspberry pi configuration -> Localisation -> 
 -> Locale -> en, US , UTP-8 으로 설정
 
 ----------------------------------------------------------------------------------
sudo apt-get install gcc : gcc 컴파일러 설치
gcc -v 
make -v
pwd :현재 위치보기
gcc -o hello hello.c : gcc 컴파일 hello라는 이름으로 output 해라
ls -al 했을때  앞에 'x' 는 실행가능여부
파일안에 만들고 누르면 geany 가 켜지고 거기서 c언어로 편집한뒤
현재 디렉토리라도 hello 이렇게만 치면 안되고 ./hello 라고 입력해야한다
```
