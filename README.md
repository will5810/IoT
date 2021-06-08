# IoT
IoT
# C_YunSeo
IoT - SW  developer Class

### WEEK 1
### 1강
```
IoT (Internet of Things) (사물인터넷)
3C: 콘텐츠, 커넥션, 컨트롤

질문? : 그래서 우리는 무엇을 어떻게 준비해야 할까?


프로그래밍 언어
 사람과 컴파일러가 이해할 수 있는 약속된 형태의 언어
 c 언어도 프로그래밍 언어 중 하나

컴파일
 프로그래밍 언어로 작성된 프로그램을 컴퓨터가 이해할 수 있도록 기계어로 번역해 주는 역할

1.Editing
2.Compiling
3.Linking


\a : arlam 경고음 소리 발생
\b : 백스페이스 (backspace)
\n : 개행
\r : 캐리지 리턴
\t : 수평 탭
\v : 수직 탭
\\ : 백슬래시(\)
\' : 작은 따옴표
\'" : 큰 따옴표



%c : 단일문자
%d : 부호 있는 10진 정수
%f : 부호 있는 10진 실수
%s : 문자열
%o : 부호없는 8진정수
%u : 부호없는 10진정수
%x : 부호없는 16진정수,소문자
%X : 부호없는 16진정수,대문자
%e : e표기법에 의한 실수 ( 5.6e+20=5.6*10^20 )
%E : E표기법에 의한 실수 ( 5.6E+20=5.6*10^20 )


1byte = 8 bit = ascii 
           0~255
2byte = 16bit 
           0~65535


변수란?
 데이터를 저장할 수 있는 메모리 공간에 붙여진 이름

다양한 형태(자료형)의 변수
 정수형: char (1byte)   , int , long
 실수형: float , double

char
 unsigned char : 부호무시  따라서 0 ~ 255
 char : -128 ~ 127

int
 4byte=32bit 
```
### 2강

```
변수 선언시 주의사항
 1. 함수와 변수는 사용되기 이전에 선어되어야 한다.
 2. -1 변수의 이름은 알파벳, 숫자 ,언더바(_)로 구성
    -2 대 소문자 구분
    -3 변수의 이름은 숫자로 시작 불가, 키워드 사용불가
    -4 공백이 포함될수 없음


대입 연산자

논리 연산자

자료형 변환의 두 가지 형태 
 -자동 형 변환 (묵시적 형 변환): 자동적으로 발생하는 형 변환
 -강제 형 변환 (강제 형 변환): 프로그래머가 명시적으로 형 변환을 요청하는 형태의 변환

while 문

for 문

switch case 문
```

### 3강
```
[함수]
  반환값이 있을때, 없을때 유의
  
  컴파일러 특성상, 함수는 호출되기 전에 정의 되어야한다.



#include <stdio.h>

int Scan(char k);
int main()
{
	char key;
	
    printf("KEY 값을 입력하시오: ");
   	scanf("%c",&key);
   	Scan(key);
    
    return 0;

}
int Scan(char k)
{
	if(k>='a' && k<='z')
	{
		return printf(":소문자\n");
	}
	else if (k>='A'&&k<='Z')
	{
		return printf(":대문자\n");		 
	}
	else if(k>='0'&& k<='9')
	{
		return printf(":숫자\n");
	 }
	else
	{
	    return printf(": 특수문자\n");
    }
}


한번만 돌렸을 때는 잘 잘동 되지만 

int main()
{
	char key;
	
	
	while(1)
	{
	    printf("KEY 값을 입력하시오(종료:z): ");
	   	scanf("%c",&key);
    	if(key=='z') break;
   	    Scan(key); 	    
	}

   	return 0;

}

이렇게 반복문을 사용하여 돌릴때는 scanf 오류 특성상 엔터키도 같이 포함하기 때문에
한줄 잘 작동되고 다음줄에 특수문자(엔터키)도 같이 찍힌다.
따라서 

if(key!=13) Scan(key); //엔터키 무시

붙여준다

이렇게 만든 함수들은
#include "MyHeader.h" 와 같이 따로 헤더 파일을 만들어 불러준다


변수의 특성에 따른 분류
  지역 변수: 중 괄호 내에 선언되는 변수
  전역 변수: 함수 내에 선언되지 않는 변수
  정적 변수: 함수 내부, 외부 모두 선언 가능

전역변수  
  전역변수는 정적변수라고 봐도 프로그맹하는데 거의 무의미하다.
  동일한 이름의 지역 변수에 의해서 가려지기도 한다. 
   -> 전역 , 지역 함수의 이름이 같으면 에러는 뜨지않고 지역변수 우선이다.
  

[배열]
  둘 이상의 변수를 동시에 선언하는 효과를 지닌다.
  많은 양의 데이터를 일괄적으로 처리해야 하는 경우에 유용하다.
  지역적 특성을 지닐 수도 있고, 전역적 특성을 지닐 수도 있다.

선언과 동시에 초기화
 
   int main()
   {
       int arr1[5]={1,2,3,4,5};
       int arr2[ ]={1,3,5,7,9};
       int arr3[5]={1,2};   //나머지는 쓰레기값
    }



문자열 상수
    -문자열 이면서 상수의 특징을 지닌다.
    printf("Hello World! \n")
문자열 변수
    -문자열의 배열 + NULL
    -문자열이면서 변수의 특징을 지닌다.
    char str1[5]="Good";  // |G|o|o|d|0| 끝에 NULL을 넣어줘야한다. 
    char str2[ ]="mood"; // NULL 까지 합쳐 총 5개 방을 만들어준다.
    char str3[4]={'n','i','c','e'}; //뒤에 NULL 값이 안들어가 있으므로 매우 불안정상태이다.

int main()
{
	char str1[5]="Good";
	char str2[]="morning";
	char str3[4]={'n','i','c','e'}; //뒤에 NULL 값이 안들어가 있으므로 매우 불안정상태이다. 
	
	printf("%s\n",str1);
	printf("%s %s\n",str1,str2);
	printf("%s %s %s\n",str1,str2,str3);
	
	
	
	return 0;
}

// 배열을 이용한 소문자를 대문자로 변환 

void ConvertChr1(char buf[]); //아스키코드 값을 이용
void ConvertChr2(char buf[]); 

int main()
{
	int len=100;
	char buf[len];
	
	
	while(1)
	{
		printf("\n");
		printf("문자열을 입력하시오: "); 
        scanf("%s",buf);
		printf("문자열: %s \n\n",buf); 
		ConvertChr1(buf);
	
    }
}


void ConvertChr1(char buf[])
{
	for(int i;buf[i]!=0;i++) // == for(int i; buf[i]; i++)
	{
		char a=buf[i];
		if(a>96 && a<123) a-=32;
		printf("%c ",a);

	}
		
}
// 위에꺼랑 똑같다. 
void ConvertChr2(char buf[])
{
	for(int i; buf[i]!=0; i++) // == for(int i; buf[i]; i++)
	{		
		if(buf[i]>='a' && buf[i]<='z') buf[i]-=32;
		printf("%c ",buf[i]);
	}
		
}


[2차원 배열]
포인터는 배열이다.

int *a -> *(a+1) 로 받고
char buf[ ] -> buf[1] 로 받을수 있고 서로 바꿔서 쓰는것도 가능하다.

하지만 2차원 배열 부터는 바꿔서 쓰는것이 불가능하다.

//포인터가 찍히는것 
/*
int main(void)
{
	int a[3][2]={ {1,2},
	              {3,4},
				  {5,6} };
	
	printf("%d\n",a[0]); // int 4byte 인데 주소가 8씩차이 난다. -> 2개씩 건너뛰어서  1 ,3, 5 를 가르키므로 
	printf("%d\n",*(a+0));
	
	printf("%d\n",a[1]);
	printf("%d\n",*(a+1));
	
	printf("%d\n",a[2]);
	printf("%d\n",*(a+2));
	
	
	printf("%d %d\n",a[1][0],(*(a+1))[0]);
	printf("%d %d\n",a[1][2],*(a[1]+2));  // a[1][2]= 없기때문에 5가 찍힌다 
	printf("%d %d\n",a[2][1],*(*(a+2)+1));
	
	return 0; 
 } 
*/


int a[2][3] 4바이트
char  1바이트
double 8바이트
이므로 주소값에서 첫번째 자리만 같고, 나머지는 byte 차이만큼 다르다.


[getch 함수]

// 문자열을 입력하고 getch 를 이용하여 몇번째 자리인지 판별하는 프로그램
/*
void Find(int n,char buf[]);


int main()
{
	int len=100;
	char buf[len];
	
	printf("문자열을 입력하시오: "); 
    scanf("%s",buf); // [Enter] 키를 눌러서 값을 되돌림 
	printf("문자열: %s \n",buf); 
	
	while(1)
	{
		printf("\n"); 
		printf("숫자를 입력하시오:");
		char ch = getch(); //단일 키값을 되돌림.
		if(ch<48 || ch>57) break; //숫자가 아니면 종료		
		Find(ch-48,buf); //ch-48: 숫자 키값을 인덱스 값으로 변환	    
    }
    
    return 0;
}


void Find(int n,char buf[])
{
    printf("%s (%d): %c" , buf,n,buf[n-1]); //  buf[n-1] = *(buf+n) 같은거다. 
}
*/



getchar() ,getche() , getch() 의 차이점
링크
https://kcoder.tistory.com/entry/getchar-getch-getche%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EC%98%88%EC%A0%9C%EC%86%8C%EC%8A%A4-%EA%B7%B8%EB%A6%BC

```



