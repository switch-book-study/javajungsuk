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

### 공통점
- List인터페이스 구현
- 데이터의 저장공간을 배열로 사용
- 멤버변수가 `Object`
- 기능이 매우 비슷함
- 내부는 `Object배열`로 되있음

### 차이점
- Vector는 동기화o, ArrayList는 동기화x
- ArrayList에서 removeRange() 메서드 추가

### 장단점
- 데이터 읽기, 저장 효율좋음
- 용량 변경을 하면 `새 인스턴스에 복사`

### 기타기능
- add(E e)
  - 무조건 true반환
  - 내부적으로 `void add(E e, Object[] elementData, int s)`호출
  - 크기가 커지면 동적으로 array크기가 커짐
    - 현재 크기의 2배
    
  
  
- remove(int index)
  1. 삭제할 인덱스 위쪽 데이터들을 아래인덱스로 복사
  2. 마지막 인덱스 null로 변경
  3. 사이즈 값 1개 감소
  4. 새로운 인스턴스 반환

### deep copy & shallow copy
shallow copy : 단순 참조복사
deep copy : 원본과 같은 데이터 객체를 생성


## LinkedList
노드로 연결되있음

### 배열의 단점
1. 크기 변경 불가
2. 큰크기의 배열을 생성, 메모리 낭비심함
3. 차례대로 추가 or 마지막 데이터 삭제는 빠름


### 간략한 코드
```java 
class Node {
	Node next; // 다음요소의 주소
    Object obj; // 데이터 저장
}
```
- next만 수정하면되서 추가나 삭제가 빠름
- 이전요소 접근이 어려운 단방향

### 더블링크드 리스트
- 링크드리스트를 보완
- 링크드리스트보다 더 많이쓰임

#### 간략한 코드
```java
class Node {
	Node next; // 다음요소 주소
    Node prev; // 이전요소 주소
    Object obj; // 데이터 저장
}
```

### 더블 써큘러 링크드리스트
더블 링크드 리스트를 보완
마지막 노드에서 다음 노드로 가면 첫번째 노드로 이동 (더블 링크드 리스트는 안됨)

> 자바의 `LinkedList`는 `더블링크드리스트`처럼 동작한다.
과거에는 `더블 써큘러 링크드리스트` 처럼 동작했다고한다.


### ArrayList, LinkedList차이
순차적으로 추가, 삭제 `ArrayList`가 더 빠름
중간데이터 추가, 삭제 `LinkedList`가 더 빠름

`LinkedList`는 개수가 많으면 차례대로 따라가야해서 접근시간이 오래걸린다.
`배열`은 `배열의주소 + index * 타입크기`로 접근이 가능해서 빠르다.

```java
ArrayList al = new ArrayList();
LinkedList ll = new LinkedList(al);
```
위 코드를 응용해서 
`저장`은 `LinkedList`
`접근`은 `ArrayList`
하면 빠름


## Stack과 Queue
스택 : LIFO
큐 : FIFO

## Enumeration, Iterator, ListIterator
모두 컬렉션 저장 요소 접근에 사용

### Iterator
`boolean hasNext()` : 다음요소 있는지 체크
`Object next()` : 다음요소 읽기 보통 `hasNext()` 다음에씀
`void remove()` : next()로 읽어욘 요소 삭제

```java
List l = new ArrayList();
Iterator it = l.iterator();
while(it.hasNext()) {
	System.out.println(it.next);
}
```
```java
// map의 키를 반복하는방법
Iterator it = map.keySet().iterator();

// map의 키, value를 반복
Set eSet = map.entrySet();
Iterator list = eSet.iterator();
list.next(); // key=value 형식으로 출력됨
```

### Enumeration과 ListIterator
- `Iterator`의 구버전이 `Enumeration`
  - 둘다 기능같음
- `Iterator`는 단방향
- `ListIterator`는 양방향
  - List인터페이스 구현해야함
- `remove`는 단독으로 안쓰이고 반드시 `next`를 먼저써야함

#### 용어
`cursor` : 앞으로 읽어올 요소 위치
`lastRet` : 마지막으로 읽은 요소 위치

## HashSet 
- Set의 구현체
- 순서를 유지하지않음
- 중복불가

> loadFactor : 컬렉션이 가득차기전(80%채워지면) 미리 사이즈를 2배로 늘림. 기본값 80%

구현체를 `LinkedHashSet`으로 하면 순서가 있음


