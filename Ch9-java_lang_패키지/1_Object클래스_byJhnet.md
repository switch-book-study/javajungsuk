- java.lang패키지는 자바에서 기본적인 클래스들을 포함
- import 없이 사용가능

# Object클래스
모든 `클래스`의 최고 조상

## eqauls메서드
객체의 `참조변수`가 같으면 true출력
```java
return this == obj;
```
### equals메서드 오버라이딩
```java
public class Main {
	public static void main(String[] args)  {
		Person p1 = new Person(123);
		Person p2 = new Person(123);
		System.out.println(p1.equals(p2));
	}
}

class Person {
	long id;
	
	@Override
	public boolean equals(Object obj) {
		if(obj != null && obj instanceof Person) {
			return id == ((Person)obj).id;
		} 
		
		return false;
	}
	
	public Person(long id) {
		this.id = id;
	}
}
```
오버라이딩해서 멤버변수와 비교한다.

String클래스도 equals를 오버라이딩해서 사용
즉, 주소값이 아닌 내용을 비교

## hashCode메서드
- 해싱기법에 사용되는 해시함수를 구현함
- 다량의 데이터를 저장하고 검색하는데 유용
- int형이다.
- 프로그램 실행마다 값이 달라짐
- 프로그램 시작부터 끝까지 같은 값 유지
- 같은 객체면 값이 같다.
- equals를 오버라이딩한다면 hashcode도 오버라이딩해서 `인스턴스를 생성할 때마다 같게한다.`

> hashCode는 주소값을 이용해서 `절대 같을 수 없다.`

## toString메서드
```java
return getClass().getName() + "@" + Integer.toHexString(hashCode());
```
그냥 호출하면 `클래스이름 + 16진법해시코드`출력
toString()을 안쓰고 변수명만 써도 toString()이 출력된다.

## clone메서드
멤버변수의 값을 복사한다.
```java
class Person implements Cloneable {
	long id;
	
	@Override
	public Object clone() throws CloneNotSupportedException {
		return super.clone();
	}
}

p1 = p2.clone(); // 깊은복사가된다.
```
사용하려면 `Clonable`인터페이스를 구현해야한다.


# String 클래스
문자열을 위한 클래스

## String 클래스 특징
- `char[]`형으로 저장된다.
- 문자열은 읽기, 쓰기는 가능. 변경은 불가능
  - 변경할때마다 새로운 String인스턴스가 생성된다. 
- 수정이 많을땐 `StringBuffer`쓰면 좋다.
- ""로 초기화하는게 좋다.
  - `+=`연산자를 쓰면 문자열앞에 `null`문자가 붙는다. 

두가지방법으로 선언가능

1. 리터럴 : 같은문자면 하나의 인스턴스를 바라본다. 
2. 인스턴스 : 생성할때마다 다른 객체

> 리터럴은 클래스파일 내에 `constant pool`이라는 목록이 있다. 
`constant pool`에는 모든 리터럴과 상수들이 저장되있다.
컴파일하면 Heap메모리 안에 저장한다.

### intern메서드
```java
String s1 = "AAA";
String s2 = new String("AAA");

s2 = s2.intern(); // AAA 문자가 들어있는 인스턴스를 바라본다.
s1 == s2 // true
```

## 빈문자열
크기가 0인 배열은 존재할 수 있다.
`String s ="";`하면 `new char[0]`이다.

## String클래스의 생성자와 메서드
String -> 숫자로 변경하는방법
```java
int value = 100;
String s1 = String.valoueOf(value); // 성능이 더좋다.
String s2 = value + ""; // 간단하다.
```
둘다 권장하는 방법이다.

숫자 ->String변경하는방법
```java
String s = "1";
Integer.parseInt(s);
```

---
이밖에 자주쓰는 메서드는 `indexOf`, `substring`, `length`등등 있다.

# StringBuffer 클래스
- String과 유사
- 문자열 변경가능
- 기본 버퍼크기는 16

## StringBuffer 생성자
- 버퍼크기를 지정안하면 `16`
- 문자열을 바로 생성하면 `문자열길이 + 16`
- 문자열 작업할때 `문자열 > 버퍼의크기`라면 버퍼크기를 증가한다.
그 이후 `arraycopy`메서드로 이전 값을 복사한다.

## StringBuffer 인스턴스의 비교
 - equals를 오버라이딩 하지않았다.
 - String으로 변환 후 equals로 비교
 
# Math클래스
- 수학계산에 유용
- static이라 인스턴스 생성 필요x

# wrapper클래스
- 기본형 -> 객체로 변환된 클래스
- Boolean, Character, Byte, Short, Integer, Long, Float, Double
- 래퍼클래스는 전부 equals가 오버라이딩 되서 객체값을 비교

#### 문자열-> 기본형
```java
byte b = Byte.parseByte("100);
int i = Integer.parseInt("100);
```
parse가 붙는다.

#### 문자열 -> wrapper클래스
```java
Byte b = Byte.valueOf("100);
Integer i = Integer.valueOf("100);
```
valueOf가 붙는다.

-----

```java
Integer intg = (Integer)i; // 컴파일 전의 코드
Integer intg = Integer.valoueOf(i); // 컴파일 후의 코드
```
컴파일 오토박싱으로 변경된다.

# Number클래스
숫자와 관련된건 Number클래스의 자손이다.
`BigInteger` : long보다 큰범위의 정수
`BigDecimal` : double보다 큰 범위의 부동소수점을 처리


> _정리_
- import없이 java.lang 사용가능
- hashCode는 메모리값을 이용, `값 중복 절대x`
- String내부는 char[]로 돼있다.
- String으로 값을 지정하면 클래스파일에 `constant pool`이 저장되고 컴파일되면 `jvm heap영역`에 저장된다.
