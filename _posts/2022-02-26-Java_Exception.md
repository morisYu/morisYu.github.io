---
layout: single
title: "[Java] 예외(Exception) 종류와 처리방법"
subtitle: 
categories: [java]
tag: [java, exception]
toc: true
toc_sticky: true
---

# [JAVA] 예외(Exception) 종류와 처리방법

## 오류(error) 와 예외(exception)  

<span style="color: pink"> **오류(Error)** </span>  

- 오류(Error)는 시스템(하드웨어)에 비정상적인 상황이 생겼을 때 발생합니다. 이는 시스템 레벨에서 발생하기 때문에 심각한 수준의 오류이며, 개발자가 미리 예측하여 처리할 수 없습니다. 오류가 발생하면 프로그램은 종료되며 복구를 할 수 없습니다.  

<span style="color: pink"> **예외(Exception)** </span>  

- 예외(Exception)는 개발자가 구현한 로직에서 발생합니다. 예외는 오류와 마찬가지로 발생하면 프로그램이 종료되지만 복구를 할 수 있으며, 개발자는 예외가 발생할 상황을 미리 예측하여 처리할 수 있기 때문에 예외를 구분하고 그에 따른 처리 방법을 명확히 알고 적용하는 것이 중요합니다.  

## 예외클래스 구조  

> 모든 예외클래스는 Throwable 클래스를 상속받고 있으며, Error 는 시스템에 변화를 주어 문제를 처리해야 하는 경우가 일반적이고, Exception은 개발자가 로직을 추가하여 처리할 수 있습니다.

![Java_Exception](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_Exception(1).png?raw=true)  

### Checked Exception VS Unchecked Exception  

<span style="color: pink"> **Checked Exception** </span>  

- Checked Exception은 주로 외부의 영향으로 발생하는 것으로, 사용자들이 존재하지 않는 파일의 이름을 입력했거나, 입력한 데이터 형식이 잘못된 경우에 발생합니다. 이는 반드시 처리를 해주어야 하고 그렇지 않으면 컴파일 시 에러가 발생합니다.  

<span style="color: pink"> **Unchecked Exception** </span>  

- Unchecked Exception은 주로 개발자의 실수에 의해 발생할 수 있는 예외이며, 프로그래밍 요소들과 관계가 깊습니다. 배열의 범위를 벗어나거나 값이 `null`인 멤버 변수를 호출할 때 발생하는 예외가 대표적입니다. 이는 예외 처리를 하지 않아도 컴파일 시 문제가 되지는 않지만, 프로그램 실행 시 에러가 발생합니다.  

|  | Checked Exception | Unchecked Exception |
| -- | -- | -- |
| 처리여부 | 반드시 예외처리를 해야함 | 명시적인 처리를 강제하지 않음 |
| 확인시점 | 컴파일 단계 | 실행 단계 |
| 예외발생 시 트랜잭션 처리 | roll-back 하지 않음 | roll-back 함 |  

## 대표적인 Unchecked Exception 종류  

### `NullPointerException`  

- null 이란?  
    - 아무것도 없음을 의미합니다.(0 또는 공백)  
    - 모든 참조유형에 대한 기본 값은 `null` 입니다.  
    - null은 유효한 객체 인스턴스가 아니므로 할당되는 메모리가 없습니다.  

- 예외가 발생하는 경우  
    - null 객체에서 method를 호출하는 경우  
    - null 객체의 필드에 접근하거나 값을 변경하는 경우  
    - null 의 길이를 배열처럼 취하는 경우  
    - null 을 throw 하는 경우  
    - null 을 통해 동기화 할 경우  

- 객체 생성 후 초기화를 잘 해주면 대부분 해결이 됩니다.  

```java
String str=null;
System.out.println(str.toString());

// 배열을 초기화 하지 않음(크기가 정해지지 않음)
int[] number = null;
System.out.println(number.length);

// Test 객체의 배열을 생성하면 각 배열의 index 마다 초기화를 해야함.
Test[] test = new Test[5];
System.out.println(test[0].name);  // 예외 발생

test[0] = new Test();  // index마다 객체 초기화
System.out.println(test[0].name);  // 정상 동작됨
```

### `ArrayIndexOutOfBoundsException`  

- 배열의 크기를 n이라고 했을 때 배열의 인덱스는 1 부터 n 이 아니라 0 부터 (n-1)이 됩니다. 이 경우 해당 범위를 벗어나는 인덱스에 대한 요청이 있을 때 예외가 발생합니다.  

```java
// i 배열의 인덱스는 0 부터 3 까지인데 인덱스가 4 인 배열의 값을 요청해서 예외 발생  
int[] array = {0, 1, 2, 3};
System.out.println(array[4]);

// 반복문에서도 i 가 0 부터 배열의 크기까지(배열 크기값 포함) 반복문을 실행할 경우에도 예외 발생  
for (int i = 0; i <= array.length; i++) {
	System.out.print(array[i]);
}
```  

