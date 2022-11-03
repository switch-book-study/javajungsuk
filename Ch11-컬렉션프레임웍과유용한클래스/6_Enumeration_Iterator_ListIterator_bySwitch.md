- _Enumeration, Iterator, ListIterator 모두 컬렉션에 저장된 요소를 접근하는데 사용되는 인터페이스다._
- _Enumeration은 Iterator의 구버전이며 ListIterator는 Iterator의 기능을 향상시킨것이다._

## Iterator
  ```
  컬렉션 프레임웍에서는 컬렉션에 저장된 요소들을 읽어오는 방법을 표준화하였으며
  컬렉션에 저장된 각 요소에 접근하는 기능을 가진 Iterator인터페이스를 정의하고
  Collection 인터페이스에는 Iterator를 반환하는 iterator()를 정의하고있다.
  ```
  ```java
  public interface Iterator {
    boolean hasNext();
    Object next();
    void remove();
  }
  public interface Collection {
    ...
    public Iterator iterator();
    ...
  }
  ```
  - ![image](https://user-images.githubusercontent.com/95848796/199734477-9e23eee8-9b73-4582-b356-24089ea2a84f.png)
  - https://www.geeksforgeeks.org/iterators-in-java/
