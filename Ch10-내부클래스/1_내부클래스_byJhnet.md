# 내부클래스
- 클래스내에 선언된 클래스
- 내부클래스에서 외부 클래스의 멤버를 쉽게접근
- 코드의 복잡성 줄임
- 실제로는 거의 사용안함
  - GUI에 사용(AWT, Swing)
  
# 내부 클래스의 종류와 특징
인스턴스 클래스 : 외부 클래스에 선언, 외부 클래스의 인스턴스 멤버처럼 쓰임
스태틱 클래스 : 외부 클래스에 선언, 외부 클래스의 static멤버처럼 쓰임
지역 클래스 : 외부 클래스, 초기화블럭에 선언 / 선언된 영역에서만 쓰임
익명클래스 : 클래스 선언 + 객체생성 동시에함 이름없는 클래스(일회용)

# 내부 클래스의 선언
```java
class Outer {
	class InstanceInner { }
    static class StaticInner { }
    void method1() {
    	class LocalIneer { }
    }
```
선언된 위치에 따라 유효범위, 접근성을 갖는다.

# 내부 클래스의 제어자와 접근성
- 내부 클래스도 클래스기에 접근제어자, abstract 등등 붙힐 수 있다.
- 인스턴스 클래스는 외부클래스를 먼저 생성해야 생성가능하다.
  ```java
  class Outer {
  	class InstanceInner {}
    
  	void a () {
    
  		Outer outer = new Outer();
  		InstanceInner obj = outer.new InstanceInner();
        }
    }
  
  ```
- 외부 클래스의 지역변수는 final이 붙은 상수만 접근가능
  > jdk  11기준에서는 이말이 틀린듯하다.
  
  - 지역변수는 콜스택이라 메서드가 실행되면 소멸되는데 상수는 constant pool이라 소멸이안된다.
  - inner instance가 계속 참조를 하려면 소멸이 안되는 상수를 해야한다.
  
  ```java
  	void myMethod() {
		int iv33 = 111;
		final int IV33 = 222;
		
		class LocalInner {
			int iv3 = iv33;
            
                  // 에러가 나야하는데 안남
			int IV3 = IV33; 
		}
		
		System.out.println(iv33);
		System.out.println(IV33);
	}
  ```
  jdk11기준으로 에러가 안난다.
  
  
### 컴파일시 생성되는파일
- Outer.class
- Outer$InnerA.class
- Outer$InnerB.class
- Outer$1Inner.class : 메서드안에 클래스면 앞에숫자가 붙는다.

### 내부클래스 선언법
```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
```
### 외부클래스 변수가져오기
``` java
Outer.this.value // Inner클래스에서 외부클래스의 변수 출력
```


# 익명클래스
