## start()와 run()
  - run()을 호출하는 것은 생성된 쓰레드를 실행시키는 것이 아니라 단순히 클래스에 속한 메서드 하나를 호출하는 것이다.
  - start()는 새로운 쓰레드가 작업을 실행하는데 필요한 호출스택을 생성한 다음에 run()을 호출해서 생성된 호출스택에 run()이 첫번째로 저장되게 한다.
  ```
  1. main메서드에서 쓰레드의 start메서드를 호출한다.
  2. start메서드는 쓰레드가 작업을 수행하는데 사용될 새로운 호출스택을 생성한다.
  3. 생성된 호출스택에 run메서드를 호출해서 쓰레드가 작업을 수행하도록 한다.
  4. 이제는 호출스택이 2개이기때문에 스케줄러가 정한 순서에 의해서 번갈아 가면서 실행된다.
  ```
  ```
  실행 중인 사용자쓰레드가 하나도 없을 때 프로그램은 종료된다.
  ```
  - 쓰레드는 사용자(user)쓰레드와 데몬(daemon)쓰레드 두 종류가 있다.
