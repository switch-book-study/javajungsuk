## Calendear 와 Date
  - 가능한 Date 보다는 Calendear를 사용하는것이 좋다.
  - 간단한 날짜처리에는 Date를 사용하는것이 나을 수 있다.
  ```java
  1. Calendar to Date
  Calendar cal = Calendar.getInstance();
  ...
  Date d = new Date(cal.getTimeInMillis()); //Date(long date)
  
  2. Date to Calendar
  Date d = new Date();
  ...
  Calendar cal = Calendar.getInstance();
  cal.setTime(d);
  ```
  - Calendar는 추상클래스기때문에 직접 객체를 생성할 수 없고, 메서드를 통해서 완전히 구현된 클래스의 인스턴스를 얻어야 한다.
  ```java
  Calendar cal = new Calendar(); // Err 추상클래스는 인스턴스를 생성할수없다.
  
  Calendar cal = Calendar.getInstance();  // Ok . getInstance()메서드는 Calendar 클래스를 구현한 클래스의 인스턴스를 반환한다.
  ```
  
