## Generics
  - 타입 안정성을 제공한다.
  - 타입체크와 형변환을 생략할 수 있으므로 코드가 간결해 진다.
  ```java
  다형성을 사용해야하는경우 조상타입을 지정하면 된다.
  ex) ArrayList<조상타입> list = new ArrayList<>();
  ```
  ```java
  조상타입 또는 그 자손들을 매개변수로 사용하고자 한다면 와일드카드를 활용한다.
  ArrayList<? extends 조상타입> list
  ```
  
