## Hashtable과 HashMap
  - Hashtable보단 새버전인 HashMap을 권장
  - Map을 구현했으므로 키벨류를 묶어 저장한다.
  - 해싱을 사용하기때문에 많은 양의 데이터를 검색하는데 있어서 뛰어난 성능을 가지고있다.
  ```java
  public class HashMap extends AbstractMap implements Map, Cloneable, Serializable {
    transient Entry[] table;
    ...
    static class Entry implements Map.Entry {
      final Object key;
      Object value;
      ...
    }
  }
  ```
  ```
  HashMap은 Entry라는 내부클래스를 정의하고 다시 Entry타입의 배열을 선언하고있다.
  키 벨류는 별개의 값이 아니라 서로 관련된 값이기 때문에
  하나의 클래스로 정의해서 하나의 배열로 다루는것이 데이터의 무결성적인 측면에서 더 바람직하다.
  ```
  ```
  key - 컬렉션 내의 키 중에서 유일해야한다.
  value - 키와 달리 데이터의 중복을 허용한다.
  ```
  
