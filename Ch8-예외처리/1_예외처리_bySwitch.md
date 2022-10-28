## 프로그램 오류
  - 자바에서는 실행시 발생할 수 있는 오류를 에러와 예외 두가지로 구분한다.
  - 에러는 메모리부족이나 스택오버플로우와같이 심각한 것들이고 예외는 발생하더라도 수습될수있는 비교적 덜 심각한 것이다.
  ```
  에러 - 프로그램 코드에 의해서 수습될 수 없는 심각한 오류
  예외 - 프로그램 코드에 의해서 수습될 수 있는 다소 미약한 오류
  ```
---
<br>


## 예외처리의 정의와 목적 
 ```
 정의 - 프로그램 실행 시 발생할 수 있는 예외의 발생에 대비한 코드를 작성하는 것
 목적 - 프로그램의 비정상 종료를 막고, 정상적인 실행상태를 유지하는것
 ```
---
<br>


 
## 예외처리 구문 try-catch
  ```java
  try {
  } catch (Exception1 e1) {
  } catch (Exception2 e2) {
  } ....
 ```
---
<br>


## try-catch 문에서의 흐름
  ```
  try블럭 내에서 예외가 발생한 경우
  1. 발생한 예외와 일치하는 catch블럭이 있는지 확인한다.
  2. 일치하는 catch블럭을 찾게되면 그 catch블럭 내의 문장들을 수행하고 전체 try-catch문을 빠져나가서 그 다음 문장을 계속해서 수행한다.
     만일 일치하는 catch블럭을 찾지 못하면 예외는 처리되지 못한다.
  
  try블럭 내에서 예외가 발생하지 않은경우
  1. catch블럭을 거치지않고 try-catch문을 빠져나가서 수행을 계속한다.
  ```
---
<br>

  
## 예외 발생시키기
  ```java
  //연산자 new를 이용해 발생시키려는 예외클래스의 객체를 만든다음
  Exception e = new Exception();
  //throw를 이용해서 예외를 발생시킨다.
  throw e;
  ```
 ---
<br>

 
## 예외 클래스의 계층구조
  - Exception과 Error클래스 역시 Object클래스의 자손이다.
  - ![image](https://user-images.githubusercontent.com/95848796/198651178-361e6ce2-b54a-4400-9d07-2e0075dd9e8d.png)
  - ![image](https://user-images.githubusercontent.com/95848796/198651654-f9d17f0f-020f-4901-a0fc-57b642103655.png)
  ```
  RuntimeException클래스들 - 프로그래머의 실수로 발생하는 예외
  Exception클래스들 - 사용자으 ㅣ실수와 같은 외적인 요인에 의해 발생하는 예외
  ```
  ```
  RuntimeException클래스들 그룹에 속하는 예외가 발생할 가능성이 있는 코드에는
  예외처리를 해주지 않아도 컴파일시에 문제가 되지 않지만,
  Exception클래스들 그룹에 속하는 예외가 발생할 가능성이 있는 예외는
  반드시 처리를 해줘야하며 그렇지 않으면 컴파일시 에러가 발생한다.
  ```
 ---
<br>

 
## 예외 발생과 catch 블럭
  - 예외가 발생하면 발생한 예외에 해당하는 클래스의 인스턴스가 만들어진다.
  - 이후 예외를 처리할 수 있는 catch 블럭이 있는지 찾게된다.
  ```
  printStackTrace() - 예외발생 당시의 호출스택(Call Stack)에 있었던 메서드의 정보와 예외 메시지를 화면에 출력한다.
  getMessage() - 발생한 예외클래스의 인스턴스에 저장된 메시지를 얻을 수 있다.
  ```
---
<br>

  
## 메서드에 예외 선언하기
  - 메서드 선언부에 키워드 throws를 사용
  ```java
  void method() throws Exception1, Exception2, ... ExceptionN {
  }
  ```
  - @SneakyThrows 어노테이션으로 몰래?던지기도 가능함

---
<br>


## 예외 되던지기 exception re-throwing
  - 하나의 예외에 대해 예외가 발생한 메서드와 이를 호출한 메서드 양쪽 모두에서 처리해줘야할때 사용된다.

---
<br>


## 사용자정의 예외만들기
  ```java
  class MyException extends Exception {
    MyException(String msg) { //문자열을 매개변수로 받는 생성자
      super(msg); //조상인 Exception클래스의 생성자를 호출한다.
    }
  }
  ```