### 4강

```
[포인터]

void : 정해지지 않는 주소

&연산자 : 변수의 주소 값 반환
*연산자 : 포인터가 가리키는 메모리 참조



오류2
int *pA=100;  // 100 이 어딘줄 알고? system area


SWAP


char str1[5]="ABCD"; 
char *str2="ABCD"; 

둘이 같은것이다. ABCD


포인터 배열

int  *arr[10] ;  // 1차원 배열처럼 생겼지만 실제로는 2차원배열이다  


값의 복사에 의한 전달
call by value

call by reference


sizeof(arr); // 함수가아니다.(오류) 매크로다. 


포인터가 가리키는 변수의 상수화

int a=10;
const int *p=&a;
*p=30;
a=30;


cast : 형변환
 ex) (double)2


void 형 포인터


char * = string(문자열) 이다.

[구조체]











<typedef 의 적용> : 호환성을 높여준다.
1,2번 같은거다.
1.
struct Data
{
  int data1;
  int data2;
};
typedef struct Data Data;


2.
typedef stuct Data
{
	int data1;
	int data2;
	
}Data;
 
[UNOIN]
  공용체의 특성 : 하나의 메모리 안에 둘이상

[Enum]

#include <stdio.h>

/*
int main()
{
	int aa=2000;
	int a=2005;
	int b=2021;	
	int *pA=&a;
	void *vp;

	printf("%08x \n",pA); //주소값을 16진수표기 
	printf("%08x \n",&a);

	(*pA)++; //a++와 같은 의미 
	
	printf("%d\n",a);
	printf("%d\n",*pA);
	
	vp = pA++; //다음번주소
	  
	printf("%08x \n",pA); 
	printf("%d \n",*pA); 
	printf("%d \n", vp++); 
	printf("%d \n", vp++); 
	
	
	 
	
	
	return 0;
}
*/



/*
int main(void)
{
	int a[5]={0,1,2,3,4};
	double *b={1,2,3,4,5,6,7};
 }
 */ 

// 배열을 이용해 가장 작은수 찾아서 출력 



/*
int Min(int *p,int n);

int main()
{
    int arr[5];
    int min;

    
    printf("숫자를 입력하시오\n");
    
    for (int i = 0; i < 5; i++)
	{
		scanf("%d", &arr[i]);	
	}
	
	min=Min(arr,5);

	
    return 0;
}



int Min(int *p,int n)
{
	
	int min=*p;
	
	for (int i = 0; i < n; i++) 
	{
        if (min > *(p+i)) {   // == min> p[i]
            min = *(p+i);
        }        
    }
 
    return  printf("min = %d\n", min);

}
*/



// 배열정렬 
/*
void swap(int *a);

int main()
{
    int a[5];
    int tmp;
    int i,k;

    
    printf("숫자를 입력하시오\n");
    
    for (i = 0; i < 5; i++)
	{
		scanf("%d", &a[i]);	
	}
	
	    printf("\n\n정렬전 배열 \n");
	for (k=0; k<5; k++)
 	{
  	printf("%d ", a[k]);
 	}
	
	swap(a);
	
 
	printf("\n\n정렬후 배열 \n");
	for (k=0; k<5; k++)
 	{
  	printf("%d ", a[k]);
 	}
 

	
    return 0;
}


void swap(int *a)
{
	
	int tmp;
	
	 for (int j= 1; j< 5; j++)
    {
      for (int i=0; i<5-1; i++)
     {
       if (a[i] > a[i+1])
      {
    
      	tmp = a[i];
    	a[i] = a[i+1];
    	a[i+1] = tmp;
       }  
 	 }
 	}
} 
*/
//두 수를 입력받아 최대공약수를 출력하는 프로그램


/*
int gong(int N,int *arr);
int gongGcd2(int *arr1,int n1,int *arr2,int n2);
int gongGcd1(int n1,int n2);

int main()
{
	int num1,num2;
	int n1,n2;
	int arr1[100],arr2[100];
	int MaxNum; 

    printf("2개의 숫자를 입력하세요.\n");
	scanf("%d %d",&num1,&num2);
	
	n1=gong(num1,arr1);
	n2=gong(num2,arr2);
	
	MaxNum=gongGcd2(arr1,n1,arr2,n2);
	
	printf("%d의 약수는: ",num1);
	for(int k=0; k<n1 ;k++)
	{
	printf("%d ",arr1[k]);
	}
	printf("\n");
	printf("%d의 약수는: ",num2);	
	for(int k=0; k<n2;k++)
	{
	printf("%d ",arr2[k]);
	}

    
    printf("\n%d와 %d의 최대공약수는 %d입니다.\n",num1,num2,MaxNum);
 
	return 0;
 } 
 
 
int gong(int N,int *arr)
{
	int count=0;
    int i;
    for (i = 1; i <= N; i++)
    {
        if ((N % i) == 0)
        {
            arr[count] = i;  // *(arr)=i;
            count++;  // arr++;
        }
        else
            continue;
    }
    
    return count;
    
}

int gongGcd2(int *arr1,int n1,int *arr2,int n2)
{
	int i,j,k;
	
	for(i=n1-1; i>=0;i--)
	{
		for(j=0;j<n2;j++)
		{
			if(*(arr1+i)==*(arr2+j)) return *(arr1+i);
		}
	}
	
	return -1;  // 뭔가 잘못됐음 
}


int gongGcd1(int n1,int n2)
{
	int i,j,k;
	
	for(i=n1;i>0;i--)
	{
		if(n1%i==0 && n2%i==0) return i;
	}
}

*/

#include <stdio.h>

struct person{
	char name[20];
	char phone[20];
};
int main()
{
	struct person man={"as","02020"};
	struct person *pMan;
	pMan=&man;
	
	printf("name :%s\n",man.name);
	printf("phone:%s\n",man.phone);
	
	printf("name :%s\n",(*pMan).name);
	printf("phone :%s\n",(*pMan).phone);
	
	printf("name :%s\n",pMan->name);
	printf("phone :%s\n",pMan->phone);
	
			
	return 0;
		
}
```
### WEEK 2
### 5강
```
// 아스키코드 만들기 (내가 한 방식) 
// DEC 7,8,9,10,13 는 예외처리 --> " " 
/*
int main()
{
	int i,j,k;
	int n=k+j;

	for (int i=0;i<4;i++)
	{
		printf("10	|HEX	|문자	|");
	}
	printf("\n");
	
	for (k=0;k<32;k++)
	{
		for(j=0;j<4;j++)
		{
			n=j*32 + k;
			if(n>=7&&n<=10 ||n==13)
			{
				printf("%3d	|%02X	|	|",n,n);
			}
			else
			{
			printf("%3d	|%02X	|%c	|",n,n,n);
		    }
		}
		printf("\n");
	}
	
	return 0;
}
*/


// 아스키코드 만들기  (강사님 방식) 
// DEC 7,8,9,10,13 는 예외처리 --> " " 
/*
int main()
{
	int i,j,k,m,m1,p;
	int n=4;
	k=(128-1)/n + 1; // (출력 갯수-1)/ n +1 
	 

	printf("\n");
	
	for(i=0;i<k;i++)
	{
		for(j=0;j<n;j++)  //for(j=i;j<128;j+=k)
		{
			m1=m=i+j*k;
			if(m>=7&&m<=10 || m==13) m1= 0x20;			
			if(m<128) printf("%3d [%02x] : %c  	",m,m,m1);
		}
		printf("\n");
	}
	
	return 0;
}
*/

// 정렬 sorting

void swap(int *a,int *b);
int sorting(int *array,int count);

int main()
{
	int arr[]={4,1,7,2,8,4,6,1,7,5};
	
    int n=sizeof(arr)/sizeof(int); //macro function
	printf("원 데이터: \n");
	for(int i=0;i<n;i++)
	{
	  printf("%d ",arr[i]);	
	}	
	printf("\n\n");
	
	sorting(arr,n);
	
	printf("정렬 데이터: \n");
	for(int i=0;i<n;i++)
	{
	  printf("%d ",arr[i]);	
	}
	
}


void swap(int *a,int *b)
{
	int c=*a;
	*a=*b;
	*b=c;
}


int sorting(int *array,int count)
{
	int i,j,k;
	for(i=0;i<count;i++)
	{
		for(j=0;j<count;j++)
		{
			if(*(array+i)>*(array+j))
			{
				swap(array+i,array+j);								
			}
			
		}
	}
	
	return 0;
}
*/






[표준 입출력 스트림]

stdin   : 표준입력 스트림    file에서 입력받음
stdout : 표준출력 스트림
stderr : 표준에러 스트림


[getchar , putchar 함수]

#include <stdio.h>
int main() 
{
   char ch=0;
   while(ch != 'q')
  {
    ch=getchar();
    putchar(ch);
   }
   return 0; 
}


[문자열의 길이를 반환하는 strlen 함수]
strlen(char *s)

[문자열을 복사하는 함수]

strcpy   크기를 복사                               
strncpy  크기를 지정해서 10개 짜리를 -> 5개 짜리로
                                                                  
[문자열을 추가하는 함수]
strcat
   
문자열을 비교하는 함수]
   
strcmp 함수 
   :  C에서는 if("abc"=="def") 이렇게 할수없다. 따라서
   : if (strcmp("abc","def") ==0 )  같은경우

strncmp 함수
     : if(strncmp("abcd","bc",2)==0)

/* strcamp.c */
#include <stdio.h>
#include <string.h>
char* str1="ABC";
char* str2="ABD";
int main (void)
{
int result;
result=strcmp(str1, str2);
if(result>0)
puts("str1이 str2보다 큽니다 ");
else if(result<0)
puts("str2가 str1보다 큽니다");
else
puts("두 문자열이 정확히 같습니다");
return 0;
}

[문자열을 숫자로 변환하는 함수들]

/*
실습문제 
int Prompt(char *pt,int *ret)
 pt로 전달된 문자열을 출력하고 (안내문자) 입력된 정수
  문자열을 숫자로 변환하여 ret값으로 반환
 +함수의 return 값으로 처리
 ex)scanf("%d",&r);
 	A=r;
    -> A=Prompt("입력하세요:",&r); 
*/

/*
int Prompt(char *pt,int *ret);

int main()
{
	int a,b,c;
	Prompt("A를 입력하세요: ",&a);
	c=Prompt("B를 입력하세요: ",&b);

	printf("A:%d  B:%d  C:%d",a,b,c);	
	
}

int Prompt(char *pt,int *ret)
{
	char buf[254];
	printf("%s",pt);
	
	fgets(buf,254,stdin);
	*ret=atoi(buf);
	
	return *ret;		
}
*/

[문자열안에 문자의 위치 찾기]


/*
함수명: int chrPos(char *str,char chr);
return type: int : chr문자의 위치, 없다면 -1 
input:	char *str : 대상 문자열 
     	char chr : 찾을 문자 
기능: str로 전달된 문자열 중에서 chr문자의 위치를
      검색하여 해당 위치를 반환(zero base)      	
  	
*/
/*
int chrPosW(char *str,char chr); //while 문 
int chrPosF(char *str,char chr); //for 문 

int main()
{
	int a,b,c;
	char *str="abcdefgh";
	printf("문자열: %s\n",str);
	printf("%c의 위치는 %d입니다.\n",'e',chrPosW(str,'e'));
	printf("%c의 위치는 %d입니다.\n",'e',chrPosF(str,'e'));  
	printf("%c의 위치는 %d입니다.\n",'o',chrPosW(str,'o'));
	printf("%c의 위치는 %d입니다.\n",'o',chrPosF(str,'o'));
	
}
 
int chrPosW(char *str,char chr)
{  //*str = "abcdefgh"; chr='d';
 	int i,j,k;
	 i=0;
	 while(*(str+i)) // NULL 이되면 while 빠져나옴 
	 {
	 	if(*(str+i++)==chr) return i-1;
	  }
	  return -1;
}


int chrPosF(char *str,char chr)
{  //*str = "abcdefgh"; chr='d';
 	int i,j,k;
	 i=0;
	 for(i;*(str+i)!=0;i++)  // for(int i=0;*(str+i);i++)
	 {
	 	if(*(str+i)==chr) return i;
	 }

	  return -1;
}
*/


[문자열안에 문자열이 있는 위치 찾기]


/*
함수명: int strPos(char *str,char *s1);
return type: int : s1문자의 우치, 없다면 -1 
input:	char *str : 대상 문자열 
     	char  s1 : 찾을 문자열
기능: str로 전달된 문자열중에서 s1문자열을
      검색하여 해당 위치를 반환(zero base)
	  검색되지 않으면 -1을 반환 
로직 구현 :
	1. str에서 s1의 첫문자가 있는 위치를 검색
	2. 해당 위치에서 strncmp를 이용하여 비교
	   같으면 return i; 아니면 다시 1번.
	3. 만일 끝까지 없으면 -1 
*/

int strPos(char *str,char *s1);
int chrPos(char *str,char chr);

int main()
{
	char *str="abcdefgacdbhj";
	char *s1="acdb";
	printf("문자열: %s\n",str);
	
	printf("%s의 위치는 %d 입니다.\n",s1, strPos(str,s1));
 
}

int chrPos(char *str,char chr)
{  

	 for(int i=0;*(str+i)!=0;i++)  // for(int i=0;*(str+i);i++)
	 {
	 	if(*(str+i)==chr) return i;
	 }

	  return -1;
}

int strPos(char *str,char *s1)
{//*str ="abcdefgacdbhj" ,s1='acdb' , ret:7
    int p;
	 for(int i=0;*(str+i);i++) //   for(int i=0;*(str+i);i+=p+1)   반복횟수를 줄여서 넘어가기위해  
	 {
	 
		p=chrPos(str+i,*s1);  // 		*s1 -> s1 첫번째 요소   // a를 찾기때문에 처음에는 p=0 나오는데
		printf("%d\n",p);
		if(p==-1) return -1;                           // strncmp때문에 다시 해서 p=6이 나온다. 
		if (strncmp(str+p+i,s1,strlen(s1)) == 0) 
		{
		return p+i;
	    }
     }
 
	  return -1;
}

```


