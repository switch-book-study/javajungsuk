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
