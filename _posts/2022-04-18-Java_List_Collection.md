---
published: true
layout: single
title: "[Java] 리스트(List) 컬렉션"
subtitle: 
categories: [java]
tag: [java, arraylist, linkedlist, vector, collection]
toc: true
toc_sticky: true
---  

# [Java] 리스트(List) 컬렉션  


## 리스트(List)  

> 설명  

- 리스트란 저장된 요소들의 순서가 있고 데이터에 중복이 가능하며, 인덱스(index) 번호에 의해서 정렬됩니다.  

> 리스트의 특징  

1. 리스트는 컬렉션 인터페이스 중 하나입니다.  
2. 리스트는 크기 조절이 가능합니다.  
3. 리스트는 초기 크기를 지정하지 않아도 됩니다.  
4. 리스트에서 삭제는 공간을 지우는 것입니다.  
5. 대표적인 구현클래스로 ArrayList, LinkedList, Vector 가 있습니다.  

> 리스트 클래스의 주요 메소드  

| 메소드 | 설명 |
| -- | -- |
| boolean add(E e) | 주어진 객체를 맨 끝에 추가합니다. |
| void add(int index, E element) | 주어진 인덱스에 객체를 추가합니다. |
| set(int index, E element) | 해당 인덱스에 저장된 객체를 주어진 객체로 바꿉니다. |
| boolean contains(Object o) | 주어진 객체가 있는지에 대한 여부를 검색합니다. |
| E get(int index) | 주어진 인덱스에 저장된 객체를 리턴합니다. |
| isEmpty() | 컬렉션이 비어있는지 여부를 확인합니다. |
| int size() | 저장되어 있는 전체 객체 수를 리턴합니다. |
| E remove(int index) | 주어진 인덱스에 저장된 객체를 삭제합니다. |
| void clear() | 리스트에 저장된 요소를 전부 삭제합니다. |
| boolean remove(Object o) | 주어진 객체를 삭제합니다. |

<br>  

### ArrayList  

> 설명  

- ArrayList는 List 인터페이스를 상속받은 클래스로 크기가 가변적으로 변하는 선형리스트입니다. 한 번 생성되면 크기가 변하지 않는 배열과는 달리 ArrayList는 객체들이 추가되어 저장 용량(capacity)을 초과하면 자동으로 부족한 크기만큼 용량이 늘어납니다.  

- ArrayList 중간에 값을 추가하면 해당 인덱스부터 마지막 인덱스까지 모두 1 씩 뒤로 밀려납니다.  

> 사용방법  

- #### ArrayList 선언   

```java
// 타입 미설정 Object로 선언
ArrayList list1 = new ArrayList();

// 타입설정 Member 객체만 사용가능
ArrayList<Member> list2 = new ArrayList<Member>();

// 타입설정 Integer 타입만 사용가능
ArrayList<Integer> list3 = new ArrayList<Integer>();

// new에서 타입 파라미터 생략가능
ArrayList<String> list4 = new ArrayList<>();

// 초기 용량(capacity)지정
ArrayList<Integer> list5 = new ArrayList<Integer>(10);

// 생성시 값추가
ArrayList<Integer> list6 = new ArrayList<Integer>(Arrays.asList(1,2,3));
```  

<br>  

- #### ArrayList 값 추가   

```java
// 선언 시 타입을 미설정하면 다양한 타입의 값(또는 객체) 추가 가능
list1.add(3);
list1.add('c');
list1.add("kim");
list1.add(new Member("kaka", 10));

// 타입을 설정했기 때문에 list2 에는 Member 객체만 추가 가능
list2.add(new Member("kim", 13));

// null 값도 추가 가능
list3.add(null);
list3.add(11);

// index 1 위치에 값(10) 추가
list3.add(1,10);

// list5 에 list3의 요소(element) 추가
list5.addAll(list3);
```  

<br>  

- #### ArrayList 값 삭제  

