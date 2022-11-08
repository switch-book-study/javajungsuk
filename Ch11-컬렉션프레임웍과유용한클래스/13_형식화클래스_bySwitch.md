## 형식화 클래스
  ### DecimalFormat
   - 숫자를 형식화 하는데 사용된다.
   - 숫자데이터를 정수, 부동소수점, 금액등 다양한 형식으로 표현할 수 있다.
   - 일정한 형식의 텍스트데이터를 숫자로 쉽게 변환하는것도 가능하다.
   ```java
   //사용법
   String number = "12345.67";
   DecimalFormat df = new DecimalFormat("#.#E0");
   
   //원하는 패턴에 맞게 변환된 문자열을 얻게됨
   String result = df.format(number);
   ```
  ### SimpleDateFormat
   - 날짜를 출력하는데 도움을 준다.
   ```java
   //사용법
   Date today = new Date();
   SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd");
   
   //오늘 날짜를 yyyy-MM-dd 형태로 변환하여 반환한다.
   String result = df.format(today);
   ```
  ### ChoiceFormat
   - 특정범위에 속하는 값을 문자열로 변환해준다.
   - 활용하기에 따라 if문과 switch문을 대신해서 다양한용도로 유용하게 쓰일 수 있다.
   ```
