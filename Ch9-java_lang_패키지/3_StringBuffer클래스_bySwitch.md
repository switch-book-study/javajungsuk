## StringBuffer 클래스
  ```
  String 클래스는 인스턴스를 생성할 때 지정된 문자열을 변경할 수 없지만
  StringBuffer 클래스는 변경이 가능하다.
  ```
  - 내부적으로 문자열 편집을 위한 버퍼(buffer)를 가지고 있으며 인스턴스생성시 그 크기를 지정할 수 있다.
  ```java
  public final class StringBuffer implements java.io.Serializable
  {
    private char[] value;
    ...
  }
  ```
---
<br>

  
## StringBuffer 클래스의 생성자
  - 인스턴스를 생성할때 적잘한 크기의 char형 배열이 생성되고 이 배열은 문자열을 저장하고 편집하기 위한 공간(buffer)으로 사용된다
  ```java
  public StringBuffer(int length) {
    value = new char[length];
    shared = false;
  }
  
  public StringBuffer() {
    this(16); //버퍼의 크기를 지정하지 않으면 버퍼의 크기는 16이 된다.
  }
  
  public StringBuffer(String str) {
    this(str.length() + 16);  //지정한 문자열의 길이보다 16이 더 크게 버퍼를 생성한다.
    append(str);
  }
  ```
---
<br>

    
## StringBuffer 인스턴스의 비교
  ```
  String클래스와 달리 StringBuffer클래스는 equals메서드를 오버라이딩 하지않아서 
  StringBuffer클래스의 equals메서드를 사용해도 == 연산자로 비교한것과 같은 결과를 얻는다.
  
  StringBuffer인스턴스에 담긴 문자열을 비교하기위해서는
  toString을 호출해서 Stirng인스턴스를 얻은다음 equals메서드를 사용하여 비교한다.
  ```
