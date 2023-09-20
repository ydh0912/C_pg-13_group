# C_13_group
3주차 토론


72페이지 2-1번

char a = 129를 int로 수정했더니 정상 작동하였다


72페이지 2-2
const 로 선언한 number가 에러가 떠서 문제가 생겼고, 하지만 우리는 const로 선언한 number를 바꿀 수 없는가? 궁금해서 인터넷에 찾아보았다
인터넷에서 인용한 답변을 적어보자면 
"단순한 형 변환으로는 일반 변수에 적어 놓은 const 키워드를 무효화 시키지 못한다. 따라서 number변수를 주소 자료형으로 변환해서
const int *로 변경 해놓고 이 자료형을 int * 자료형으로 형 변환을 한다. 그리고 * 연산자를 사용해 값을 변경하면
const 변수에 정상적으로 값이 대입된다" 라는 방법으로 
*(int *)&number = 30; 이렇게 바꾸었고 이러한 방법으로 number에서 뜨는 에러를 수정할 수 있었다

하지만 우리 생각으로는 이 프로그램에선 number라는 변수를 쓰지 않기에 굳이 필요한가? 의문이 들었다
따라서 우린 number라는 변수 자체를 없애는 것도 답변이 될 수 있다고 생각한다.

두 번째로는 area 변수를 short인 정수형 변수로 선언했는데 printf에서는 %d가 아닌 %lf인 double형으로 printf를 하려고 해서
값이 0.000... 이렇게 떴다 이것은 서로가 잘 이해하고 있는 부분이여서 %lf를 %d로 바꾸어서 쉽게 오류를 수정하였다.



------------------------------------------------------------------------------------

10진수
68과 126을
2진수 / 16진수로 변경

68
2진수 : 1000100
16진수 : 44



126
2진수 :1111110
16진수 : 7E


----------------------------------------------------------------------------------------


char -> short -> int -> unsigned -> long -> float -> double

왜 이러한 방향으로 자동 변환이 되는가??

=> int가 4byte고 double 8byte고 int를 double로 변환이 되는거 같다 받아들일수 있는 양이 다르고..아마도 데이터 손실이 적다


왜 반대로는 불가능 한가?
=> 8byte에서 4byte로 가면 데이터 손실이 생길것 같아서 안되는거 같다 실수에서 정수가면 소수점들이 사라지는 것 처럼
반대로 가면 데이터가 많이 날라가서 안되는 것 같다.



----------------------------------------------------------------------------------------

int a = 10, b = 20, c;
float d = 5.6, e = 8.4, f;

c = d + e;
printf("c = d + e의 연산결과는 %.2f이다.\n", (float)c);

부분에서 의문이 들었다
변수 c는 int 형이고 d, e는 float형이다

int형 값에 float형을 넣으려고 하는데
그러하면 d 와 e가 자동으로 int로 변환되지 않고

c가 왜 float형으로 변환이 되었는가?

c에 저장하기 위해 d , e가 int로 변형되어 5.6 / 8.4인 소수점이 사라지고 5와 8로 더해진 값인 13이 들어가는 줄 알았고
마지막에 float형으로 명시적으로 바꾸어도 13.00이 나올 줄 알았다

하지만 프로그램에서는 c가 float형으로 변환되어 5.6 + 8.4 의 값인 14가 들어갔다.

이러한 이유는 아까 묵시형 변환 순서인
char -> short -> int -> unsigned -> long -> float -> double 룰에 따른 것 같다고 생각이 들었다

아니면

int = float + float 인 float연산이기에 int형이 float형으로 자동 변환이 된거 같다고 생각한다.
