# 상속
기존의 클래스를 재사용 하는것

## 상속의 정의와 장점
- 조상클래스 : 부모클래스, 상위클래스, 기반클래스
- 자손클래스 : 자식클래스, 하위클래스, 파생된클래스


![](https://velog.velcdn.com/images/bjh0501/post/4e6891ad-0f34-4138-9112-7131fb4ccd8d/image.png)
>상속 그림 표시
자식클래스에서 부모클래스로 화살표가 표시돼있다.

![](https://velog.velcdn.com/images/bjh0501/post/867cfea2-d78e-4ec0-a792-6814d54f0ac4/image.png)

> 다이어그램

- 부모에 변수를 추가하면 자식도 변수가 자동으로 추가된다.
- 한 부모에는 여러 자식클래스가 있을 수 있다.
- 상속에 상속을 받을 수 있다.
- 상속을 받은 자식클래스의 인스턴스를 생성하면 부모+자식클래스가 하나의 인스턴스로 생성된다.

## 클래스간의 관계 - 포함관계
```java
class Circle {
	int x;
    int y;
    int r;
}
```
코드를 
```java
class Circle {
	Point c = new Point();
    int r;
}
```
로 바꾸면 간결하고 코드 관리가 쉽다.

## 클래스간의 관계 설정하기

클래스를 `포함`할것인지 `상속`할것인지 헷갈릴때가있다.

>
- 상속 (a는 b_다._)
  - `원`은 `점`이다.
  - `스포츠카`는 `자동차`다.
- 포함 (a는 b를 _가지고있다._)
  - `원`은 `점`을 가지고 있다.
  - `스포츠카`는 `자동차`를 가지고 있다.
  
구조짤때 이렇게 문장을 만들어서 생각하면 쉽다.

## 단일상속
`c++`은 `다중상속`이 가능한데 `자바`는 `하나`만 가능하다.

## object클래스 - 모든 클래스의 조상
- **모든 클래스는 object클래스가 상속돼있다.**
- 컴파일하면 컴파일러가 자동으로 붙혀준다.
- Object의 멤버들을 사용할 수 있다.

# 오버라이딩
- 조상클래스에서 상속받은 메서드를 변경하는것
- 오버라이딩은 메서드 내용을 새로 쓰는것이다.
## 오버라이딩의 조건
- `이름`, `매개변수`, `리턴타입`이 같아야한다.
- `접근제어자`는 조상 클래스보다 범위가 넓어야한다.
- `예외`는 조상 클래스보다 많이 쓸 수 없다. (넓은 범위로 쓸 수 없다.)
  - `예외`도 조상순으로 조건을 맞춰야한다.
  - ex) 부모에 `IOException`을 쓰면 자식에는 `Exception`을 못쓴다.
- 인스턴스 메서드와 static메서드는 서로 반대로 변경할 수 없다.

## 오버로딩 vs 오버라이딩
- 오버로딩 : 새로운 메서드를 정의
- 오버라이딩 : 메서드를 변경

## super
같은 클래스는 `this`로 썼다면 상속 받은 멤버는 `super`로 쓴다.

## super()
`this()`는 같은 클래스 생성자 호출
`super()`는 상속 클래스 생성자 호출
- 생성자에서만 첫째줄에서만 쓸 수 있다.
- 모든 클래스의 생성자에는 super()를 쓴다. 없다면 컴파일러가 첫줄에 자동으로 `super();`코드를 생성한다.

# package와 import
## package
클래스의 묶음

- 클래스파일 최상단엔 `package` 예약어로 선언해야한다.
- 모든 클래스는 반드시 하나의 패키지에 속해야한다.
- 패키지는 .으로 계층 구분
- 클래스는 파일, 패키지는 디렉터리

## 패키지의 선언
```java
package 패키지명;
```
파일 최상단에 선언해야한다.

### 이름없는패키지
패키지를 선언하지 않으면 자동으로 이름 없는 패키지에 속한다.

`javac -d PackageTest.java`
- -d 옵션은 코드에서 `package 패키지명`을 통해 알아서 폴더를 만들어준다.
- 폴더가 없으면 자동으로 생성된다.
- -d 옵션을 사용하지 않으면 직접 디렉터리를 생성해야한다.

### 클래스패스
- 패키지를 `클래스패스`에 포함해야 클래스파일을 읽는다.
- 보통 환경변수에 설정한다.
- `;`로 구분한다.
- `.`은 현재 경로 추가

클래스패스 : `c:\a`
클래스파일 : `c:\a\b\c\Test.class`
명령어 : `java b.c.Test` Test.class 실행됨

임시로 클래스패스 지정하기 `-cp` 명령어
ex) `java -cp c:\~~임시클래스패스경로 b.c.Test`