### 6강

```
stdin  --> File의 한종류이다
stdout

[파일의 OPEN]

FILE* fopen ( char *filename , char *mode)

파일접근 모드
  : 개방한 파일의 사용 용도를 결정
 r  : read 
 w : write
 a : append 

데이터 입,출력 모드
 t : 텍스트모드 
 b : 2진모드    ex) "rb" , "wb"



#include <stdio.h>
#include <io.h>

/*
int main()
{
	FILE *fp= fopen("test.txt","ab");  //FILE* fopen(const char * filename, const char * mode)
	
	
	fprintf(fp,"Hello Everybody!");  //int fprintf(FILE* stream,const char* format, ...)
	
	fclose(fp);
}
*/
// folder == directory
 

int main()
{
    char s1[10];


    FILE *fp = fopen("D:\\C_YunSeo\\Week2\\test.txt", "r");  // 경로를 표시할때는 \\ 두개를 써줘야한다.  
    fscanf(fp, "%s", s1);  

    printf("%s \n", s1);    

    fclose(fp);   

    return 0;
}




visual studio

asp.net 웹개발 , c++를 사용한 데스크톱개발, net을 사용한모바일개발,  데이터 스토리지 및처리 , visual 확장개발
/*
int main()
{
    char buf[256];


    FILE *fp = fopen("D:\\C_YunSeo\\Week2\\test.txt", "rb");  // 경로를 표시할때는 \\ 두개를 써줘야한다.  
    

	for(int i=0;i<3;i++)
	{
	
	  fscanf(fp, "%s", buf);  
      printf("%s \n", buf );   
    }

    fclose(fp);   

    return 0;
}*/

void FileTest()
{
    char *buf = (char*)malloc(255); //중간에 메모리공간을 확보할수 있다 malloc함수 


    NOTE *fp = fopen("D:\\C_Yunseo\\test.txt", "rb");  // 경로를 표시할때는 \\ 두개를 써줘야한다.  
    fscanf(fp, "%s",buf);  

    printf("파일에서 읽은 문자열: \"%s\" ", buf);    

    fclose(fp);   

}


int main()
{
	FILE *fp= fopen("D:\\C_Yunseo\\test.txt","ab");  //FILE* fopen(const char * filename, const char * mode)
	
	
	fprintf(fp,"Hello! ever");  //int fprintf(FILE* stream,const char* format, ...)
	
	FileTest();
	fclose(fp);
}
*/

//파일을 이용해 성적처리 프로그램
//데이터 파일을 open하여 읽어오기
// --->	이름  	과목명1	과목명2	과목명3	총점	평균	석차 
// --->	홍길동  점수1	점수2	점수3	총점	실수	등수 

#define PNUM 100

int main()
{
	//int pNum=100
	int i,j,k,n;
    int *eng,*kor,*san;
    char **name;
    
    eng=(int*)malloc(PNUM* sizeof(int)); // 명시적인 형변환을 해줘야한다. casting 연산을 해줘야한다. 
    kor=(int*)malloc(PNUM* sizeof(int));
    san=(int*)malloc(PNUM* sizeof(int));

    //name=(char**)malloc(PNUM*10);

	FILE *fp= fopen("D:\\C_Yunseo\\test.txt","rb");
	
	for(i=0;i<PNUM;i++)
	{
		k=fscanf(fp,"%d %d %d",kor+i,san+i,san+i);
		if(k!=3)  break;
	
	
	} 
	n=i;  // for 문 종료되었을 때의 i 값은 무엇을 가리키나요? :데이터의 갯수  (줄의 갯수) 
	for(i=0;i<n;i++)
	{
		printf("%d	%d	%d \n", *(kor+i),*(eng+i),*(san+i));
	}
	fprintf(fp,"Hello! ever");

	
	fclose(fp);
}


```

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
### 3.26
```
[프로젝트] 

1. 프로젝트 수행 계획 수립
 - 프로그램 : S/W : 소프트웨어
 - H/W : 하드웨어
 - 시스템 : 환경, 네트워크 , Mobile

2. 프로젝트 명칭 제정 : 
   ex) IoT 216_FMS  의미부여

3. 개요 : 프로젝트 (프로그램) 설명
  -기능
  -효과

4. 일정, 개발자 ,참고자료 ... 



1. 개요

 1) 프로그램명 :(영문약자)
 2) 개발자
 3) 사용언어 및 개발환경 
    -사용언어 : C/C++/C#
    -개발환경 : window 10
    -개발 툴: Visual

2. 소개
 1) 프로그램 개요
    프로그램만든 이유 , 목적
 2) 프로그램 기능 정의
  ex) 물품  등록,검색,목록,삭제  그거에따른 설명
 3) 개발일정
 4) 프로그램 산출물
   ex) 물품관리를 유용하게하는 어플리케이션
   프로젝트 결과 보고서 + [사용자 메뉴얼]
 
--------------------------------------------------------------------------

개발체제 및 일정
 1. 설계단계
   -아이디어 도출
   -자료수집
   -시나리오/인터렉션 연출
   -인터페이스 설계
   -코드화
   -플로우 차트 작성
   -스토리 보드 작성

 2. 제작단계
   -원시자료 가공/입력
   -인터페이스 디자인
   -프로그래밍
   -디버깅/테스트
   -사용자 테스트
   -수정 및 보안

----------------------------------------------------------------------------

[ DB Open process ]

file select
connection string 구성
DB open
SQL Command object 연결
DB Table 정보 Read
Status Bar : DB name , Table List , 처리 결과


<DBManager>

[ Main Menu - file ]  ,[ Main Menu - edit ] , .....

file 안에
New -> New 의 기능 및, 설계도 작성


New	: grid 초기화 , Table 명칭 초기화 , DB 초기화
Open	: txt , csv 파일 open 및 Migration
Save  : 	1 . save file name 선택
          	2. Grid의 header Text를 ',' 구분자로 출력
	3. 각 Row 단위로 text 파일에 ',' 구분자로 출력
////

visual studio , GitHub 연결하기



opendialog  속성 ValidateNames : False
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

### 5/17
```
라즈베이파이 설정
 SSH : 외부접속을 위한 SSH(Secure Shell)를 사용할수 있도록 설정한다.
 VNC : 외부 화면공유를 위한 VNC를 사용할수 있도록 설정한다.

