## 컬렉션 프레임워크 핵심 인터페이스 - List, Set, Map
  - 크게 List, Set, Mep 이라고 정의
  ```
  - 컬렉션 프레임웍의 핵심 인터페이스간의 상속 계층도
  
  List -> Collection <- Set
  
  Map
  
  List와 Set을 구현한 컬렉션클래스들은 서로 많은 공통부분이 있어서
  공통된부분을 다시 뽑아 Collection인터페이스를 정의할 수 있었지만
  Map인터페이스는 이들과는 전혀 다른형태로 컬렉션을 다루기때문에
  같은 상속계층도에 포함되지 못했다.
  ```
  
  ```
  List 
  - 순서가 있는 데이터의 집합.
  - 데이터의 중복을 허용한다.
  - 구현클래스: ArrayList, LinkedList, Stack, Vector  ...
  ```
  ```
  Set
  - 순서를 유지하지 않는 데이터의 집합.
  - 테이터의 중복을 허용하지 않는다.
  - 구현클래스: HashSet, TreeSet ...
  ```
  ```
  Map
  - 키 벨류의 쌍으로 이루어진 데이터의 집합.
  - 순서는 유지되지 않는다.
  - 키는 중복을 허용하지 않고 값은 중복을 허용한다.
  - 구현클래스: HashMap, TreeMap, Hashtable, Properties ...
  ```
  
  ### Collection 인터페이스
   - ![image](https://user-images.githubusercontent.com/95848796/199273657-359e5d01-cf0d-46f6-8d85-8ec299c228ea.png)
   - https://www.benchresources.net/collection-interface-in-java/
   ```
   List 인터페이스
   - 중복허용하면서 저장순서가 유지되는 컬렉션을 구현할때 주로사용한다.
   ```
   ```
   Set 인터페이스
   - 중복을 허용하지 않고 저장순서가 유지되지않는 컬렉션 구현시 사용된다.
   ```
   ```
   Map 인터페이스
   - 키벨류를 하나의 쌍으로 묶어 구현한다. 키는 중복이 안된다.
   ```
   ```java
   Map.Entry 인터페이스
   - Map인터페이스의 내부 인터페이스이다
   - 내부클래스와 같이 인터페이스도 인터페이스 안에 인터페이스를 정의하는 내부인터페이스를 정의하는것이 가능하다.
   - 보다 객체지향적으로 설계하도록 유도하기 위한것
   - Map 인터페이스를 구현하는 클래스에서는 Map.Entry인터페이스도 함께 구현해야한다.
   
   // Map 인터페이스의 소스코드 일부
   public interface Map {
    ...
    interface Entry {
      Object getKey();
      Object getValue();
      Object setValue(Obect value);
      Boolean equals(Object o);
      int hashCode();
    }
  }
  ```
---
<br>

## 동기화 (Synchronization)
  - 멀티쓰레드환경에서(한 객체를 여러 쓰레드가 동시에 접근) 데이터의 일관성을 유지하기위해서 동기화가 필요하다.
  - Vector와 Hashtable과 같은 구버전의 클래스들은 자체적으로 동기화 처리가 되어있는데, 멀티쓰레드 프로그래밍이 아닌 경우에는 불필요한기능이되어 성능이 저하된다.
  - `ArrayList와 HashMap` 같은 컬렉션은 동기화를 자체적으로 처리하지않고 `필요한경우만 java.util.Collections클래스의 동기화 메서드`를 이용해서 동기화처리가 가능하도록 변경되었다.
  - 