## TreeSet
- 레드-블랙트리로 구현
- Set인터페이스로 구현
- 검색시간이 매우빠름
  - 루트부터 검색
- 삭제속도가 느림
  - 트리 재구성
  
## Comparator, Comparable
### Comparable 
- 클래스의 기본정렬 구현
- 오름차순정렬

### Comparator
- 다른기준 정렬
- 내림차순등등 가능

## Hashtable HashMap
- `HashTable` 이전버전
- `HashMap` 최신버전
- `Map`으로 구현

`key`, `value`가 있는 객체로 저장되는 `Array`

```java
public class Main {
	static HashMap phoneBook = new HashMap();

	public static void main(String[] args) {
		addPhoneNo("친구", "a", "1111");
		addPhoneNo("친구", "b", "2222");

		addPhoneNo("회사", "b", "33");
		addPhoneNo("회사", "c", "44");
		addPhoneNo("회사", "d", "55");
		
		printList();
	}

	static void addGroup(String groupName) {
		if (!phoneBook.containsKey(groupName)) {
			phoneBook.put(groupName, new HashMap());
		}
	}

	static void addPhoneNo(String groupName, String name, String tel) {
		// 새로운 HashMap put
		addGroup(groupName);
		// 그룹네임에 맞는 phoneBook객체 get
		// 해당 객체에 put을 해서 shallow카피로 값저장
		HashMap group = (HashMap) phoneBook.get(groupName);
		group.put(tel, name);
	}

	static void printList() {
		Set set = phoneBook.entrySet();
		Iterator it = set.iterator();

		while (it.hasNext()) {
			Map.Entry e = (Map.Entry) it.next();

			// value의 HashMap
			Set subSet = ((HashMap) e.getValue()).entrySet();
			Iterator subIt = subSet.iterator();

			System.out.println("그룹 : " + e.getKey());
			
			while (subIt.hasNext()) {
				Map.Entry subE = (Map.Entry) subIt.next();
				String tel = (String) subE.getKey();
				String name = (String) subE.getValue();
				System.out.println(name + ":" + tel);
			}
		}
	}
}
```

### 해싱이란
`해시함수`를 이용해 데이터를 `해시테이블`에 `저장` & `검색`

1. 검색 값의 키로 해시함수 호출
2. 해시코드로 저장되어있는 링크드리스트 찾음
3. 링크드리스트에서 검색한 키와 일치하는 데이터 찾음

## TreeMap
- 검색, 정렬에 적합한 클래스
- `HashMap`, `TreeMap`은 `검색성능`에 관한 클래스
- 대부분 `HashMap`이 더 뛰어남
- `범위검색`, `정렬`은 `TreeMap`을 사용

## Properties
- HashMap의 구버전
- String, String으로 저장된 클래스

``` java
Properties prop = new Properties();
prop.setProperty("time","30");
prop.setProperty("size","10");
prop.setProperty("lang","kr");
```

``` java
// name=value형식을 쉽게 파싱할 수 있다.
Properties prop = new Properties();
prop.load(new FileInputStream("file.txt"));
prop.getProperty("name");
```

# 유용한 클래스들
`java.util`에서 자주쓰이는 클래스들

## Calendar와 Date
- `Date`보다는 `Calendar`권장
- `Calendar`는 추상클래스
- 2월의 마지막날을 구할땐 3월1일에서 하루빼면됨


`new Calendar.getInstance()`로 지역, 국가설정, 현재날짜를 설정
```java
Calendar date = Calendar.getInstance();
date.set(2005,0,31); // 직접 설정
```

## Random
- 난수얻는 클래스
- Math.random()과 비슷함

## 정규식
원하는 조건의 문자열을 찾아줌

```java
// 패턴
Pattern p = Pattern.compile("c[a-z]*"); 
// 데이터
Matcher m = p.matcher(data[i]);
// 매치되는지 체크
if(m.matches()) {
	System.out.println(data[i]);
}
```

```java
String source = "HP:011-1111-1111, HOME:02-999-9999";
// ()로 그룹핑
String pattern = "(0\\d{1,2})-(\\d{3,4})-(\\d{4})";

Pattern p = Pattern.compile(pattern);
Matcher m = p.matcher(source);

// it.hasNext()랑 같음
while (m.find()) {
	System.out.println(m.group(1) + "," + m.group(2) + "," + m.group(3) + "," + m.group());
}
```
## Scanner
`화면`, `파일`, `문자열` 입력 -> 문자데이터 읽기

