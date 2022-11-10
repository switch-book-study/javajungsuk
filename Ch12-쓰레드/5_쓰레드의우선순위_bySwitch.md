## 쓰레드의 우선순위
  - 쓰레드는 우선순위라는 속성을 가지고있다.
  - ![image](https://user-images.githubusercontent.com/95848796/201106069-437ac245-6a5c-47d0-be60-36a6bdfb352d.png)
  - 우선순위가 높은쪽에 더 많은양의 실행시간이 주어지고 더 빨리 작업이 완료될 수 있다.
  ```java
  void setPriority(int newPriority) : 쓰레드의 우선순위를 지정한 값으로 변경한다.
  int getPriority() : 쓰레드의 우선순위를 반환한다.
  ```
  ```
  쓰레드의 우선순위는 1~10의 범위를 가지고 숫자가 높을수록 우선순위가 높다.
  ```
