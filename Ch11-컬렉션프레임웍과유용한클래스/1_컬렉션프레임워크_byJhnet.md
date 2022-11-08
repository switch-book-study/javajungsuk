### java.util 패키지에서 프로그래밍에서 자주쓰이는 클래스들
1. 컬렉션 프레임워크 : 많은 데이터를 쉽게 처리하는 클래스
2. 유용한 클래스 : 자주 쓰이는 클래스
3. 형식화 클래스 : 데이터 표준화 형식 출력 클래스

# 컬렉션 프레임워크
**프레임워크** : 클래스들을 표준화한 설계


## 컬렉션 프레임워크의 핵심 인터페이스 - List, Set, Map

크게 List, Set, Map이 있다.
- List : 순서유지o , 중복허용o
- Set : 순서유지x, 중복허용x
- Map : Key, Value로 이뤄진 데이터, 순서유지x, 키중복x, 값중복o

컬렉션프레임워크는 이름만으로 클래스의 특징을 알 수 있다.
`Vector`, `Stack`, `HashTable`, `Properties`는 이전부터 있었음
> 기존클래스는 안쓰는게 좋음

### Collection 인터페이스
add, clear, contains, equals 등 여러 메서드가 있음
대부분 return이 boolean임

### List 인터페이스
![](https://velog.velcdn.com/images/bjh0501/post/489d13e7-ef06-47fa-9c4e-177aa10844d1/image.png)
>그림 출처 : https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=baekmg1988&logNo=20194514561

중복허용o, 순서유지o

### Set 인터페이스
![](https://velog.velcdn.com/images/bjh0501/post/31739365-7c9b-451a-88aa-c875fcd84d5f/image.png)
> 그림출처 : https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=baekmg1988&logNo=20194515468

중복허용x, 순서유지x


### Map 인터페이스
![](https://velog.velcdn.com/images/bjh0501/post/db22afe9-7384-402a-a34e-c3c40c911a4a/image.png)
> 그림출처 : https://blog.naver.com/baekmg1988/20194516618

키, 값이 한쌍
키는중복x
값은중복o

#### 메서드
둘다 value 반환
values() : 반환타입 `Collection` value중복됨
keySet() : 반환타입 `Set` value중복안됨

### Map.Entry 인터페이스
- `Map`의 내부 인터페이스
- `Map`의 `Key`, `Value`를 다루기위해 정의해놓은 인터페이스

## 동기화
- 멀티쓰레드에서는 동기화가 필요
- `Vector`, `HashTable`은 자체적으로 동기화됨
- `ArrayList`, `HashMap`등등 클래스는 동기화 메서드로 해야함
- 동기화가 필요할때 `Collections`클래스에서 사용하면됨
ex) 
```java
List list = Collections.synchronizedList(new ArrayList<>());
```

## Vector와 ArrayList
기능이 매우 비슷함

### 공통점
- List인터페이스 구현
- 데이터의 저장공간을 배열로 사용
- 멤버변수가 `Object`

### 차이점
- Vector는 동기화o, ArrayList는 동기화x
- ArrayList에서 removeRange() 메서드 추가

### 장단점
- 데이터 읽기, 저장 효율좋음
- 용량 변경을 하면 `새 인스턴스에 복사`



## LinkedList

## Stack과 Queue

## Enumeration, Iterator, ListIterator

### Iterator

### Enumeration과 ListIterator
