
## 증감 연산자 ( ++, -- )
  - 증가 연산자(++): 피연산자의 값을 1 증가시킨다.
  - 감소 연산자(--): 피연산자의 값을 1 감소시킨다.
  - boolean형을 제외한 모든 기본형 변수에 사용 가능하며  전위형(++i)과 후위형(i++)이 있다.
  - 수식에서 전위형은 변수의 값을 먼저 증가시킨 후 변수의 값을 읽어오고 후위형은 변수의값을 먼저 읽어온 후 값을 증가시키기 때문에 결과가 다를 수 있다.
  - 함수의 매개변수로 사용된 경우에도 전위형은 값을 증가시킨 후 값을 넘겨주고 후위형은 값을 넘겨준 후 증가시켜주기때문에 결과가 다를 수 있다.
<br>


---
## 부호 연산자 ( + , - )
  - 피연산자의 부호를 변경하는데 사용된다.
  - boolean형과 char형을 제외한 나머지 기본형에 사용할 수 있다.
  - 부호연산자 +의 경우 양수 1을 곱한 결과를, -의 경우 음수 1을 곱한 결과를 얻는다.
<br>


---

## 비트전환 연산자 ( ~ )
  - 정수형과 char형에만 사용될 수 있다.
  - 피연산자를 2진수로 표현했을 때 0은 1로 1은 0으로 바꾼다. 그래서 연산자 ~에 의해 비트전환 되고나면 피연산자의 부호가 반대로 변경된다.
<br>


---
## 논리부정 연산자 ( ! )
  - boolean형에만 사용될 수 있다.
