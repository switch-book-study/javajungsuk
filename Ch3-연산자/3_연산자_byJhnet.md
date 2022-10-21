# 연산자
산술 > 비교 > 논리 > 대입 순으로 수행된다.

# 단항연산자
```++```, ```--``` ```1증가``` 또는 ```감소```
 **i++** ```값 참조``` 후 ```증가```
** ++i ** ``` 증가``` 후 ```값 참조```

```
i = i + 1; // 느림
i++; // 빠름
// 결과는 같음

```
#### i = i + 1 내부
피연산자 형변환을함
istore_1 -> iload_1 -> iconst_1 -> iadd -> istore_1
* 무슨내용인지 까볼려했는데 자료가 없어서 포기

#### i++ 내부
istore_1 -> iinc 1 1

## 부호 반전하기
```
int i = -10;
i = +i; // -10
i = -i; // 10
```
```i = -i```는 ```i*(-1)```를 한거다.

## 비트 전환
```
int n = 10;
n = ~n; // -11;
n = ~n; // 10;

byte n = ~10; // n에는 -11이 저장됨 (n은 int형으로 변환됨)
```
```~```를 붙히면 부호비트가 변경됨
```byte```, ```short```, ```char```는 ```int```로 변환후 사용해야한다.

## 논리 부정
```
boolean b = true;
System.out.println(!b); // false
```


# 산술연산자
2byte + 1byte = 4byte

4byte + 2byte = 4byte

8byte + 2byte = 8byte

큰 byte로 형변환됨 (최소 4byte)

```
byte a = 10;
byte b = 10;
byte c = a + b; // error, int인 값을 byte로 넣으려해서 그런다.
byte c = (byte) (a + b); // 정상
```

```
int a = 1000000;
int b = 2000000;
long c = a*b; // 2천억, -1454759936
```
int형에서 오버플로 후 long에 저장된다.

## %
나머지 구하는 연산자

## \>> <<
시프트 연산자

```/```, ```*``` 보다 빠름
```
System.out.println(8 << 2); // 32
System.out.println(8 >> 2); // 2
```


# 비교연산자
```true``` or ```false``` 반환

```==```, ```!=```, ```>=```, ```<=```, ```>```, ```<```가 있음

```
System.out.println(10.0 == 10.0f); // true
System.out.println(0.1 == 0.1f); // false
```

0.1d의 근사값과 0.1f의 근사값이 달라서 false (리터럴을 안쓰면 기본값은 d)


# 논리연산자

```boolean``` 반환
``` a && b``` : 모두 true면 true변환
- false 확률이 높은건 맨왼쪽

``` a || b ``` : 1개만 true면 true
- true 확률이 높은건 맨 오른쪽

조건이 성립되면 오른쪽을 안돌아 성능이 상승한다.

## 비트연산자
```&``` ```|``` ```^```
```^``` 는 ```XOR```연산자
각 비트대로 연산을 한다.

a = 3

b = 5

00011

00101

a & b = 1

a | b = 7

a ^ b = 6


# 그외의연산자
## 삼항연산자
```
System.out.println(1 >= 3 ? true : false); // false
System.out.println(3 >= 1 ? true : false); // true
```
if문 대신 사용 짧은게 장점이다.
## 대입연산자
```=``` 를 사용


> 중요 : i=i+1 보단 ```무조건 i++```을 쓰자
연산하면 default로 4byte로 변환된다.


> 참조 : https://d2.naver.com/helloworld/1230
