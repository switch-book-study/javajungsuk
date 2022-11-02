## 동기화 (Synchronization)
  - 멀티쓰레드환경에서(한 객체를 여러 쓰레드가 동시에 접근) 데이터의 일관성을 유지하기위해서 동기화가 필요하다.
  - Vector와 Hashtable과 같은 구버전의 클래스들은 자체적으로 동기화 처리가 되어있는데, 멀티쓰레드 프로그래밍이 아닌 경우에는 불필요한기능이되어 성능이 저하된다.
  - `ArrayList와 HashMap` 같은 컬렉션은 동기화를 자체적으로 처리하지않고 `필요한경우만 java.util.Collections클래스의 동기화 메서드`를 이용해서 동기화처리가 가능하도록 변경되었다.
  ```java
  static Collection synchronizedCollection(Collection c)
  sattic List synchronizedList(List list)
  static Map synchronizedMap(Map m)
  static Set synchronizedSet(Set s)
  static SortedMap synchronizedSortedMap(SortedMap m)
  static SortedSet synchronizedSortedSet(SortedSet s)
  ```
  - 사용시
  ```java
  List list = Collections.synchronizedList(new ArrayList(...));
  ```