## import문
`import 패키지명.클래스명`을 붙혀서 선언할 수 있다.
import문은 프로그램에 성능에 영향을 안끼친다. 다만 컴파일시간이 더 걸린다.

## import문 원리
코드에 import를 선언하면 컴파일러는 해당 코드안에 있는 모든클래스 앞에 패키지를 붙혀준다.
ex )
```java 
import java.util.Date
Date d = new Date(); // java.util.Date d = new java.util.Date();
```

## import문의 선언
1. package
2. import문
3. 클래스선언

순으로 작성한다.

### import문 작성법
`import 패키지명.클래스명`
`import 패키지명.*`
\*을 붙히면 해당 패키지명에 있는 모든 클래스를 import한다.

`import java.*;`으로 import해도 아래 포함된 클래스들은 import 안된다.
`import java.util.*;`
`import java.text.*;`
대신 java안에 클래스가 있다면 `java.클래스`들은 import된다.

> `import java.lang.*` 은 자동 import가 된다.

# 제어자
`접근제어자`와 `그외의 제어자`로 나뉜다.
## static - 클래스의, 공통적인
1. 하나의 변수를 모든 인스턴스가 공유한다.
1. 인스턴스 생성없이도 사용가능하다.
> 사용되는곳 : 멤버변수, 메서드, 초기화 블럭

## final - 마지막의, 변경될 수 없는
- 클래스에 사용 : 상속불가 (조상이 안됨)
- 메서드에 사용 : 오버라이딩으로 재정의 안됨
- 변수에 사용 : 상수


## 생성자를 이용한 final 멤버변수 초기화
인스턴스변수는 생성자에서 초기화할 수 있다.

## abstract - 추상의, 미완성의
클래스에 사용 : 추상메서드가 있음을 의미
메서드에 사용 : 선언만 작성, 구현은 없음

- 추상메서드가 없어도 클래스에 `abstract`를 선언 가능한데 이럴 이유는 없다.

## 접근제어자
접근 제한 역할

- private : `같은클래스` 내에서만 접근
- default : `같은패키지` 내에서만 접근
- protected : `같은패키지`, `다른패키지 자손`에서 접근가능
   - 자식 클래스에서 상속후 사용가능하다.
- public : `접근제한없음`

## 접근 제어자를 이용한 캡슐화
- 데이터의 유효값 유지
- 클래스 내부에서 사용하는 임시변수
- 복잡성 줄임

> java파일 안에서는 하나의 public class만 존재가능

## 생성자의 접근 제어자
```java
class Singleton {
	// 인스턴스 생성
	private static Singleton s = new Singleton();
    
    // 외부에서는 인스턴스 생성을 못한다.
	private Singleton(); 
    
    // 인스턴스 생성없이 호출가능
    public static Singleton getInstance() {
    	return s;
    }
}
```
`Singleton.getInstance();`를 하면 Singleton 인스턴스를 생성하고 객체를 가져온다.

- 생성자가 전부 private면 그 클래스는 상속불가
  - 자손 클래스는 조상클래스를 호출해야하는데 호출을 못해서다.

## 제어자의 조합
1. 메서드에 `static`과 `abstract`는 동시에 사용 못한다.
	- `클래스.메서드`를 쓰면 사용이 되야하는데 `abstract`는 구현이 없다.
1. 클래스에 `abstract`와 `final`을 동시에 사용 못한다.
	- `abstract`는 상속받는용도, `final`은 상속불가능
1. `abstract`메서드의 접근제어자는 `private`일 수 없다.
	- `abstract`는 구현해야하는데 `private`를 쓰면 접근을 못한다.
1. 메서드에 `private`와 `final`은 같이 쓸 필요 없다.
	- 하나만 적어도 오버라이딩이 안된다.
    
# 다형성
여러 가지 형태를 가질 수 있는 능력
`조상클래스 타입`의 `참조변수` -> `자손클래스`의 `인스턴스`를 참조

