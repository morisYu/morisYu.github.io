---
layout: single
title: "[Java] 입력과 출력 방법"
subtitle: 
categories: [java]
tag: [java, bufferedreader, bufferedwriter, scanner]
toc: true
toc_sticky: true
---

# [JAVA] 입력과 출력 방법  

## 입력 방법  

### InputStream  

- 자바에서 데이터는 스트림을 통해 입출력 됩니다. 스트림은 단일 방향으로 연속적으로 흘러가는 것을 말하며, 데이터는 출발지에서 나와 도착지로 흘러간다는 개념입니다.  

- 프로그램이 데이터를 입력받을 때에는 입력 스트림(InputStream)이라고 합니다. InputStream은 바이트 기반 입력 스트림의 최상위 클래스로 추상 클래스입니다.  

> 예시  

```java
import java.io.IOException;
import java.io.InputStream;

public class Test1 {

	public static void main(String[] args) throws IOException {
		InputStream in = System.in;

        // read() 메소드는 1 byte씩 데이터를 읽어옴
		int i = in.read();
		
        // 배열을 선언해서 데이터를 각각 대입 가능
        // 배열 크기가 3 이기 때문에 3 byte의 데이터를 넣을 수 있음
        byte[] a = new byte[3];
        in.read(a);
	}
}
```  

### InputStreamReader  

- InputStream의 read() 메소드로 읽은 값은 아스키코드 값으로 저장이 되기 때문에 해석하기 불편합니다. 입력한 문자값을 그대로 저장하기 위해서는 InputStreamReader 를 사용하면 됩니다.  

> 예시  

```java
import java.io.IOException;
import java.io.InputStreamReader;

public class Test1 {

	public static void main(String[] args) throws IOException {
		//InputStream in = System.in;
		//InputStreamReader inputReader = new InputStreamReader(in);
		
		// 위의 두 줄을 합쳐서 한 줄로 표현 가능함
		InputStreamReader inputReader = new InputStreamReader(System.in);
		
        char[] ch = new char[3];
        inputReader.read(ch);
	}
}
```  

### BufferedReader  

- InputStreamReader 로 데이터를 읽을 경우 설정한 배열 길이만큼의 데이터만 읽을 수 있는 단점이 있습니다. BufferedReader는 엔터를 경계로 인식하여 엔터 입력 전까지의 모든 문자열을 읽을 수 있습니다.  

- BufferedReader와 함께 Scanner도 데이터 입력 시 많이 사용이 되는데 두 클래스의 가장 큰 차이점은 많은 양의 데이터 입력 시 속도차이입니다. Scanner는 데이터를 입력하는 동시에 전송이 되고, BufferedReader는 데이터의 입력이 완료된 후 데이터를 한 번에 전송하기 때문에 많은 양의 데이터를 입력할 때에는 BufferedReader가 훨씬 빠릅니다.  

> 예시  

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Test1 {

	public static void main(String[] args) throws IOException {

		InputStreamReader inputReader = new InputStreamReader(System.in);
		BufferedReader br = new BufferedReader(inputReader);
		
        // readLine() 메소드는 한 줄씩 문자열을 읽음
		String str = br.readLine();
	}
}
```  

### Scanenr  

- BufferedReader 와 같이 데이터 입력 시 많이 사용되는 클래스입니다. BufferedReader 보다 입력을 쉽게 처리할 수 있지만 많은 양의 데이터 처리 시 속도가 느리다는 단점이 있습니다.  

- 메소드 사용 시 nextLine()의 경우 개행 기준으로 입력을 받게되는데 nextLine() 메소드 사용 전 다른 메소드를 사용하게 되면 이전 메소드에서 데이터 입력 후 엔터를 눌렀을 때 개행문자가 남아있게 되어 nextLine() 메소드는 건너뛰게 됩니다.  

- next()와 nextLine() 메소드 외 다른 메소드는 각 타입에 맞는 데이터를 입력하지 않으면 예외가 발생합니다.  

> 예시  

```java
import java.util.Scanner;

public class Test1 {

	public static void main(String[] args){
		Scanner scanner = new Scanner(System.in);
		
		// 문자열을 개행(엔터) 기준으로 입력받음
		String str1 = scanner.nextLine();
		System.out.println(str2);
		
		// 문자열을 공백/개행 기준으로 하나의 문장만 입력받음
		String str2 = scanner.next();
		System.out.println(str1);
		
		// 정수를 입력받음
        // 정수가 아닌 문자열이 입력되는 경우 예외 발생함
		int a = scanner.nextInt();
		System.out.println(a);
	}
}
```  

## 출력 방법  

### System.out.println  

- 가장 일반적으로 사용되는 출력문입니다.  

> 예시  

```java
// System.out.print 는 줄바꿈 없이 출력됨.
System.out.print("hello");
// System.out.println 은 줄바꿈이 됨.
System.out.println("world");
```  

### System.out.printf  

- 서식 문자를 사용해서 데이터를 원하는 형태로 출력이 가능합니다.  

`printf() 지시자`  

| 지시자 | 설명 |
| -- | -- |
| %b | boolean 형식으로 출력 |
| %d | 10진(decimal) 정수의 형식으로 출력 |
| %o | 8진(octal) 정수의 형식으로 출력 |
| %x, %X | 16진(hexa_decimal) 정수의 형식으로 출력 |
| %f | 부동 소수점의 형식으로 출력 |
| %e, %E | 지수 표현식의 형식으로 출력 |
| %c | 문자로 출력 |
| %s | 문자열로 출력 |
| %n | 줄바꿈 |  

> 예시  

```java
// System.out.printf("형식", 변수값)
System.out.printf("%d %.3f %c %s  %b", 100, 3.1415, 'A', "string", true);
System.out.printf("%n%s > [%-5d]", "전체 5자리 수, 왼쪽정렬", 10);
System.out.printf("%n%s > [%05d]", "전체 5자리 수, 앞에 빈자리는 0으로 채움", 10);
```  

### BufferedWriter  

- System.out.print()와 동일한 기능을 하는 클래스로 버퍼를 이용하기 때문에 속도가 빠릅니다. 자동 줄바꿈이 되지 않기 때문에 "\n" 을 넣어주거나 newLine()메소드를 사용해야 합니다.  

- 사용 시 flush() 메소드를 사용해서 버퍼를 비워주고 작업이 마무리되면 close() 메소드로 스트림을 닫아줘야 합니다.  

> 예시  

```java
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.OutputStreamWriter;

public class Test1 {

	public static void main(String[] args) throws IOException{
		
		String str1 = "hello world";
		String str2 = "goodbye world";
		
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
		bw.write(str1); // 출력할 내용을 버퍼에 추가
		bw.newLine();  // 줄 바꿈
		bw.write(str2);  // 출력할 내용을 버퍼에 추가
		bw.flush();  // 남은 데이터 모두 출력
		bw.close();  // 스트림 닫음(이 후에는 버퍼에 출력 내용 추가 불가)
	}
}
```  





<br><br><br>

# <strong>Reference</strong>  

- [콘솔 입출력](https://wikidocs.net/226){:target="_blank"}  
- [입력 스트림(Input Stream)과 출력 스트림(Output Stream)](https://coding-factory.tistory.com/281){:target="_blank"}  
- [스캐너(Scanner)클래스와 입력](https://st-lab.tistory.com/92){:target="_blank"}  
- [자바의 정석 기초(자바출력 printf/printf 지시자)](https://yunjungblog.tistory.com/26){:target="_blank"}  
- [BufferedReader/BufferedWriter 사용법](https://mebadong.tistory.com/12){:target="_blank"}   
