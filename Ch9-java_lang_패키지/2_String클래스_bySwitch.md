## String클래스
  - 문자열을 저장하기 위해서 문자형 배열 변수(char[]) value를 인스턴스변수로 정의해놓고있다.
  - 인스턴스 생성 시 생성자의 매개변수로 입력받는 문자열은 인스턴스변수에 문자형 배열로 저장되는것이다.
  ```java
  public final class String implements java.io.Serializable, Comparable {
    /** The value is used for character storage. */
    private char[] value;
    ...
  }
  ```
  ```
  한번 생성된 String인스턴스가 갖고있는 문자열은 읽어올수만있고 변경할수는 없다.
  + 연산자를 이용해서 문자열을 결합하는경우 인스턴스 내의 문자열이 바뀌는것이 아니라
  새로운 문자열이 담긴 String인스턴스가 생성되는것이다.
  ```
  - +연산자를 이용해서 문자열을 결합하는것은 매 연산시마다 새로운 문자열을가진 String인스턴스가 생성되어 메모리공간을 차지하게되므로 결합횟수를 줄이는것이 좋다.
  - 문자열간 결합이나 추출등 문자열을 다루는 작업이 많이 필요한경우 StringBuffer클래스를 사용하는 것이 좋다.
  - StringBuffer인스턴스에 저장된 문자열은 변경이 가능하기때문이다.
  ```
  String클래스의 intern()은 String인스턴스의 문자열을 constant pool에  등록하는일을한다.
  등록하고자 하는 문자열이 constant pool에 이미 존재하는 경우에는 그 문자열의 주소값을 반환한다.
  ```
