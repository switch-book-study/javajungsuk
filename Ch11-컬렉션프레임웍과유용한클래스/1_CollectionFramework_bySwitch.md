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
  ---
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
---
<br>


  ### Collection 인터페이스
   - ![image](https://user-images.githubusercontent.com/95848796/199273657-359e5d01-cf0d-46f6-8d85-8ec299c228ea.png)
   - https://www.benchresources.net/collection-interface-in-java/
 ---
<br>

 
  ### List 인터페이스
   - 

