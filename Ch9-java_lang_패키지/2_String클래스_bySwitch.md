## toString 메서드
  - 인스턴스에 대한 정보를 문자열로 제공할 목적으로 정의한것이다.
  ```java
  //Object 클래스에 정의된 toString()
  public String toString() {
    return getClass().getName() + "@"
      + Integer.toHexString(hashCode());
  }
  ```
  - 오버라이딩하지않은 Object클래스의 toString()을 호출하면 클래스이름에 16진수의 해시코드값을 얻게된다.
  - 해시코드는 인스턴스의 주소와 관련된 값으로, 서로다른인스턴스는 서로 다른 해시코드값을 가질 것을 보장한다.
