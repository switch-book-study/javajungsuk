## HashSet
  - Hashset은 Set인터페이스를 구현한 대표적인 컬렉션이다.
  - HashSet은 저장순서를 유지하지 않으므로 유지하고자한다면 LinkedHashSet을 사용해야한다.

## TreeSet
  - 이진검색트리(binary search tree) 자료구조의 형태로 데이터를 저장하는 컬렉션이다.
  - TreeSet은 이진검색트리의 성능을 향상시킨 Red-Black tree로 구현되어있다.
  - 중복된 데이터의 저장을 허용하지 않으며 정렬된 위치에 저장하므로 저장순서를 유지하지도 않는다.
  - ![image](https://user-images.githubusercontent.com/95848796/200023523-b624c9b9-9491-4326-b69f-d2067f172e34.png)
  - https://www.geeksforgeeks.org/binary-tree-data-structure/
  ```java
  class TreeNode {
    TreeNode left;  //왼쪽 자식노드
    Object element; //객체를 저장하기 위한 참조변수
    TreeNode right; //오른쪽 자식노드
  }
  ```
  ```
  이진검색트리(binary search tree)
  - 모든 노드는 최대 두 개의 자식노드를 가질 수 있다.
  - 왼쪽 자식노드의 값은 부모노드의 값보다 작고 오른쪽자식노드의 값은 부모노드의 값보다 커야한다.
  - 노드의 추가 삭제에 시간이 걸린다 (순차적으로 저장하지 않으므로)
  - 검색과 정렬에 유리하다
  ```
  
