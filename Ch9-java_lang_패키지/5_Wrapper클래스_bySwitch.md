## Wrapper 클래스
  - 기본형값들을 객체로 변환하여 작업을 할 경우 wrapper클래스를 이용한다.
  - 자료형 이름의 첫 글자를 대문자로 한것이 각 wrapper클래스의 이름이다. (int, char 제외)
  - wrapper 클래스는 모두 equals()가 오버라이딩 되어있어서 주소값이아닌 객체가 가지고 있는 값을 비교한다.
  ```java
  public final class Integer extends Number implements Comparable {
    ...
    private int value;
    ...
  }
  ```
  - ![image](https://user-images.githubusercontent.com/95848796/198889963-92d9356e-832e-4c01-a572-f2cfde63ec81.png)
  - https://www.geeksforgeeks.org/wrapper-classes-java/
