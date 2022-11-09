## 쓰레드의 구현과 실행
  - Thread 클래스를 상속받는 방법과 Runnable 인터페이스를 구현하는 방법으로 쓰레드를 구현한다.
  - 일반적으로 Runnable인터페이스를 구현하는 방법이 일반적이다. (재사용성이 높고 일관성을 유지할 수 있어서 보다 객체지향적인 방법이다.)
  ```java
  1. Thread클래스를 상속
  class MyThread extends Thread {
    public void run() { ... } // Thread클래스의 run()을 오버라이딩
  }
  
  2. Runnable 인터페이스 구현
  class MyThread implements Runnable {
    public void run() { ... } // Runnable 인터페이스의 추상메서드 run()을 구현
  }
  ```
  
  