### `NegativeArraySizeException`

- 배열을 생성할 때 배열의 크기를 음수로 지정할 때 예외가 발생합니다. 배열의 크기를 양수로 바꾸어주면 해결이 됩니다.  

```java
int[] array = new int[-1];
```

### `ClassCastException`  

- 객체의 형을 변환할 때 객체 타입 변환이 부적절할 때 발생합니다. 클래스의 상속 관계를 잘 확인해야 합니다.  

```java
// Dog 과 Cat 클래스는 Animal 클래스와 상속 관계에 있음.
class Animal {
	String name = "ANIMAL";
}
class Dog extends Animal {
	String name = "DOG";
}
class Cat extends Animal {
	String name = "CAT";
}

// 부모 객체에서 자식 객체로 강제 형 변환(Casting) 시 예외 발생
// 자식 객체가 부모 객체로 자동 형 변환이 되어있는 경우에만 강제 형 변환(Casting) 가능
Animal animal = new Animal();
Dog animalDog = (Dog) animal;  // (X)

Animal dog = new Dog();  // 자동 형 변환(Promotion) 
Dog castingDog = (Dog) dog;  // 자동 형 변환이 된 상태에서 강제 변환 가능
System.out.println(dog.name);

// Dog 클래스와 Cat 클래스는 서로 상속관계가 아니기 때문에 형 변시 예외 발생
Animal cat = new Cat();
Dog castingCat = (Dog) cat;
```  

### `ArithmeticException`  

- 예외적인 산술 조건(숫자를 0 으로 나누어주는 경우)이 있는 경우 예외가 발생합니다. 계산식을 작성할 때 0 으로 나누어지는 상황이 없는지 확인해야 합니다.  

## 예외처리 방법  

### `try-catch-finally`  

- try 문 안에서 예외가 발생할 경우 catch 문의 내용을 실행합니다. 예외가 발생하게되면 이후의 코드는 실행이 되지 않기 때문에 반드시 실행해야 하는 코드가 있다면 finally 문 안에 배치를 하면 해당 코드는 예외가 발생하더라도 무조건 실행이 됩니다.  

```java
int a = 10;
int b = 0;
try {
	int result = a / b; // 예외가 발생할 가능성이 있는 코드를 try 문 안에 배치
} catch (ArithmeticException e) {  // ArithmeticException 예외가 발생하면 catch 문 코드를 실행
	System.out.println("산술 오류입니다.");
} finally {  // 예외 발생여부와 관계없이 finally 문 코드는 실행됨
	System.out.println("예외가 발생해도 무조건 실행됩니다.");
}
```  

> catch 문은 여러 종류를 적용 가능합니다. 다만 상위 예외 코드가 위에 있는 경우 아래에 있는 예외에 검출되지 않습니다.  

```java
int a = 10;
int b = 1;
int result = 0;
int size = -1;

// catch 문을 추가하여 여러 종류의 예외 검출 가능
try {
	result = a / b;  // 변수 b 가 0 인 경우 ArithmeticException 발생
	int[] array = new int[size];  // 변수 size 가 음수인 경우 NegativeArraySizeException 발생
} catch (ArithmeticException e) {
	System.out.println("산술 오류입니다.");
} catch (NegativeArraySizeException e) {
	System.out.println("배열 크기가 음수입니다.");
} finally {
	System.out.println("예외가 발생해도 무조건 실행됩니다.");
}

// 여러 종류의 예외를 한 번에 검출 가능(어떤 예외인지는 정확히 알기 어려움)
try {
	result = a / b;
	int[] array = new int[size];
} catch (ArithmeticException | NegativeArraySizeException e) {
	System.out.println("산술 오류이거나 배열의 크기가 음수입니다.");
} finally {
	System.out.println("예외가 발생해도 무조건 실행됩니다.");
}

// 여러 종류의 예외를 검출 시 상위 예외가 위에 있으면 하위 예외는 검출할 수 없습니다.
try {
	result = a / b;  
	int[] array = new int[size];  
} catch (Exception e) {  // 상위 예외에서 프로그램이 종료되기 떄문에 어떤 예외인지 알 수 없음
	System.out.println("상위 예외입니다.");
} catch (ArithmeticException e) {
	System.out.println("산술 오류입니다.");
} catch (NegativeArraySizeException e) {
	System.out.println("배열 크기가 음수입니다.");
} finally {
	System.out.println("예외가 발생해도 무조건 실행됩니다.");
}
```  

> 반복문에서 Scanner 객체를 예외처리할 때 주의할 점  