```java
// index 1 위치에 있는 값 삭제
list5.remove(1);

// 모든 값 삭제
list6.clear();
```  

<br>  

- #### ArrayList 크기 확인  

```java
System.out.println(list5.size());
```  

<br>  

- #### ArrayList 값 검색  

```java
// list1에 "kim"이 있는지 검색(true 또는 false 출력)
System.out.println(list1.contains("kim"));

// 'c'가 있는 index 를 출력, 없으면 -1 을 출력
System.out.println(list1.indexOf('c'));
```  

<br>  

- #### ArrayList 값 출력  

```java
// 배열 형식으로 출력
System.out.println(list6);

// 0 번째 index 값 출력
System.out.println(list6.get(0));

// for문을 통한 전체출력
for(Integer i : list6) { 
    System.out.println(i);
}

// Iterator 선언
Iterator<Integer> iter = list6.iterator();
// 다음값이 있는지 체크
while(iter.hasNext()){
	//값 출력
    System.out.println(iter.next()); 
}
```  

<br>  

### LinkedList  

> 설명

- LinkedList는 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식의 자료구조입니다. 노드는 LinkedList에 객체를 추가하거나 삭제하면 앞뒤 링크만 변경되고 나머지 링크는 변경되지 않습니다.  

- 중간에 데이터가 삽입/삭제가 되더라도 ArrayList처럼 데이터가 삽입/삭제 후의 전체 인덱스가 1 씩 뒤로 밀리거나 당겨지는 것이 아니라 앞뒤 링크만 변경되기 때문에 데이터의 삽입/삭제가 빈번한 경우에는 LinkedList를 사용하는 것이 좋습니다.  

- 인덱스가 없기 때문에 특정 요소에 접근하기 위해서는 순차 탐색이 필요하며 탐색속도가 ArrayList에 비해 느립니다.  

> 사용방법  

- #### LinkedList 선언  

```java
// 타입 미설정 Object로 선언
LinkedList list1 = new LinkedList();

// 타입설정 Member 객체만 사용가능
LinkedList<Member> list2 = new LinkedList<Member>();

// 타입설정 Integer 타입만 사용가능
LinkedList<Integer> list3 = new LinkedList<Integer>();

// new에서 타입 파라미터 생략가능
LinkedList<Integer> list4 = new LinkedList<>();

// 생성시 값 추가
LinkedList<Integer> list5 = new LinkedList<Integer>(Arrays.asList(3, 2, 1));
```  

<br>  

- #### LinkedList 값 추가  

```java
// 가장 뒤에 값 추가
list5.add(5);

// 가장 앞에 값 추가
list5.addFirst(22);

// 가장 뒤에 값 추가
list5.addLast(33);

// index 1 위치에 null 추가
list5.add(1, null);
```  

<br>  

- #### LinkedList 값 삭제  

```java
// 가장 앞의 값 삭제
list5.removeFirst();

// 가장 뒤의 값 삭제
list5.removeLast();

// index 생략시 첫번째 값 삭제
list5.remove();

// index 1 위치의 값 삭제
list5.remove(1);

// 모든 값 삭제
list5.clear();
```  

<br>  

- #### LinkedList 크기 확인  

```java
System.out.println(list5.size());
```  

<br>  

- #### LinkedList 값 검색  

```java
// list5에 null이 있는지 검색(true 또는 false 출력)
System.out.println(list5.contains(null));

// 'c'가 있는 index 를 출력, 없으면 -1 을 출력
System.out.println(list5.indexOf('c'));
```  

<br>  

- #### LinkedList 값 출력  

```java
// 배열 형식으로 출력
System.out.println(list5);

// 0 번째 index 값 출력
System.out.println(list5.get(0));

// for문을 통한 전체출력
for(Integer i : list5) { 
    System.out.println(i);
}

// Iterator 선언
Iterator<Integer> iter = list5.iterator();
// 다음값이 있는지 체크
while(iter.hasNext()){
	//값 출력
    System.out.println(iter.next()); 
}
``` 

