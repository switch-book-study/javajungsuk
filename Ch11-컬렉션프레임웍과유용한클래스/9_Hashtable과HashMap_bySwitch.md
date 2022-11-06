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
  
## 해싱
  - 해시함수를 이용해서 데이터를 해시테이블에 저장하고 검색하는 기법이다.
  - 해시함수는 데이터가 저장되어있는곳을 알려주기때문에 다량의 데이터중에서도 원하는 데이터를 빠르게 찾을 수 있다.
  - 해싱에서 사용하는 자료구조는 배열과 링크드리스트의 조합으로 되어있다.
  - ![image](https://user-images.githubusercontent.com/95848796/200164557-fa080beb-d344-41db-9132-5721416fe1a3.png)
