# 예외처리
## 프로그램 오류
프로그램 실행중 오작동하는것
- 런타임 에러 : 실행도중 에러
  - 에러 : 메모리부족, 스택오버플로우
     - 복구못하는 심각한에러
  - 예외 : 발생해도 수습가능, 비정상종료 막을 수 있음
- 컴파일 에러 : 컴파일중 에러

## 예외처리의 정의와 목적
정의 : 프로그램 실행시 예외에 대비한 코드
목적 : 프로그램의 비정상 종료막기, 정상적인 실행유지

## 예외처리구문 try catch
```java
int number = 100;
int result = 0;

for(int i = 0; i < 10; i++) {
	try {
			result = number / (int) (Math.random() * 10);
			System.out.println(result);
	} catch (ArithmeticException e) {
		System.out.println("0");
	}
}
```

## try catch문에서의 흐름
### 예외발생
1. 발생한 예외가 있으면 catch절에서 찾음
2. catch블럭을 찾고 수행. 없으면 예외처리안됨

### 예외발생X
catch절 무시

## 예외발생시키기
```java 
Exception e = new Exception("고의로 예외발생"); // 1번방식 
```

## 예외 클래스의 계층구조
![](https://velog.velcdn.com/images/bjh0501/post/f11f4b29-e029-48e8-8d3f-a92a27851a5a/image.png)
> 그림출처 : https://velog.io/@mingseok/%EC%98%88%EC%99%B8-%ED%81%B4%EB%9E%98%EC%8A%A4%EC%9D%98-%EA%B3%84%EC%B8%B5%EA%B5%AC%EC%A1%B0

예외클래스는 2개로 나눌수 있다.
- `Exception`클래스와 그 자손클래스들
  - IOexception, ClassNotFoundException, RuntimeException 등등
  - 사용자의 실수 (라이브러리 사용자)
  - 컴파일 시 에러
- `RuntimeException`클래스와 자손클래스
  - ArithmeticException, NullPointerException, IndexOutOfBoundsException 등등
  - 개발자의 실수
  - 컴파일시 문제되지 않음
  

```java
// try catch문으로 감싸야한다.
throw new Exception(); // 컴파일에러

// 컴파일시 문제되지 않는다.
throw new RuntimeException(); // // 비정상에러
```

## 예외의 발생과 catch블럭
### 동작순서
1. 예외발생
2. catch에 선언된 예외변수를 찾음
3. 1번의 예외클래스와 catch 예외클래스 인스턴스와 instanceof로 검사한다.
4. true면 해당 catch문 실행

```java
PrintStream ps = null;
try {
	ps = new PrintStream("error2.log");
	System.out.println(0/0); // 예외발생
	System.out.println(1);
} catch(ArithmeticException ae) { // true
	System.out.println(12);
	ae.printStackTrace();
    ps.println("예외 : " + ae.getMessage());
    System.err.println("err : " + ae.getMessage()); // 파일로저장
	System.out.println(ae.getMessage());
} catch (Exception e) {
	// 조상클래스 Exception사용
	// instanceof로 true인데 위에서 수행되서 
	// 2는 출력안됨
	System.out.println(2);
}
/*
 if
 elseif
 else
 구조라고 생각하면될듯
*/
```
- printStackTrace : 예외발생당시 콜스택에 있던 `메서드정보`와 `예외메시지`출력
- getMessage : 예외 클래스 인스턴스의 메세지를 읽는다.

## finally블럭
try문이 끝나고 finally블럭으로 이동한다.
try문에서 return을 만나도 finally가 수행된다.

## 메서드에 예외 선언하기
```java
throws Exception1, Exception2 { }
```
`throws`는 선언할때
`throw`는 메서드 몸통에서

throws를 쓰면
- 예외가 있다는걸 예측할 수 있음
- 호출스택을 알 수 있음
- 에러 맨위에있는게 최초 발생, 아래가 호출지점
```java
java.lang.Exception
	at ExceptionEx18.method2 (ExceptionEx18.java:12)
    at ExceptionEx18.method1 (ExceptionEx18.java:8)
    at ExceptionEx18.main (ExceptionEx18.java:4) 
```

```java
void method1() {
	try { 
    	throw new Exception();
	} catch(Exception e) {}
}

method1();
```
위처럼 사용하면 정상작동하지만 어디서 예외가 발생됐는지 알 수 없다.

```java
void method1() throws Exception {
	throw new Exception();
}
try {
	method1();
} catch(Exception e) {}
```
위처럼 사용해야 `method1()`을 호출한  부분에서 에러가 났다는것을 알 수있다.


### 예외처리 방법 
- 파라미터가 없는 메서드는 `메서드 내에서 예외처리`
- 파라미터가 있는 메서드는 `호출쪽하는 쪽`에서 처리

## 예외 되던지기
```java
	public static void main(String[] args) {
		try {
			method1();
		} catch (Exception e) {
			System.out.println("에러2");
		}
	}
	
	static void method1() throws Exception {
		try {
			throw new Exception();
		} catch (Exception e) {
			System.out.println("에러1");
			throw e;
		}
	}
```
`throw e`로 호출쪽에도 예외가 발생되게 한다.
`throw e`가 없으면 에러1만 출력된다.

## 사용자 정의 예외 만들기
개발자가 직접 예외를 만들 수 있다.
```java
public class Main {
	public static void main(String[] args)  {
		try {
        	// throw MyException으로 돼있어서 
            // catch로 갈수있다.
            
			test(); 
		} catch (MyException e) {
			System.out.println("에러 : " + e.getMessage());
		}
	}
	
    // 에러 메서드
	public static void test() throws MyException {
		throw new MyException("ERR");
	}
}

// Exception 상속받기
class MyException extends Exception {
	public MyException(String msg) {
		super(msg);
	}
}
```
`에러 : ERR` 출력

> 정리 
Exception안에 RuntimeException이 있다.
예외가 발생하면 catch문에서 instanceof로 예외클래스랑 비교해서 처리됨
