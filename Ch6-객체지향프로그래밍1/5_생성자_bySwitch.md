## 생성자란?
  - 생성자는 인스턴스가 생성될 때 호출되는 인스턴스 초기화 메서드이다.
  - 생성자도 메서드처럼 클래스 내에 선언되고 구조도 메서드와 유사하지만 리턴값이 없다.
  ```
  생성자의 이름은 클래스의 이름과 같아야한다.
  생성자는 리턴값이 없다.
  하나의 클래스에 여러개의 생성자가 있을 수 있다 (오버로딩 가능)
  ```
  ```java
  클래스이름(타입 변수명, 타입 변수명, ... ) {
    //인스턴스 생성 시 수행될 코드,
    //주로 인스턴스 변수의 초기화 코드를 적는다.
  }
  ```
  - 생성자는 단순히 인스턴스변수들의 초기화에 사용되는 메서드일뿐 생성자가 인스턴스를 생성하는것은 아니다.
  ```java
  Card card = new Card();
  1. 연산자 new에 의해서 메모리(heap)에 Card클래스의 인스턴스가 생성된다.
  2. 생성자 Card()가 호출되어 수행된다.
  3. 연산자 new의 결과로, 생성된 Card인스턴스의 주소가 반환되어 참조변수 card에 저장된다.
  ```
---
<br>


## 기본 생성자 (default constructor)
  - 컴파일할때 소스파일(.java)의 클래스에 생성자가 하나도 정의되지 않은 경우 컴파일러는 자동적으로 기본생성자를 추가하여 컴파일한다.
  ```
  클래스이름() { }
  ```
  - 컴파일러가 자동적으로 추가해주는 기본생성자는 매개변수도없고 아무런내용도없는 간단한것이다.
  - 기본생성자가 컴파일러에 의해서 추가되는 경우는 클래스에 정의된 생성자가 하나도 없을때 뿐이다.
---
<br>


## 매개변수가 있는 생성자
  - 생성자도 메서드처럼 매개변수를 선언하여 호출 시 값을 넘겨받아서 인스턴스의 초기화작업에 사용할 수 있다.
---
<br>


## 생성자에서 다른 생성자 호출하기 ( this(), this )
  - 생성자간에도 서로 호출이 가능하다
  ```
  - 생성자의 이름으로 클래스이름 대신 this를 사용한다
  - 한 생성자에서 다른 생성자를 호출할 때는 반드시 첫줄에서만 호출이 가능하다.
  ```
  ```
  - this - 인스턴스 자신을 가리키는 참조변수, 인스턴스의 주소가 저장되어있다.
           모든 인스턴스메서드에 지역변수로 숨겨진 채로 존재한다.
  - this(), this(매개변수) - 생성자, 같은 클래스의 다른 생성자를 호출할때 사용한다.
  ```
