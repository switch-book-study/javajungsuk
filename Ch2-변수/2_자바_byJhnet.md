# 변수 컨벤션
- 변수는 1개씩만
```int a, b;```금지
- carmelCase로 작성
- boolean 변수명
```is```, ```has```, ```can```, ```should``` 등등을 앞에 붙히면된다.
ex) ``` bool isProcess = false; ```
```exists```는 메서드에 붙힌다.




# 변수 타입
기본형 8개
나머지는 참조형
- ```null```과 ```주소값```(거의 무한)
- 모든 참조형은 ```4바이트```


## 기본형
### boolean
```1byte``` 
true, false만 있다.
- 데이터를 다루는 최소단위는 ```byte```라 ```1bit가 아니다.```

### char
``` 2byte ```
 ```영어```와 ```특수문자```는 ```1byte```로 표현가능한데
``` 한글, 한자, 일본어``` 때문에 ```2byte```를 사용
char의 모든 데이터는 숫자로 저장된다.
1개의 문자만 저장가능
```char ch = 'A';```


### byte, short
byte : ```1byte```
short : ```2byte```

```
byte a = 127;
byte b = 127;
System.out.println(a+b); // 4byte로 변환되서 254 출력
```

**JVM의 피 연산자 스택이 ```4byte```로 저장한다. 
```byte, short```는 자동으로 ```4byte```로 변환됨**



> 피연산자 : ```+```, ```-``` 뒤에 있는 숫자 (위 예시에선 ```b```가 피연산자)



### int
``` 4byte ```
```
int a = 010; // 8진수
int b = 0x10; // 16진수
```

### long
``` 8byte ```
```
long a = 1000000000L; // 안붙히면 d가 들어감
```
long형은 뒤에 ```L``` or ```l``` 을 붙혀서 저장함
- ```l```은 숫자 ```1```과 비슷해서 대문자를 써야한다


> 숫자형데이터는 자기 byte수를 넘어가면  overflow가 된다.
실행은 정상적으로됨

### float, double
float : ```4byte```
double : ```8byte```

```
float f = 1.12f; // float는 뒤에 f를 붙힌다.
double d = 1.12d; // d를 생략해도된다. 생략하면 자동d 붙혀짐
```

#### 부동소수점
float, dobule의 내부 원리다.

![image](https://user-images.githubusercontent.com/28896454/196996914-0a6b12d0-d5e5-4117-b153-a76c20cee634.png)

> 이미지 참고 : https://steemit.com/kr/@modolee/floating-point
위는 float일때

부호비트 : ```+, -```를 구분한다 ```0이면 +```
지수 비트 : 127+8
가수 비트 : 23

뒤에 소수점이 많으면 잘린다.

# 캐스팅
기본형<->기본형
기본형->참조형 (오토박싱)
참조형<->참조형 끼리만 가능
> boolean형 제외

```
int a = 10;
double d = 11.0;
System.out.println(a + (int) d); // 10 + 11 = 21		
```

```
int n = 210000000;
long l = n; // (int) 생략가능
System.out.println(l);
```
```높은byte``` -> ```낮은byte```로 변환하면 ```byte손실```이 일어난다.
```낮은byte``` -> ```높은byte```로 변환하면 ```()``` 생략가능


> 중요 : ```4byte이하``` 변수가 연산되면 ```JVM```에 의해서 ```4byte```로 자동 형변환이 됨
```short```, ```byte```보단 ```int```로 쓰자.