```java
class TV { 
	boolean power;
    int channel;
    
    void power() {power=!power;}
}

class CpationTV extends TV {
	String text;
	void caption() {};
}


CaptionTV c = new CaptionTV();
Tv t = new CaptionTV(); 
CaptionTV ct = new Tv(); // 에러
```
**용어**
`Tv t = new CaptionTV(); `
- Tv : 참조변수`타입`
- t : 참조변수
- new CaptionTV() : 참조변수가 참조하는 `인스턴스`

**설명**
1. c는 `CaptionTV` + `TV` 클래스 멤버 사용가능
2. t는 `TV` 멤버만 사용가능
3. ct는 `TV`가 쓰려는 멤버보다 `CaptionTV`의 멤버가 더많아서 안된다.
4. Tv를 기준으로 멤버를 쓸수있다.


> 참조변수타입에 따라 사용할 수 있는 멤버가 다르다.
모든 참조변수는 4byte 주소값을 가진다.
조상타입의 참조변수로 자손타입의 인스턴스 참조가능
``` Tv t = new Caption(); ```
이 반대는안된다.

## 참조변수의 형변환
기본형처럼 참조형도 형변환이 가능하다.
단 상속관계만가능

- 업캐스팅 : 자손 -> 조상 (형변환 생략가능)
  - 자손이 더 많은 멤버를 가지고 있어서 가능하다.
  - ex) `자동차 = (자동차) 스포츠카`
- 다운캐스팅 : 자손 <- 조상 (형변환 생략불가)
  - 업캐스팅한걸 다시 캐스팅할때 쓰인다.
  - ex) `스포츠카 = (스포츠카) 자동차`
  - ex) Button b = (Button) view
    - 안드로이드에서 쓰인다.

