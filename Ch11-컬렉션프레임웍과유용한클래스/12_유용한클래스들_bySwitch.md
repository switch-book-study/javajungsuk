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
---
<br>


## Random
  - Ramdom보다는 Math.random()을 사용하는것이 권장된다.

---
<br>


## 정규식(Regular Expression) - Pattern, Match
  - 정규식이란 텍스트 데이터 중에서 원하는 조건과 일치하는 문자열을 찾아내기 위해 사용하는것이다.
  - 많은 양의 텍스트 파일 중에서 원하는 데이터를 손쉽게 뽑아낼 수도 있고 입력된 데이터가 형식에 맞는지 체크할 수도 있다.
  ```java
  import java.util.regex.*;
  
  class RegularExample {
    public static void main(String[] args) {
      String[] data = {"bat", "baby", "cat" ... };
      Pattern p = Pattern.complie("c[a-z]*"); //c로 시작하는 소문자영단어
      
      for (int i=0; i < data.length; i++) {
        Matcher m = p.matcher(data[i]);
        if(m.matches())
          System.out.print(data[i] + ",");
      }
    }
  }
  ```
  ```
  1. 정규식을 매개변수로 Pattern 클래스의 static메서드인 Pattern compile(String regex)을 호출하여 Pattern인스턴스를 얻는다.
  Pattern p = Pattern.compile("c[a-z]*");
  
  2. 정규식으로 비교할 대상을 매개변수로 Pattern클래스의 Matcher matcher (CharSequence input)를 호출해서 Matcher인스턴스를 얻는다.
  Matcher m = p.matcher(data[i]);
  
  3. Matcher인스턴스에 boolean matches()를 호출해서 정규식에 부합하는지 확인한다.
  if(m.matches())
  ```
  - ![image](https://user-images.githubusercontent.com/95848796/200343537-b9413e3c-58c8-4551-8513-6b5eac9acb70.png)

---
<br>


## Scanner
  - 입력소스로부터 문자데이터를 읽어오는데 도움을 준다.
  ```java
  Scanner s = new Scanner(System.in);
  String input = s.nextLine();
  ```
  
## StringTokenizer
  - 긴 문자열을 지정된 구분자를 기준으로 토큰이라는 여러개의 작은 문자열로 잘라내는 데 사용된다.
  - 구분자로 단 하나의 문자밖에 사용하지 못하기때문에 보다 복잡한 형태의 구분자로 나누어야할때는 Scanner나 split메서드를 사용해야한다.