ls -al > aa
 -> >: Redirection  ls -al에 'aa' 저장해라

Analog : 연속적

Digital : 부호화

gcc -o Hello hello.c  : hello.c 파일을 Hello 라는 이름으로 Output 해라
./Hello : Hello 열기

FILE *fp = fopen("test.txt","ab"); 
 -> "ab" : append 하고 b(binary)모드(\n) 
 fopen 함수 원형
 FILE* fopen (const char* fileName, const char* fileMode)

https://blockdmask.tistory.com/392 설명

getchar -> 엔터까지 취급한다

[terminal]
 rm 파일명 : Remove
 rm *.txt    : .txt 로 끝나는거 다 Remove


[일일 과제]

C# 의
string GetToken(int index,string str,char chr)
{
 string [] sArr=str.split(chr);
 return sArr[index];
}
함수를 C 기초작업 부터 코드 짜보기

C

#include <stdio.h>
#include <malloc.h>
#include <string.h>

int chrFind(char *str,char chr);
int chrFind(char *str,char chr);
char **Split(char *str,char chr);
int chrCount(char *str,char chr);
char *GetToken(int index,char *str,char chr);


int main()
{
	char buf[256];
	int a,b,c;
	/*printf("Input Output FileName:");
	scanf("%s",buf);
	FILE *fp = fopen(buf,"ab"); 
	
	while(1)
	{		
		scanf("%s",buf);	    
		if(buf[0]=='>') break;
		fprintf(fp,"%s",buf);
	}
	fclose(fp);
	*/
	/*
	char *s1="abcdefghijkl";
	while(1)
	{
		printf("input search char :");
		int ch=getchar();
		printf("[%c] 문자는 %d 번째에 있습니다\n",ch,chrFind(s1,ch)+1);		
     }
     */
     char *tt="1,3,4,5,6,7,8,9";
     char **ss=Split(tt,',');
     while(1)
     {
		 printf("Input searce num:");
		 scanf("%d",&a);
		 printf("%d 번째 아이템은 %s 입니다\n",a,GetToken(a,tt,','));
	 }
	 

	/*	
	printf("Hello world!");
	int c=getchar();
	printf("you press [%c] key..",c);
	*/
	return 0;
}

