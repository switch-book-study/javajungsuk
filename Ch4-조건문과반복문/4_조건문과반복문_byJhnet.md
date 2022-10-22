# 조건문
모든 switch문은 if문으로 변경가능.
반대는 안될 수 있음

## if문
if문 결과는 ```true``` or ```false```만 허용

```
boolean b = true;
if(b) {
	System.out.println("실패 결과");
	return;
}
		
System.out.println("여러가지 로직");
```
```validation```은 위와같은 코드가 가독성이 좋다.
```
boolean b = true;
if(b) {
	System.out.println("짧은로직1");
} else {
	System.out.println("짧은로직2");
}
```
로직을 짧게 나누려면 위와 같은 방식으로 한다.
* if로 하는 변수선언이면 삼항연산자를 쓴다.

```
boolean b = true;
if(b) {
	if (1 == 1) {
		System.out.println("짧은로직 1-1");
	} else {
		System.out.println("짧은로직 1-2");
	}
	
    System.out.println("짧은로직1");
} else {
	System.out.println("짧은로직2");
}
```
보통 위처럼 쓸경우에는 함수를 하나더 만들어서 호출시킨다.


```
if(b) {
	짧은로직1_1_1_2();
	
    System.out.println("짧은로직1");
} else {
	System.out.println("짧은로직2");
}


```


# switch문
```
int in = 1;
switch (in) {
	case 1: System.out.println("1번로직"); break;
	case 2: System.out.println("2번로직"); break;
	case 3: System.out.println("3번로직"); break;
	case 4: System.out.println("4번로직"); break; // break는 안써도 되지만 가독성을 위해 쓴다.
}
```
스위치 기본문법

```
int 권한 = 1;
switch (권한) {
	case 1: 관리자권한(); break;
	case 2: 일반권한(); break;
	case 3: 뷰어권한(); break;
}		
```
```switch```로 권한주는 예제 

```enum```과 섞으면 훌륭한 코드가 될것같다.

# 반복문

## for문
```
for(초기화;조건식;증강식)
	// 조건식이 true일때 수행

```
### 작동원리
```초기화``` -> (```조건식``` -> ```수행```-> ```증강식```) ```반복```

조건식이 ```false```일때까지 반복한다.

조건식이 생략되면 ```true```다.

자료형붙힌 초기화변수는 for문 안에서만 유효하다

## while문
```
while (조건식) 
	// 조건식이 true일때 수행
```

## do while문
```
do {
   // 조건식이 true일때 수행
} while(조건식)
```
최소 1번은 수행된다.


## break, continue
```break``` 가장가까운 반복문탈출
```continue``` 가장 가까운 반복문 ```}```로 이동


> 정리 : if문 보다 switch문이 더 빠르다.
