## Comparator와 Comparable
  - 정렬 또는 이진검색트리를 구성하는데 필요한 메서드를 정의하고있다.
  ```
  Comparable - 기본 정렬기준을 구현하는데 사용.
  Comparator - 기본 정렬기준 외에 다른기준으로 정렬하고자할 때 사용
  
  Comparable을 구현한 클래스들이 기본적으로 오름차순으로 정렬되어 있지만,
  내림차순으로 정렬한다던가 아니면 다른 기준에 의해서 정렬되도록 하고싶을때
  Comparator를 구현해서 정렬기준을 제공할수있다.
  ```
  ```java
  public interface Comparator {
    int compare(Object o1, Object o2);
    boolean equals(Object obj);
  }
  
  public interface Comparable {
    public int CompareTo(Object o);
  }
  ```
  