- 반복문에서 Scanner 객체 사용 시 예외가 발생하면 입력한 값이 계속 남아있어서 무한루프에 빠지는 경우가 발생하기 때문에 예외 처리 부분(catch)에서 객체를 새로 생성해서 초기화를 해야 합니다.  

```java
// 반복문에서 scanner 객체 사용 시 예외가 발생하면 무한루프에 빠짐
while (true) {
	int a;
	int b;
	int result=0;
	try {
		a = scanner.nextInt();
		b = scanner.nextInt();
		result = a / b;
	} catch (InputMismatchException e) {
		System.out.println("숫자가 아닌 문자가 입력되었습니다.");
	} catch (Exception e) {
		System.out.println("예외 발생");
	}
}

// 무한루프에 빠지지 않기 위해서는 예외 발생 시 scanner 객체를 초기화 해주면 됩니다.
while (true) {
	int a;
	int b;
	int result=0;
	try {
		a = scanner.nextInt();
		b = scanner.nextInt();
		result = a / b;
	} catch (InputMismatchException e) {
		System.out.println("숫자가 아닌 문자가 입력되었습니다.");
        scanner = new Scanner(System.in);
	} catch (Exception e) {
		System.out.println("예외 발생");
	}
}
```  

### `throws`  

- 메소드 내부에서 예외가 발생할 수 있는 코드를 작성할 때 `try-catch` 블록으로 예외를 처리하는 것이 기본이지만, 경우에 따라서는 메소드를 호출한 곳으로 예외를 위임시킬 수 있습니다. 이때 사용하는 키워드가 `throws` 입니다. 메소드에 예외를 선언함으로써 메소드를 사용하는 사람이 메소드의 선언부를 보았을 때 어떠한 예외들이 처리되어야 하는지 쉽게 알 수 있습니다.   

```java

int a = 0;
int b = 4;
int result

// 예외 발생 상황
result = b / a;  // ArithmeticException 발생

// try-catch 로 예외 처리
try {
	result = b / a;
} catch (ArithmeticException e) {
	System.out.println("예외 발생 시 실행내용");  // 예외 발생 시 직접 처리
}

// throws 로 예외 처리(메소드에 예외 선언)
// main 메소드에도 예외 선언을 해서 사용 가능
static void divide(int a, int b) throws MyException1, ArithmeticException  {  // 쉼표로 여러 개의 예외를 선언할 수 있음
	if (a == 0) {
        MyException e = new MyException("0으로 나누는 것은 허용되지 않습니다.");
        throw e;
        // 윗부분을 줄여서 한 줄로 표현 가능
		throw new MyException("0으로 나누는 것은 허용되지 않습니다.");  // MyException 으로 예외 처리를 떠넘김
	}
}

// Exception 클래스를 상속받아서 사용자 정의 예외를 만들 수 있음
class MyException extends Exception {
	MyException(String msg) {  // 문자열을 매개변수로 받는 생성자
		super(msg);  // 조상인 Exception 클래스의 생성자를 호출한다.
	}
}
```  

## Java Exception 에러 출력  

### `e.getMessage()`  

- 예외 메세지를 가지고 옵니다. 기본적으로 예외의 원인을 설명하는 메세지가 있으며, 사용자가 예외를 정의한 경우 예외 생성 시 설정한 메세지를 가지고 옵니다.    

```java
try {
	throw new MyException("테스트");  // MyException 예외를 생성해서 던짐
} catch (MyException e) {
	System.out.println(e.getMessage());  // 위에서 생성한 MyException 예외 메세지를 가지고와서 출력
}

// Exception 클래스를 상속받아서 만든 사용자 정의 예외
class MyException extends Exception {
	MyException(String msg) {
		super(msg);
	}
}
```  

### `e.printStackTrace()`  

- 예외가 발생한 이유와 발생 위치의 전체적인 단계를 출력합니다.  

```java
try {
	throw new MyException("테스트");
} catch (MyException e) {
	e.printStackTrace();
}
```





<br><br><br>

# <strong>Reference</strong>  

- [예외처리(Exception handling)](https://catsbi.oopy.io/92cfa202-b357-4d47-8de2-b9b3968dfb2e){:target="_blank"}  
- [Java 예외(Exception) 처리에 대한 작은 생각](https://www.nextree.co.kr/p3239/){:target="_blank"}  
- [예외의 종류](https://sorjfkrh5078.tistory.com/104){:target="_blank"}  
- [java.lang.NullPointerException 해결법](https://yeolco.tistory.com/73){:target="_blank"}  
- [java.lang.ArrayIndexOutOfBoundsException 해결법](https://yeolco.tistory.com/72){:target="_blank"}  
- [예외처리(다중catch, 예외강제발생, 예외떠넘기기..)](https://earthconquest.tistory.com/80){:target="_blank"}  