![](https://velog.velcdn.com/images/bjh0501/post/e301ab50-73dd-439b-b875-2fb3bfc7a097/image.png)



```java
public class Main {
	public static void main(String[] args) {
		FireEngine f;
		Ambulance a;
		
//		a = (Ambulance)f; // 에러
//		f = (FireEngine)a; // 에러
		
		Car car = null;
		FireEngine fe = new FireEngine();
		FireEngine fe2 = null;
		car = (Car) fe; // (Car) 생략가능, 조상 <- 자손
		fe2 = (FireEngine) car;// 생략불가능, 자손 <- 조상
		fe2.color = "RED";
	}
}

class Car {
	String color;
	int door;
	void drive() {
		System.out.println("drive");
	}
	
	void stop() {
		System.out.println("stop");
	}
}

class FireEngine extends Car {
	void water() {
		System.out.println("water!");
	}
}

class Ambulance extends Car {
	void siren() {
		System.out.println("siren~");
	}
}
```
### 형변환
- 인스턴스는 변하지않는다.
- 멤버의 개수가 변경된다.
- 상속관계에서 양방향으로 수행된다.

## instanceof 연산자
```java
Car car = null;
		
if (car instanceof FireEngine) {
	FireEngine fe = (FireEngine) car;
	fe.water();
} else if (car instanceof FireEngine) {
	FireEngine fe = (FireEngine) car;
	fe.water();
}
```
- 인스턴스 타입을 체크한다.
- **조상인스턴스도 검사한다.**
- instanceof가 true면 형변환이 가능하다.

## 참조변수와 인스턴스의 연결
```java
Parent p = new Child();
Child c = new Child();

// 메서드 오버라이딩으로 둘에 결과는 같다.
p.method();
c.method();

System.out.println(p.x);
System.out.println(c.x);
```
메서드 : 둘다 Child의 method가 호출된다.
변수 : 각각의 변수가 호출된다.

### 설명
1. p, c 모두 Child인스턴스를 바라본다.
2. p, c 모두 같은 멤버들 정의한다.
3. ~~`method()`는 `실제 인스턴스`를 바라본다.~~
	- 메서드 오버라이딩된거다. (IDE로 확인가능)

## 매개변수의 다형성
```java
public class Main {
	public static void main(String[] args) {
		Buyer b = new Buyer();
		Tv tv = new Tv(); // #1
		Computer com = new Computer(); // #4
		
		b.buy(tv); // #7
		b.buy(com); // #10
		
		System.out.println("남은돈:" + b.money);
		System.out.println("보너스:" + b.bonusPoint);
	}
}


class Product {
	int price;
	int bonusPoint;
	
	// #3 #6
	public Product(int price) {
		this.price = price; 
		bonusPoint = (int)(price/10.0);
	}
}

class Tv extends Product {
	Tv() {
		super(100); // #2
	}
	
	// #9
	@Override
	public String toString() {
		return "TV";
	}
}

class Computer extends Product {
	public Computer() {
		super(200); // #5
	}
	
	// #12
	@Override
	public String toString() {
		return "Computer";
	}
}

class Buyer {
	int money = 1000;
	int bonusPoint = 0;
	
	// #8 #11
    // 업캐스팅
	void buy(Product p) {
		if(money < p.price) {
			System.out.println("잔액부족");
			return;
		}
		
		money -= p.price;
		bonusPoint += p.bonusPoint;
		System.out.println(p + "를 구입");
	}
}
```

### 동작순서
1. Tv 인스턴스생성
2. Tv 생성자 실행
3. Tv의 super를 통해 Product생성자 실행
4. Computer 인스턴스생성
5. Computer 생성자 실행
6. Computer의 super를 통해 Product생성자 실행
7. b.buy(tv) 실행
8. Buyer.buy() 실행
9. Tv의 toString()실행
10~11. 8~9반복
마지막에 출력

## 여러 종류의 객체를 하나의 배열로 다루기
```java
Product p[] = new Product[3];
p[0] = new Tv();
p[1] = new Computer();
p[2] = new Audio();
```
공통의 조상으로 배열을 다뤄야한다.

```java

public class Main {
	public static void main(String[] args) {
		Buyer b = new Buyer();
		Tv tv = new Tv();
		Computer com = new Computer();
		Audio audio = new Audio();
		
		b.buy(tv);
		b.buy(com);
		b.buy(audio);
		b.summary();
		System.out.println();
		b.refund(com);
		b.summary();
	}
}


class Product {
	int price;
	int bonusPoint;
	
	public Product(int price) {
		this.price = price; 
		bonusPoint = (int)(price/10.0);
	}
}

class Tv extends Product {
	Tv() {super(100);}
	
	@Override
	public String toString() {return "TV";}
}

class Computer extends Product {
	public Computer() {super(200); }
	
	@Override
	public String toString() {return "Computer";}
}

class Audio extends Product {
	public Audio() {super(50); }
	
	@Override
	public String toString() {return "Computer";}
}

class Buyer {
	int money = 1000;
	int bonusPoint = 0;
	Vector item = new Vector();
	
	void buy(Product p) {
		if(money < p.price) {
			System.out.println("잔액부족");
			return;
		}
		
		money -= p.price;
		bonusPoint += p.bonusPoint;
		System.out.println(p + "를 구입");
		item.add(p);
	}
	
	void refund(Product p) {
		if(item.remove(p)) {
			money += p.price;
			bonusPoint -= p.bonusPoint;
			System.out.println(p + "를 반품");
		} else {
			System.out.println("제품없음");
		}
	}
	
	void summary() {
		int sum = 0;
		String itemList = "";
		
		if(item.isEmpty()) {
			System.out.println("구입상품없음");
		}
		
		for(int i = 0; i < item.size(); i++) {
			Product p = (Product) item.get(i);
			sum += p.price;
			itemList += (i==0) ? "" + p : ", " + p;
		}
		
		System.out.println("총 " + sum + "원");
		System.out.println("구입제품 " + itemList + "임");
	}
}
```
TV, 오디오, 컴퓨터를 객체에 저장해서 구매자가 지정된 액션을 하는 예제
객체지향의 완벽한 예제인것같다.

# 추상클래스
- 미완성 설계도
- 상속받아서만 완성됨
- 조상클래스로서 중요한 의미를 갖음

## 추상메서드
- 미완성메서드
- 실제 수행될 내용은 없음
- 어떤 기능인지 메서드제목과 주석으로 작성후 상속받은곳에서 구현하도록한다.

```java
abstract class Player {
	abstract void play(int pos);
	abstract void stop();
}

class AudioPlayer extends Player {
	@Override
	void play(int pos) { }

	@Override
	void stop() { }
}

abstract class AbstractPlayer extends Player { }
```
구현부분만큼이나 `메서드이름, 매개변수 , 타입도 중요`해서 추상메서드를 쓰는거다.

## 추상클래스의 작성
기존의 클래스에서 공통부분을 뽑아서 조상클래스를 만드는것.
상속은 위와 반대다.

- 추상화 : 클래스간의 공통점의 조상을 만듬
- 구체화 : 상속을 통해 클래스를 구현

```java
abstract class Player {
	boolean pause;
	int currentPos;
	
	// 생성자
	Player() {
		pause = false;
		currentPos = 0;
	}
	
	// 추상메서드, 필수로입력해야함
	abstract void play(int pos);
	abstract void stop();
	
	void play() {
		play(currentPos);
	}
	
	// 일반메서드
	void pause() {
		if(pause) {
			pause= false;
			play(currentPos);
		} else {
			pause = true;
			stop();
		}
	}
}

class CDPlayer extends Player {
	@Override
	void play(int pos) {}

	@Override
	void stop() { }	
	
	int currentTrack;
	
	void nextTrack() { currentTrack ++;}
	
	void preTrack() { 
		if(currentTrack > 1) {
			currentTrack --;
		}	
	}	
}
```
`play`와 `stop`은 필수로 작성해야한다.

```java
// 스타크래프트 유닛 클래스
abstract class Unit {
	int x, y;
	// 공중과 지상 공통 move이름
	// 공중과 지상이 움직임이 달라서 abstract로 한다. 
	abstract void move(int x, int y);
	
	// 예제는 일반메서드지만
	// 공중은 멈출때 가속도가 붙어서 abstract로 한다.
	abstract void stop();
}

class Marine extends Unit {
	void move(int x, int y) { }
	// 추상 메서드가 일반메서드였다면 오버라이딩된다.
	void stop() { } // 즉시 stop
}

class Dropship extends Unit {
	void move(int x, int y) { }
	void stop() { } // 가속도붙은 stop
	void load() { }
	void unload() { }
}
```
추상클래스 예제

# 인터페이스
- 추상클래스보다 추상화가 높다.
- 추상클래스는 일반메서드허용, 인터페이스는x
- `추상메서드`와 `상수`만 허용
- 추상클래스는 절반작성된 클래스, 인터페이스는 밑그림만 되있는 클래스
- 다른 클래스 작성을 도움주는데 사용

## 인터페이스 작성
```java
interface 인터페이스이름 {
	public static final 타입 상수이름 = 값;
    public abstract 메서드이름();
}
```
- 인터페이스의 접근제어자 `public`, `default`만 가능
- 인터페이스 있는 `모든 메서드`는 `public abstract`다. (생략가능)
- `모든 타입`은 `	public static final`이다. (생략가능)
- 모든 멤버에 적용되는거라 생략이 가능하다.

## 인터페이스의 상속
- 인터페이스는 인터페이스 끼리만 상속가능
- 다중상속 가능 `implements` 키워드사용
- interface는 `최고조상(Object)`이 없다. 

## 인터페이스의 구현
```java
abstract class Fighter implements Fightable {
	public void move(){}
}
```
위처럼 구현도 할수 있다.

> 인터페이스 이름은 `~을 할 수있다.` 의미인 `able`로 쓴다.

- 인터페이스는 상속대신 `구현`이라는 용어를 쓴다.
  - 구현체
- 인터페이스에서 상속되면 접근제어자는 `public`만 써야한다.
  - 상속받으면 부모 접근제어자보다 낮출수 없다.


## 인터페이스를 이용한 다중 상속
- 다중상속을 받았을때 멤버변수나 메서드명이 같으면 충돌난다.
  - 하나의 상속을 포기하던가 이름을 변경한다.
- 인터페이스는 다중상속이 된다.
  - `static final변수`라 충돌이 피해진다.
  - `구현부가 없는 메서드`라 충돌이 피해진다.
    - 이름이 같으면 상위조상의 메서드를 가져온다.
  - 하지만 잘 사용하지 않는다.

## 인터페이스를 이용한 다형성
자손클래스의 인스턴스를 조상타입의 변수로 참조가 가능하다.

```java
Fightable f = (Fightable) new Fighter();
Fightable f = new Fighter();
```

```java
void attack(Fighter f) {}
```
매개변수로도 가능하다.

```java
public class Main {
	public static void main(String[] args) {
		Parseable parser = ParseManager.getParser("XML");
		parser.parse("doc.xml");
		
		parser = ParseManager.getParser("HTML");
		parser.parse("doc2.html");
	}
}

interface Parseable {
	void parse(String fileName);
}

class XMLParser implements Parseable {
	@Override
	public void parse(String fileName) {
		System.out.println(fileName + "- XML parsing");
	}	
}

class HTMLParser implements Parseable {
	@Override
	public void parse(String fileName) {
		System.out.println(fileName + "- HTML parsing");
	}	
}

class ParseManager {
	public static Parseable getParser(String type) {
		if(type.equals("XML")) {
			return new XMLParser();
		} else {
			Parseable p = new HTMLParser();
			return p;
		}
	}
}
```

> 위와같은 코드에서 XMLParser->NewXMLParser로 변경되는게아닌 JSON형식이 추가된다면 Json클래스생성과 ParseManager클래스에 조건문으 하나 더 추가할지 설계가 잘못된건지 의문이다.

## 인터페이스의 장점
### 개발시간 단축
- 메서드 이름만 보고 어떻게 구현할지를 알 수 있다.
- 호출쪽에서는 구현이 안되있어도 바로 호출이 가능하다.
- A->B 개발이 아닌 A,B 동시개발이 가능하다.

### 표준화가능
- 인터페이스 규칙을 따라야해서 표준화가 된다.

### 관계기능
- 서로 다른 조상클래스여도 관계가 맺어진다.
- 공통된 기능으로 관계를 맺는다.

### 독립적인 프로그래밍
- `클래스<->클래스`가 아닌 `클래스->인터페이스<-클래스`관계다.
- 하나의 클래스가 변경되어도 관련된 다른 클래스에 영향을 안미친다.

![](https://velog.velcdn.com/images/bjh0501/post/bce9ae59-4e8e-44b5-ab8b-2718d74d4000/image.png)
- 회색 : 인터페이스
- 하얀색 : 클래스


- 인터페이스먼저 구현을하면 여러사람이 마린, SCV, 탱크, 드랍쉽을 한번에 만들수 있다.
- _~~하지만 인터페이스를 잘못구현하면 망한다.~~_

> 위 코드에서 건물까지 합쳐진 코드를 나중에 직접 짜봐야겠다.

## 인터페이스의 이해
- `클래스를 사용하는쪽`, `클래스를 제공하는쪽`이 있음
- 메서드를 사용하는 쪽은 메서드의 선언부만 알면된다.
  - 내용은 몰라도된다.

### 용어
사용하는쪽 : user
사용하려는 메서드 : provider


```java
public class Main {
	public static void main(String[] args) {
		A a = new A();
		a.a(new B());
	}
}

class A {
	public void a(B b) {
		b.b();
	}
}

class B {
	public void b() {
		System.out.println("call");
	}
}
```
위코드는 A-B가 직접적인 관계가있다.
- `B(provider)`가 변경되면 `A(user)`도 변경되야한다.
- 직접적인 관계가 없게하려면 `B(provider)`를 변경해야한다.

```java
public class Main {
	public static void main(String[] args) {
		A a = new A();
		a.a(new B());
	}
}

class A {
	public void a(I i) {
		i.b();
	}
}

class B implements I{
	public void b() {
		System.out.println("call");
	}
}

interface I {
	void b();
}
```
- 이젠 인터페이스에 코드를 표준시켜서 A는 바꿀일이 없다.
- 코드는 B를 변경해야한다.
> C, D, E가 추가되서 A에 선언 후 C, D, E가 변경되도 A는 변경을 안해도된다.

```java
public class Main {
	public static void main(String[] args) {
		A a = new A();
		a.a();
	}
}

interface I {
	void b();
}

class A {
	public void a() {
		I i = InstanceManager.getInstance();
		i.b();
	}
}

class B implements I{
	public void b() {
		System.out.println("call");
	}
}

class InstanceManager {
	public static I getInstance() {
		return new B();
	}
}
```
위 코드에서 매개변수 대신 instance를 바로 얻어서 사용한다.
JDBC의 DriverManager클래스가 위처럼 생겼다.

> ## 정리
### 상속할때 팁
- 상속 (a는 b다.)
- 포함 (a는 b를 가지고있다.)
### object클래스 - 모든 클래스의 조상
### 형변환은 상속관계에서 양방향으로 수행
### 추상화 : 클래스간의 공통조상
### 추상클래스보다 인터페이스가 더 추상적이다.
### 인터페이스는 선언부만 알고 내용은 몰라도 된다.