int chrFind(char *str,char chr) //문자열 str 에서 문자 chr의 위치를 변환
{
	int i=0;
	while(*str)
	{
		if(*str++ == chr) return i;
		i++;
	}
	return -1;
}


int StrLens(char *str)
{
	int i=0;
	while(*str++)
	{
		i++;
		return i;
	}
}
char *GetToken(int index,char *str,char chr)
{
	char** ss=Split(str,chr);
	return *(ss+index-1);
}

char **Split(char *str,char chr) // "123,456,789" 
{
	char *tmp1=malloc(StrLens(str));
	char **tmp2=malloc((chrCount(str,chr)+1)*4);
	int i=1;
	strcpy(tmp1,str);
	*(tmp2+0)=tmp1;
	while(*tmp1)
	{
		
		if(*tmp1 == chr)  // "123" "456" "789" :원본손실
		{
			*tmp1=0;
			*(tmp2+i++)=tmp1+1;
			//*tmp2++=tmp1+1;
			//for(int j=0;j<i;j++)
			//{
			//	printf("%s\n",*(tmp2+j));
			//}
		}
		tmp1++;		
	}
	return tmp2;
}
int chrCount(char *str,char chr)
{
	int i=0;
	while(*str++)
	{
		if(*str==chr) i++;
	}
	return i;
	
}

```

### 5.18

```
* (포인터) == [ ](배열) 똑같으나 '[ ]' 안에는 상수가 들어가야한다.(n -> X)

malloc 과 free

C# 에서는
int chrFind(char *str,char chr) 
int chrFind(char *str,char chr,int n)
이렇게 오버로딩이 가능한데 C는 안된다 따라서 
int chrFindEx 이런식으로 새로 만들어야한다 

gcc -o hello hello.c myLib.c : hello.c , myLib.c 실행
gcc -o hello hello.c -lwiringPi : -l 라이브러리 -> wiringPi 생성 

hello.c
myHeader.h
myLib.c        -> GetToken  부분 자세히 보기
makefile

[makefile]

CC=gcc
CFLAGS=-g
OBJS=hello.o myLib.o
TARGET=hello


hello : hello.o myLib.o
	$(CC) -o $@ $(OBJS)

clean :
	$(RM) $(OBJS) $(TARGET) core

hello.o : hello.c myHeader.h
myLib.o : myLib.c

이렇게 만들게 되면 이제 make 만 쳐도 gcc할수있게 된다.

빵판
숫자 1,2,3,4,.... 은 그 줄에 5개씩이 연결 , 
사이드에 '+'와 '-'는 그 전체줄이 연결되어있다


엔터누르면 저기 들어오게 하는 코드
#include <stdio.h>
#include <wiringPi.h>

int main()
{
	wiringPiSetup();
	
    pinMode(8,OUTPUT); // wPi:8번 핀을 쓰겠다 : 실제로는 3번을 쓴다
 	digitalWrite(8,HIGH); // LOW ,GND,0V (같은말)
	
	printf("엔터입력시 끄고꺼짐");
	int i=0;
	char c;
	while(1)
	{
		getchar();
		i++;
		if(i==1)
		{
			digitalWrite(8,LOW);
		}
		else
		{
			digitalWrite(8,HIGH);
			i=0;
		}				
	}
	return 0;
}

[terminal]
   gcc -o led LEDcontrol.c -lwiringPi
   ./led
```

### 5/21
```
<#include <softPwm.h>> 
밝기가 서서히 켜지고 꺼지기

소스코드
#include <stdio.h>
#include <stdlib.h>
#include <wiringPi.h>
#include <softPwm.h>

int main(int argc,char *argv[])
{
	if(argc<2)
	{
		printf("\nUsage : %s wPI-No\n\n",argv[0]);
		return 0;
	}
	int pNo=atoi(argv[1]);
	int pwmRange=100;
	wiringPiSetup();
	
    pinMode(pNo,OUTPUT); // wPi:8번 핀을 쓰겠다 : 실제로는 3번을 쓴다
    softPwmCreate(pNo,0,pwmRange);
 	//digitalWrite(8,HIGH); // <->LOW ,GND,0V (같은말)
	
	printf("엔터입력시 끄고꺼짐");
	int i=0,k=1;
	char c;
	while(1)
	{
		getchar();
		printf("%d번째",k);
		k++;
		i++;
		if(i==1)
		{
			//for(int j=0;j<pwmRange;j++)
				//softPwmWrite(pNo,pwmRange-j);// 이렇게 하면 실행속도가 늦어진다
			for(int j=pwmRange;j>=0;j--)
			{
				softPwmWrite(pNo,j);
				delay(30);
			} 					 			
			//digitalWrite(8,LOW);
		}
		else
		{
			for(int j=0;j<pwmRange;j++)
			{
				softPwmWrite(pNo,j); // 밝기 점점 up
				delay(30);
			}	
			//digitalWrite(8,HIGH);
			i=0;
		}				
	}
	return 0;
}

<조도센서를 이용하여 불켜지고 꺼지기>
조도센서(Photo Resistor)는 주변 환경의 밝기를 측정할 수 있는 센서입니다.
[terminal]
 i2cdetect -y 1 

SPI, I2C ,Serial Port ,Serial Console  를 Enable 후 reboot한뒤
[terminal]
 i2cdetect -y 1 

소스코드
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <wiringPi.h>
#include <wiringPiI2C.h>

//int main(int argc, char *argv[]){	// 메인 함수의 원형 : int main(int argc, char *argv[])	
int main(){
	float val;
	int hndl = wiringPiI2CSetup(0x48); // 리턴값은 I2C 모듈의 handle
	int ch = 2;
	
	wiringPiSetup();
	pinMode(25,OUTPUT);
	
	int op = 100;
	/*
	if(argc<2){
		printf("\nUsage : %s AIN_No \n\n", argv[0]);
		return 0;
	}
	int ch=atoi(argv[1]);	// ascii to integer
	
	if(strcmp(argv[1],"0")==0) ch=0;
	else if(strcmp(argv[1],"1")==0) ch=1;
	else if(strcmp(argv[1],"3")==0) ch=3;
	*/
	
	wiringPiI2CWrite(hndl, ch);
	wiringPiI2CRead(hndl);	// ack
	
	while(1){
		// 자동증가비트, 아날로그출력 인에이블비트 1로
		//0100 01xx		//채널 자동 증가 모드	--> wiringPiI2CWrite(hndl,0x44)	
		val = wiringPiI2CRead(hndl);   // 센서에서 받은 값 반환
		printf("read from I2C address [%d] : %f \n",ch,val);
		
		if(val>op)	digitalWrite(25,HIGH);
		else digitalWrite(25,LOW);
		 
		delay(1000);
	}
	
	return 0;
}



아두이노 센서

PWM (Pulse Width Modulation)
 :일정한 주기 내에서 Duty의 비를 변환 시켜서 평균 전압을 제어하는 방법
  일반적으로 MCU 내부의 내장된 타이머 카운트를 이용하여 제어하게 됩니다.

알고리즘
1. Trig 신호 발사
2. 발사와 동시에 timer가동
3. Echo 감지와 동시에 timer 종료
4. 3-2 : dt 계산
5. dt(마이크로 세컨드) * 0.17 mm 


#include <stdio.h>
#include <stdlib.h>
#include <wiringPi.h>

