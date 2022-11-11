## synchronized를 이용한 동기화
  ```
  synchroized를 통해 해당작업과 관련된 공유데이터에 락을걸어서
  먼저 작업중이던 쓰레드가 작업을 완전히마칠때까지는
  다른쓰레드에게 제어권이 넘어가더라도 데이터가 변경되지 않도록 보호함으로써
  쓰레드의 동기화를 가능하게한다.
  ```
  ```java
  1. 특정 객체에 lock을 걸고자 할 때 
    synchronized(객체의 참조변수) {
      //...
    }
  2. 메서드에 lock을 걸고자할 때
    public synchronized void calcSum() {
      //...
    }
  ```
  ```
  주의사항
  dead lock 상황이 될 수 있다.
  ```
  
## wait()과 notify()
  - 동기화 효율을 높이기위해 사용한다.
  ```
  wait(), notify(), notifyAll()
  - Object에 정의되어있다.
  - 동기화 블록 내에서만 사용할 수 있다.
  - 보다 효율적인 동기화를 가능하게한다.
  ```
  - ![image](https://user-images.githubusercontent.com/95848796/201361156-4d487148-e093-4104-b110-f2d9f63a1ac1.png)
  - https://www.baeldung.com/java-wait-notify

  