```java
Scanner s = new Scanner(System.in);
String input = s.nextLine();
```
```java
// 숫자들이 저장되있는 파일읽기
Scanner sc = new Scanner(new File("number-file.txt"));
while(sc.hasNextInt()) {
	sc.nextInt(); // 줄단위로 숫자 출력
}
```

## StringTokenizer
긴 문자열의 토큰을 구분
```java
String source = "100,200,300,400";
StringTokenizer st = new StringTokenizer(source, ","); // split 대신 사용
		
while(st.hasMoreTokens()) {
	System.out.println(st.nextToken());
}
```

# 형식화클래스
`변환`, `표준화`관련 클래스

## DecimalFormat
```java
double number = 123.45;
DecimalFormat df = new DecimalFormat("0.0");
System.out.printf("%s", df.format(number));
```

## SimpleDataFormat
날짜출력을 다양하게 하는 클래스

```java
Date today = new Date();
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
System.out.println(sdf.format(today));		
```

## ChoiceFormat
특정범위 값을 문자열로 변환
```java
double[] limits = { 60, 70, 80, 90 };
String[] grades = { "D", "C", "B", "A" };
int[] scores = { 100, 95, 88, 70, 52, 60, 70 };
ChoiceFormat form = new ChoiceFormat(limits, grades);
for (int i = 0; i < scores.length; i++) {
	System.out.println(scores[i] + ":" + form.format(scores[i]));
}
```
for, if문으로 학점구하는 로직이랑 비슷함

## MessageFormat
메세지형식 출력
```java
String msg = "Name : {0}, Tel : {1}";

Object[] arg = {
		"이자바","010-1323-1231"
};

String result = MessageFormat.format(msg, arg);
System.out.println(result);
// Name : 이자바, Tel : 010-1323-1231
```

# 제네릭스
- 타입안정성 제공
- 차입체크, 형변환 생략
- 타입을 지정하지않으면 `Object`

## ArrayList&#60;E>
```java
ArrayList<Tv> tvList = new ArrayList<Tv>();
```
Tv객체만 저장가능한 예제

```java
ArrayList tvList = new ArrayList();
tvList.add(new Tv());
Tv t = new (Tv) tvList.get(0);
```
제네릭 없이사용


```java
ArrayList<Tv> tvList = new ArrayList<Tv>();
tvList.add(new Tv());
Tv t = tvList.get(0);
```
제네릭 사용

```java
public static void printAll(ArraytList<? extends Product> list) {
	for(Unit u : list) {
    	System.out.println(u);
    }
}
```
제네릭 다형성사용`?`을 쓴다.
- ?대신 T를 써도된다.
<br>
## Iterator&#60;E>
```java
public interface Iterator<E> {
	boolean hasNext();
    E next();
    void remove();
}
```
Iterator 코드
<br>


```java
Iterator<Student> it = list.iterator();
while(it.hasNext()) {
	Student s = it.next();
    System.out.println(s.name);
}
```
위 예제에서 Iterator를 제네릭으로 안쓰면 
`Student s = (Student) it.next()` 이렇게 형변환해서 사용해야한다.

## Comparable&#60;T>과 Collection.sort()
클래스 정렬
```java
public class Main {
	public static void main(String[] args) {
		List<Student> list = new ArrayList<>();
		list.add(new Student("A", 1));
		list.add(new Student("Ab", 12));
		list.add(new Student("Ac", 3));
		list.add(new Student("Ad", 11));
		
		Collections.sort(list); // Comparable을 구현해야 사용가능
		
		Iterator<Student> it = list.iterator();
		while(it.hasNext()) {
			Student s = it.next();
			System.out.println(s);
		}
	}
}

class Student implements Comparable<Student> { // Cmparable 구현
	String name = "";
	int number = 0;

	public Student(String name, int number) {
		this.name = name;
		this.number = number;
	}

	@Override
	public int compareTo(Student o) {
		return o.number - this.number; // 내림차순
	}
	
	@Override
	public String toString() {
		return name + " " + number;
	}
}
```

`java
public static <T extends Comparable<? super T>> void sort(List<T> list)
`
`Collection.sort()`의 선언부
- `List<T> list` : List&#60T>인터페이스를 구현해야 사용가능
- `<T extends Comparable<? super T>>`
  1. Comparable인터페이스를 구현한 타입이여야 함
  1. `? Super T`는 조상타입만 가능
  
## HashMap&#60K, V>
아래형식으로 선언
```java
HashMap<String, Stduent> map = new HashMap<String, Student>();
```