int main()
{
	int wTrig=15;
	int wEcho=16;
	
	wiringPiSetup();
	pinMode(wTrig,OUTPUT); // 측정 신호 발사
	pinMode(wEcho,INPUT); // 반사 신호 검출

	while(1)
	{
		digitalWrite(wTrig,LOW);
		delayMicroseconds(100); // 트리거 신호 초기화
		
		digitalWrite(wTrig,HIGH); // 트리거 발사
		delayMicroseconds(10); // 기본 delay 보다 훨씬 짧은 시간 10us(마이크로세컨)의 트리거 신호	
		digitalWrite(wTrig,LOW);
		delayMicroseconds(200); // 실제 신호발사까지 지연시간
		
		while(digitalRead(wEcho)==LOW); //until high	
		long start = micros(); // 현재 시간의 마이크로초 단위 count
		while(digitalRead(wEcho)==HIGH);	//until low
		long end = micros(); // 현재 시간의 마이크로초 단위 count
		
		double dist=(end-start) * 0.17;
		printf("Distance : %f\n",dist);
		delay(1000);
	}
}
```
### 5/24
```
<자이로 센서>
   : x,y,z 축의 기울기(각도)측정 , x,y,z 축의 가속도 측정
MPU6050
(Gyroscope[각속도])
(Accellerate[가속도])

자이로 센서
 Interface에서
 SPI,I2C,Serial Port,Serial Console -> Enable

[terminal]
i2cdetect -y 1
#include <stdio.h>
#include <wiringPi.h>
#include <wiringPiI2C.h>

short i2cInt16(int hndl, int addr);

int main()
{
	int i2cAddr = 0x68;
	int bufAddr = 0x3b;
	int pwrAddr = 0x6b;
	
	wiringPiSetup();
	int hndl = wiringPiI2CSetup(i2cAddr);
	
	wiringPiI2CWriteReg8(hndl,pwrAddr,0);
	
	double x1,y1,z1,x2,y2,z2;
	while(1)
	{
		 x1=i2cInt16(hndl,bufAddr)/16384.;
		 y1=i2cInt16(hndl,bufAddr+2)/16384.;
		 z1=i2cInt16(hndl,bufAddr+4)/16384.;
		 x2=i2cInt16(hndl,bufAddr+8)/131.;
		 y2=i2cInt16(hndl,bufAddr+10)/131.;
		 z2=i2cInt16(hndl,bufAddr+12)/131.;
		
		printf("x1=%f y1=%f z1=%f x2=%f y2=%f z2=%f\n",x1,y1,z1,x2,y2,z2);		
	}	

}
short i2cInt16(int hndl, int addr)
{
	short d1=wiringPiI2CReadReg8(hndl,addr);
	short d2=wiringPiI2CReadReg8(hndl,addr+1);
	short d3=(d1<<8) | d2;//d1*256+d2; 
	// 만약 8 shift 연산했는데 1------/----- 이러면 맨앞은 부호이므로 -(마이너스)가 된다.
	// int 는 4byte 이고 short 는 2byte
	return d3;
}

```
### 5.25

```
ADC = 48
 ch(채널) 0~3 방식 

I2C = 68
 memory block 

[ 과제 ]
초음판센서를 이용해서
거리에 따라 LED 등 3개 Red,Green,Yellow 가 켜지게하는
차량 후진 상황을 시뮬

#include <stdio.h>
#include <stdlib.h>
#include <wiringPi.h>

int main()
{
	int wTrig=15;
	int wEcho=16;
	
	wiringPiSetup();
	pinMode(wTrig,OUTPUT); // 측정 신호 발사
	pinMode(wEcho,INPUT); // 반사 신호 검출
	
	pinMode(0,OUTPUT);
	pinMode(2,OUTPUT);
	pinMode(3,OUTPUT);
	


	while(1)
	{
		digitalWrite(wTrig,LOW);
		delayMicroseconds(100); // 트리거 신호 초기화
		
		digitalWrite(wTrig,HIGH); // 트리거 발사
		delayMicroseconds(10); // 기본 delay 보다 훨씬 짧은 시간 10us(마이크로세컨)의 트리거 신호	
		digitalWrite(wTrig,LOW);
		delayMicroseconds(200); // 실제 신호발사까지 지연시간
		
		while(digitalRead(wEcho)==LOW); //until high	
		long start = micros(); // 현재 시간의 마이크로초 단위 count
		while(digitalRead(wEcho)==HIGH);	//until low
		long end = micros(); // 현재 시간의 마이크로초 단위 count
		
		double dist=(end-start) * 0.17;
		if(dist>=150)
		{
			digitalWrite(3,HIGH);
			digitalWrite(2,LOW);
			digitalWrite(0,LOW);
			printf("Distance : %f\n",dist);
			delay(1000);
		}
		else if(dist>=100)
		{
			digitalWrite(3,LOW);
			digitalWrite(2,HIGH);
			digitalWrite(0,LOW);
			printf("Distance : %f\n",dist);
			delay(1000);
		}
		else
		{
			digitalWrite(3,LOW);
			digitalWrite(2,LOW);
			digitalWrite(0,HIGH);
			printf("Distance : %f\n",dist);
			delay(1000);
		}

	}
}



<리눅스를 이용한 TCP 소켓통신>

알고리즘
<Client>
1. Socket 선언
2. 초기화/생성 open 구성
3. connection to Server

<Server>
1. 선언
2. 구성
3. local port 에 bind (엮어주는)
4. listen
5. Client 에서 connection 하면 Accept 하면 
    Client<= (Session 연결) =>Server

[terminal]
   set
   set | more : 한페이지씩 보여줌 (스페이스바)

[terminal]
cd /usr/include
find . *.h | grep -r inet_addr : include 안에 .h 가 있는 것중 inet_addr을 read 
```
### 5 / 26
```
Github 파일 저장법
1. 주소복제하는 곳에가서 zip 다운로드후
2. 압축한뒤 visual 에서 파일을 연다
3. 그리고 한번 모두저장해주면 
4. sln 파일이 생성된다.


Server 와 Client 소켓통신

------------------------------------------------------------------------------------------

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/socket.h> //sys 밑에 socket.h
#include <arpa/inet.h>
#include <unistd.h>
#include <fcntl.h>
#include <pthread.h>
#include <wiringPi.h>

void * readProc();

char *IP ="192.168.0.69";
int PORT=9001;
int sock; //socket handle

int main()
{

	struct sockaddr_in sockinfo;
	char buf[1024];
	int i,j,k;
	pthread_t readThread;
	
	sock=socket(AF_INET, SOCK_STREAM, 0);
	sockinfo.sin_family = AF_INET;
	inet_pton(AF_INET, IP, &sockinfo.sin_addr.s_addr);
	sockinfo.sin_port=htons(PORT);
	
	
	connect(sock, (struct sockaddr*)&sockinfo, sizeof(sockinfo));	
	k=fcntl(sock, F_SETFL, 0);
	fcntl(sock, F_SETFL, k | O_NONBLOCK);
	
	pthread_create(&readThread, NULL, readProc, NULL); // Thread 생성과 동시에 실
	 
	while(1)
	{
		scanf("%s",buf);
		if(buf[0]=='q') break;
		send(sock,buf,strlen(buf),0);
         
	}
    
	close(sock);
	pthread_join(readThread,NULL);	
}

void * readProc() // Thread 함수는 포인터를 써야한다.
{
	int i;
	char buf[1024];
	
	while(1)
	{
		i= recv(sock,buf,1024,0);
		if(i>0) 
		{
			buf[i]=0;      // Server에서 메세지를 보내면 Client에서 보낸 것도 같이 보내지므로 		                       // Server에서 온 메시지 뒤부터 (i번째후) null 값으로 만들어준다
			//if(buf[0]=='q') break;
			printf("%s\n",buf);	//console 출력
			delay(500);			
		}

	}
	return NULL;
}