<br>  

### Vector  

> 설명  

- Vector 는 ArrayList와 동일한 내부구조를 가지고 있습니다. 한 가지 다른 점은 Vector는 동기화된 메소드로 구성되어 있기 때문에 멀티 스레드가 동시에 이 메소드들을 실행할 수 없고, 하나의 스레드가 실행을 완료해야만 다른 스레드들이 실행할 수 있습니다. 따라서 멀티 스레드 환경에서 안전하게 객체를 추가하고 삭제할 수 있습니다.  

> 사용방법  

- #### Vector 선언  

```java
// 타입 미설정 Object로 선언된다.
Vector vector1 = new Vector();

// 타입설정 Member 객체만 사용가능
Vector<Member> vector2 = new Vector<Member>();

// 타입설정 Integer 타입만 사용가능
Vector<Integer> vector3 = new Vector<Integer>();

// new에서 타입 파라미터 생략가능
Vector<Integer> vector4 = new Vector<>();

// 초기 용량(capacity)지정
Vector<String> vector5 = new Vector<String>(10);

// 초기값 지정
Vector<Integer> vector6 = new Vector<Integer>(Arrays.asList(1, 2, 3));
```  

<br>  

- #### Vector 값 추가  

```java
// 값 추가
vector5.add("KIM");

// null값도 add가능
vector1.add(null);

// index 1 위치에 값(10) 추가
vector1.add(1, 10);

// index 2 위치의 값을 변경
vector6.set(2, 99);

// Member 객체 추가
Member member = new Member("park", 20);
vector2.add(member);
vector2.add(new Member("Yun", 31));
```  

<br>  

- #### Vector 값 삭제  

```java
// index 1 제거
vector6.remove(1);

// 모든 값 제거
vector6.removeAllElements();

// 모든 값 제거
vector6.clear();
```  

<br>  

- #### Vector 크기 확인  

```java
// Vector 의 자료 개수
System.out.println(vector5.size());

// Vector 물리적 크기
System.out.println(vector5.capacity()); 
```  
<br>  

- #### Vector 값 검색  

```java
// vector5에 "kim"이 있는지 검색(true 또는 false 출력), 대소문자 구분함
System.out.println(vector5.contains("kim"));

// "LEE"가 있는 index 를 출력, 없으면 -1 을 출력
System.out.println(vector5.indexOf("LEE"));
```  

<br>  

- #### Vector 값 출력  

```java
// 배열 형식으로 출력
System.out.println(vector5);

// 0 번째 index 값 출력
System.out.println(vector5.get(0));

// for문을 통한 전체출력
for(Integer i : vector5) { 
    System.out.println(i);
}

// Iterator 선언
Iterator<Integer> iter = vector5.iterator();
// 다음값이 있는지 체크
while(iter.hasNext()){
	//값 출력
    System.out.println(iter.next()); 
}
```  





<br><br><br>  

# <strong>Reference</strong>  

- [컬렉션이란?(Collection)](https://hoon26.tistory.com/25){:target="_blank"}  
- [자바 컬렉션 프레임워크(List, Set, Map) 총정리](https://coding-factory.tistory.com/550){:target="_blank"}  
- [List(컬렉션)](https://velog.io/@sunnamgung8/%EC%9E%90%EB%B0%94List%EC%BB%AC%EB%A0%89%EC%85%98){:target="_blank"}  
- [자바 ArrayList 사용법 & 예제 총정리](https://coding-factory.tistory.com/551){:target="_blank"}  
- [자바 LinkedList 사용법 & 예제 총정리](https://coding-factory.tistory.com/552){:target="_blank"}  
- [자바 Vector 사용법 & 예제 총정리](https://coding-factory.tistory.com/553){:target="_blank"}  