------------------------------------------------------------------------------------------
[terminal]
   gcc -o tcp tcp.c -l wiringPi -l pthread 
  : -l 2개를 해주어야한다.



------------------------------------------------------------------------------------------

중간과제 < 센서를 이용하여 거리를 Server로 보내기>

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/socket.h> //sys 밑에 socket.h
#include <arpa/inet.h>
#include <unistd.h>
#include <fcntl.h>
#include <wiringPi.h>

char *IP ="192.168.0.69";
int PORT=9001;

int main()
{
	int sock;
	struct sockaddr_in sockinfo;
	char buf[1024];
	int i,j,k;
	int wTrig=15;
	int wEcho=16;
	
	sock=socket(AF_INET, SOCK_STREAM, 0);
	sockinfo.sin_family = AF_INET;
	inet_pton(AF_INET, IP, &sockinfo.sin_addr.s_addr);
	sockinfo.sin_port=htons(PORT);
	connect(sock, (struct sockaddr*)&sockinfo, sizeof(sockinfo));
			
	k=fcntl(sock, F_SETFL, 0);
	fcntl(sock, F_SETFL, k | O_NONBLOCK);
	
	wiringPiSetup();
	pinMode(wTrig,OUTPUT); // 측정 신호 발사
	pinMode(wEcho,INPUT); // 반사 신호 검출

	
	while(1)
	{
		digitalWrite(wTrig,LOW);
		delayMicroseconds(100); // 트리거 신호 초기화
		
		digitalWrite(wTrig,HIGH); // 트리거 발사
		delayMicroseconds(10); // 기본 delay 보다 훨씬 짧은 시간 10us(마이크로세컨)의 트리거 신호	
		digitalWrite(wTrig,LOW);
		delayMicroseconds(200); // 실제 신호발사까지 지연시간
		
		while(digitalRead(wEcho)==LOW); //until high	
		long start = micros(); // 현재 시간의 마이크로초 단위 count
		while(digitalRead(wEcho)==HIGH);	//until low
		long end = micros(); // 현재 시간의 마이크로초 단위 count
		
		double dist=(end-start) * 0.17;
		
            


		//scanf("%s",buf);
		//if(buf[0]=='q') break;
		send(sock,buf,strlen(buf),0);
		sprintf(buf,"%f",dist);
		printf("%s\n",buf);	
        delay(1000);
        
		i= recv(sock,buf,1024,0);
		if(i>0) buf[i]=0;       
		if(buf[0]=='q') break; 
        //fprintf : file 출력
        //sprinf : sprintf(buf, "%s\n",buf); 버퍼출력 // strcpy 끝에 NULL 확인
        
        

	}
	
	close(sock);
}
```
### 5 / 28

```


================================================================================


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <pthread.h>
#include <wiringPi.h>


char *IP = "192.168.0.69";
int PORT = 9001;
int sock, sock_cli;
struct sockaddr_in sockinfo, sockinfo_cli;	// 구조체 생성

void *readProc();

int main(){
	char buf[1024];
	pthread_t readThread;
	sock = socket(AF_INET, SOCK_STREAM,0);	
	
	//sockinfo - 구조체 멤버변수에 값 넣기
	sockinfo.sin_family = AF_INET;
	// h: 리틀 앤디안, -->(to) s(short), l(long)
	sockinfo.sin_addr.s_addr = htonl(INADDR_ANY);	// ip: 4byte, 
	sockinfo.sin_port = htons(PORT);				//port: 2byte
	
	bind(sock,(struct sockaddr*)&sockinfo, sizeof(sockinfo));
	listen(sock,100);
	
	int n = sizeof(sockinfo_cli);
	//클라이언트용 sockinfo
	sock_cli = accept(sock,(struct sockaddr*)&sockinfo_cli,&n);	// blocking
	//int k=fcntl(sock_cli, F_SETFL,0);  // F_SETFL: setting flag, 현재 소켓의 flag 가져오기
	//fcntl(sock_cli, F_SETFL, k | O_NONBLOCK);	//Output nonbolck
	pthread_create(&readThread, NULL, readProc, NULL);
	
	while(1){
		printf("Input text > ");
		scanf("%s",buf);
		if(buf[0] == 'q') break;
		send(sock_cli,buf,strlen(buf),0);
		int i=recv(sock_cli,buf,1024,0);	// blocking
		if(i>0) buf[i]=0;
		if(buf[0]=='q') break;
		printf("%s\n",buf);
	}
	close(sock);
	//pthread_join(readThread, NULL);	// 스레드 종료까지 기다림
	return 0;
}
void *readProc(){
	int i;
	char buf1[1024];
	while(1){
		i=recv(sock_cli,buf1,1024,0);	// blocking
		
		if(i>0) buf1[i]=0;
		if(buf1[0]=='q') break;
		printf("\n%s\n",buf1);

		delay(500);
	}
	return NULL;
}


================================================================================

<UDP Server >


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <pthread.h>

typedef union teamType
{
	int ips;
	char ip[4];
} TMTP;

void *readProc();

//char *IP_CLI ="192.168.0.69";
int PORT = 9100;
int sock_sv, sock_cli, f_cli=0;

struct sockaddr_in sockinfo_sv, sockinfo_cli;

int main()
{
	char buf[512];
	
    pthread_t readThread; //리눅스 스레드는 생성과 동시에 실행된다
	sock_sv=socket(AF_INET,SOCK_DGRAM,0);
	sock_cli=socket(AF_INET,SOCK_DGRAM,0); //
	sockinfo_sv.sin_family=AF_INET;
	sockinfo_sv.sin_addr.s_addr=htonl(INADDR_ANY);
	// htonl : h to n l :h를 n으로 바꾸는데 long(4byte)로 바꾼다.
	sockinfo_sv.sin_port=htons(PORT);
	
	//printf("PORT: %d(%04x) ===> htons(PORT): %d(%04x)\n",PORT,PORT,sockinfo_sv.sin_port,sockinfo_sv.sin_port);
	bind(sock_sv,(struct sockaddr *)&sockinfo_sv, sizeof(sockinfo_sv));
	pthread_create(&readThread,NULL,readProc,NULL);
	

    printf("Waiting for Remote message...\n\n");
    while(1)
    {
		if(f_cli)
		{
			TMTP tt;
			tt.ips=sockinfo_cli.sin_addr.s_addr;
			printf("input text (0x%x8x : %d.%d.%d.%d) :"
			,sockinfo_cli.sin_addr,tt.ip[0],tt.ip[1],tt.ip[2],tt.ip[3]);
			//printf("Input text (0x%08x) :",sockinfo_cli.sin_addr.s_addr);
			scanf("%s",buf);
			sockinfo_cli.sin_port=htons(PORT);
			sendto(sock_cli, buf, strlen(buf), 0, (struct sockaddr *)&sockinfo_cli, sizeof(sockinfo_cli));					
		}
		pthread_join(readThread,NULL);
		close(sock_sv);
		/*
		int n=sizeof(sockinfo_cli);
		int count = recvfrom(sock_sv, buf, 512, 0, (struct sockaddr *)&sockinfo_cli, &n);
		if(count>0)
		{
			buf[count]=0;
			printf("%s",buf);
			//inet_pton(AF_INET,IP_CLI,&sockinfo_cli.sin_addr.s_addr);	
			sockinfo_cli.sin_port=htons(PORT);
			strcpy(buf,"ACK");
			printf("Remote EP : 0x%08x : 0x%04x \n",sockinfo_cli.sin_addr.s_addr,sockinfo_cli.sin_port);
			sendto(sock_cli, buf, strlen(buf), 0, (struct sockaddr *)&sockinfo_cli, sizeof(sockinfo_cli));		
		}		*/
	}	
}

void *readProc()
{
	char buf[512];
	while(1)
	{
		int n=sizeof(sockinfo_cli);
		int count =recvfrom(sock_sv, buf, 512, 0, (struct sockaddr *)&sockinfo_cli, &n);
		if(count>0)
		{
			buf[count]=0;
			printf("%s",buf);
			system(buf);
			//printf("%s",buf);
			f_cli=1;
		}
	}
}

================================================================================
udpSend 
<IP><Port>   :server
 <file>  :target file(full path)

서버에서
ip , port , file경로 입력하면

send에서 파일안에 텍스트를 읽어

서버로 다시보낸다.
IP ,PORT , FILE PATH 
입력하면 그 파일안의 텍스트를 가져오는 프로그램

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <unistd.h>


//char *IP = "192.168.0.69";
//int PORT = 9100;
struct sockaddr_in udp_info;
int sock;

int main(int argc,char **argv) // <IP>,<PORT>,<FILE PATH>
{
	char *IP =argv[1];
 	int PORT =atoi(argv[2]);
 	char *File_path = argv[3];
 	
	FILE *fp=fopen(File_path,"rb"); //b : binary 있는 그대로 read (거의 무조건 뒤에'b'를 붙임)
 
	char buf[512];
	sock = socket(AF_INET, SOCK_DGRAM, 0);
	udp_info.sin_family=AF_INET;
	inet_pton(AF_INET,IP,&udp_info.sin_addr.s_addr);
	udp_info.sin_port= htons(PORT);

    
    
	while(fgets(buf,512,fp))
	{
		sendto(sock, buf, strlen(buf), 0, (struct sockaddr *)&udp_info, sizeof(udp_info));			
		sendto(sock,"\r\n", strlen(buf), 0, (struct sockaddr *)&udp_info, sizeof(udp_info));			
	}
	
	close(sock);
	fclose(fp);
}	


================================================================================

```

### 6/8

```
#include <SoftwareSerial.h>
#include <AFMotor.h>

//뒷쪽
AF_DCMotor motor_1(1);
AF_DCMotor motor_2(2);
//앞쪽
AF_DCMotor motor_3(3);
AF_DCMotor motor_4(4);


void setup() {
  Serial.begin(9600);
  //뒷쪽
  motor_1.setSpeed(255);
  motor_1.run(RELEASE);
  motor_2.setSpeed(255);
  motor_2.run(RELEASE);
  //앞쪽
  motor_3.setSpeed(255);
  motor_3.run(RELEASE);
  motor_4.setSpeed(255);
  motor_4.run(RELEASE);

}

void forward(){
  //뒷쪽
  motor_1.run(FORWARD);
  motor_2.run(FORWARD);
  //앞쪽
  motor_3.run(FORWARD);
  motor_4.run(FORWARD);
  
}

void backward(){
  //뒷쪽
  motor_1.run(BACKWARD);
  motor_2.run(BACKWARD);
  //앞쪽
  motor_3.run(BACKWARD);
  motor_4.run(BACKWARD);
}

void rel(){
  //뒷쪽
  motor_1.run(RELEASE);
  motor_2.run(RELEASE);
  //앞쪽
  motor_3.run(RELEASE);
  motor_4.run(RELEASE);
}

void right(){
  //뒷쪽
  motor_1.run(FORWARD);
  motor_2.run(BACKWARD);
  //앞쪽
  motor_4.run(FORWARD);
  motor_3.run(BACKWARD);
}

void left(){
  //뒷쪽
  motor_1.run(BACKWARD);
  motor_2.run(FORWARD);
  //앞쪽
  motor_4.run(BACKWARD);
  motor_3.run(FORWARD);
}
char op;
void loop() {

  /*
  Serial.println(distance);
  if(distance <= 10){
    right();
    delay(500);
    rel();
  }
  else{
    rel();
  }
  delay(2000);
  while(1){}
  //char op = 
  */
  
  if(Serial.available()){
    char rd = Serial.read();
    Serial.println(rd);
    op = rd;
  
    if(op=='w'){
      forward();
      //delay(500);
      //rel();
    }
    else if(op=='s'){
      backward();

      //delay(500);
      //rel();
    }
    else if(op=='a'){
      left();
      //delay(500);
      //rel();
      
    }
    else if(op=='d'){
      right();
      //delay(500);
      //rel();
    }
    else{
      rel();
    }
    
    delay(500);
    while(1){}
    /*
    else if(rd=='c'){
      exit(0);
    }
    else{
      rel();
    }
    */
  }
}
----------------------------------------

#include <stdio.h>
#include <wiringPi.h>
#include <stdlib.h>
#include <wiringSerial.h>
#include <pthread.h>


#define wTRIG 15
#define wECHO 16

char device[] = "/dev/ttyACM0";

// filedescriptor
int fd;
unsigned long baud = 9600;
double getDistance(int trigPinNum, int echoPinNum);

void *dist(){
	while(1){
		digitalWrite(wTRIG, LOW);
		delayMicroseconds(100);

		digitalWrite(wTRIG, HIGH);
		delayMicroseconds(10);
		digitalWrite(wTRIG, LOW);
		delayMicroseconds(200);

		while (digitalRead(wECHO) == LOW);
		long start = micros();
		while (digitalRead(wECHO) == HIGH);
		long end = micros();

		double distance = (end - start) * 0.017;
		printf("%f\n", distance);
		if(distance<10.) serialPutchar(fd,'x');
	}
}


int main(){
	fflush(stdout);
	
	if(wiringPiSetup()==-1) exit(1);
	if((fd=serialOpen(device, baud))<0) exit(1);

	pinMode(wTRIG,OUTPUT);
	pinMode(wECHO,INPUT);

	pthread_t thr_dist;

	int time_s, time_e;
	float distance;
	char op;
	pthread_create(&thr_dist, NULL, dist, NULL);
	while(1){
//		distance = getDistance(wTRIG,wECHO);
		op = getchar();
		getchar();
//		if(distance <= 10.) op = 'x';
//		printf("%f\n",distance);
		serialPutchar(fd,op);
		delay(500);
	}
	

	return 0;
}



double getDistance(int trigPinNum, int echoPinNum) {

	digitalWrite(trigPinNum, LOW);
	delayMicroseconds(100);

	digitalWrite(trigPinNum, HIGH);
	delayMicroseconds(10);
	digitalWrite(trigPinNum, LOW);
	delayMicroseconds(200);

	while (digitalRead(echoPinNum) == LOW);
	long start = micros();
	while (digitalRead(echoPinNum) == HIGH);
	long end = micros();

	double distance = (end - start) * 0.017;

	return distance;
}

--------------------------------------------------------------------------------------


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <unistd.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <pthread.h>
#include <wiringPi.h>
#include <wiringSerial.h>


char* IP = "192.168.0.154";
int PORT = 9001;
int sock_serv, sock_cli;
struct sockaddr_in sockinfo_serv, sockinfo_cli;	

char device[] = "/dev/ttyACM0";
unsigned long baud = 9600;

int main() {
	int fd;
	char buf[1024];
	fflush(stdout);
	if((fd=serialOpen(device, baud))<0) exit(1);

	sock_serv = socket(AF_INET, SOCK_STREAM, 0);

	sockinfo_serv.sin_family = AF_INET;
	sockinfo_serv.sin_addr.s_addr = htonl(INADDR_ANY);
	sockinfo_serv.sin_port = htons(PORT);

	bind(sock_serv, (struct sockaddr*)&sockinfo_serv, sizeof(sockinfo_serv));
	listen(sock_serv, 100);

	int n = sizeof(sockinfo_cli);

	sock_cli = accept(sock_serv, (struct sockaddr*)&sockinfo_cli, &n);	// blocking

	char op='c';
    	while(1){
		int i=recv(sock_cli,buf,1024,0);	// blocking
		if(i>0) buf[i]=0;
		if(buf[0]=='q') break;
		printf("buf=%s\n",buf);
	    op=buf[0];
	    //printf("op=%s\n",&op);
		serialPutchar(fd,op);
		delay(500);
	} 
	close(sock_cli);
	close(sock_serv);

	return 0;
}


```
