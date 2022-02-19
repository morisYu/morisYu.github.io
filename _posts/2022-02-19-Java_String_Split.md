---
layout: single
title: "[Java] 문자열(String) 분리하기"
subtitle: 
categories: [java]
tag: [java, String, method]
toc: true
toc_sticky: true
---

# [JAVA] 문자열(String) 분리하기  

## `split()  메소드`  

> 설명  

split() 메소드는 구분자를 기준으로 문자열을  분리해서 문자열의 배열로 저장합니다.  

```java
split(String Rex);
split(String Rex, int limit);

String str = "안녕하세요. 반갑습니다. 또만났네요. 날이좋네요.";
String[] strArray = str.split(" ");  // 구분자마다 분리함.
String[] strArray2 = str.split(" ",2);  // 구분자를 통해 분리하지만 limit 수 만큼 분리함.
```  

위 코드에서는 구분자를 공백(" ") 으로 지정했기 때문에 공백을 기준으로 문자열을 분리합니다.  

첫번째 코드는 문자열에서 구분자를 발견할 때마다 문자열을 분리해서 배열에 대입해주지만, 두번째 코드의 경우 배열의 크기를 제한했기 때문에 배열의 수 만큼 문자열을 분리해서 배열에 대입합니다.  

> **결과**  

![Java_String_Split(1)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_String_Split(1).png?raw=true)  

### 구분자 설정  

> 설명  

구분자는 어떤 문자가 와도 관계가 없으며, 여러 개의 문자를 동시에 적용할 수 있습니다.  

```java
String str = "hello@niceTomeetYou#good morning";
String[] strArray = str.split("@|#| ");
```  

위 코드에서는 구분자를 @, #, /s(공백) 세 개 설정하였습니다. 여러 개의 문자를 동시에 적용할 때에는 각 구분자를 `"|"` 를 사용해서 같이 넣어줄 수 있습니다.  

> **결과**  

![Java_String_Split(2)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_String_Split(2).png?raw=true)  

### 메타문자를 구분자로 사용하기  

> 설명  

메타문자란 정규표현식 또는 정규식을 제어할 수 있는 문자입니다.  

<span style="color: #F361DC">**메타문자의 종류**</span>  

| 종류 | 설명          |
| ---- | ------------- |
| ^    | 문자열의 처음 |
| $    | 문자열의 끝   |
| .    | 임의의 한 문자   |
| *    | 바로 앞의 문자가 없거나 하나 이상  |
| +    | 바로 앞의 문자가 하나 이상 |
| ?    | 앞의 문자가 없거나 하나 |
| [ ]  | 한 문자를 가리키고 묶음 안의 내용은 가리키는 문자의 범위 |
| { }  | 앞에 있는 문자의 개수를 나타내고 묶음 안에서 ',' 는 문자 개수의 범위 |
| ( )  | 괄호 안의 문자열은 하나로 묶어서 취급 |
| \|   | 또는(or) 의 뜻으로 선택문에 사용됨 |
| \    | 메타 문자의 성질을 없앨 때 사용 |  

메타문자를 구분자로 사용하기 위해서는 이스케이프 처리(`\\메타문자`)가 필요합니다. 

```java
\\?
\\.
```  

### 문자열에 공백이 있는 경우  

> 설명  

구분자를 공백으로 설정했을 경우, 공백은 문자열의 시작, 중간, 끝 부분에 전부 존재 가능합니다. 문자열의 중간이나 끝에 공백이 있는 경우에는 원하는 결과가 나오겠지만, 문자열의 시작에 공백이 있는 경우 원하는 결과와 다르게 나올 수 있으니 주의해야 합니다.  

```java
String str1 = "nice meet you";
String str2 = " nice meet you";
String str3 = "nice meet you ";
String[] strArray1 = str1.split(" ");
String[] strArray2 = str2.split(" ");
String[] strArray3 = str3.split(" ");
```  

> **결과**  

![Java_String_Split(3)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_String_Split(3).png?raw=true) 


## `trim() 메소드`  

> 설명  

위와 같이 문자열의 앞에 공백이 있는 경우에는 공백 앞에 비어있는 하나의 문자열을 추가하기 때문에 원하는 결과와 다르게 나오게 됩니다. 이 경우 문자열의 앞에 있는 공백을 제거 후 문자열을 분리해주어야 하는데, 이 때 trim() 메소드를 사용합니다. trim() 메소드는 문자열의 앞, 뒤 공백을 제거합니다.  

```java
String str1 = " nice meet you";
String str2 = " nice meet you";

String[] strArray1 = str1.split(" ");
String str3 = str2.trim();
String[] strArray3 = str3.split(" ");
```  

> **결과**  

![Java_String_Split(4)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_String_Split(4).png?raw=true)  

## `strip() 메소드`  

> 설명  

Java11 이후에는 java.lang.String 클래스에 strip() 메소드가 새로 추가되었습니다. stip() 메소드 역시 trim() 메소드와 같이 문자열의 앞, 뒤 공백을 제거해주며, stripLeading() 메소드는 문자열의 앞에 있는 공백을 제거하고, stripTrailing() 메소드는 문자열의 뒤에 있는 공백을 제거합니다.  

```java
String str = " nice meet you ";

String stripstr = str.strip();
String[] strArray1 = stripstr.split(" ");

String stripLeadingstr = str.stripLeading();
String[] strArray2 = stripLeadingstr.split(" ");

String stripTrailingstr = str.stripTrailing();
String[] strArray3 = stripTrailingstr.split(" ");
```

> **결과**  

![Java_String_Split(5)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_String_Split(5).png?raw=true)

## `subString() 메소드`  

> 설명  

위의 메소드들은 구분자를 기준으로 문자열을 분리하였다면, substring() 메소드는 문자열의 인덱스(위치)를 기준으로 문자열을 분리합니다.  

```java
substring(int index);
substring(int beginIndex, int endIndex);

String str = "hello nice to meet you"

String substring1 = str.substring(5);
String substring2 = str.substring(6, 16);

// 중간에 있는 "nice to" 부분을 잘라내고 싶으면 해당 문자열의 앞, 뒤를 substring() 메소드로 잘라주면 됩니다.
String substring3 = str.substring(0, 6)+str.substring(14);
```  

> 결과  

![Java_String_Split(6)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_String_Split(6).png?raw=true)

## `StringTokenizer 클래스`    

> 설명  

StringTokenizer 는 문자열을 추출하기 위한 클래스입니다. 생성자에 따라 다양한 방법으로 문자열을 추출할 수 있습니다.  

```java
// 외부 클래스이기 때문에 import 해야 함
import java.util.StringTokenizer;

StringTokenizer st1 = new StringTokenizer(문자열);
StringTokenizer st2 = new StringTokenizer(문자열, 구분자);
// 세 번째 생성자는 구분자를 토큰에 넣을지(true), 제외할지(false) 선택 가능(false가 기본 설정)
StringTokenizer st3 = new StringTokenizer(문자열, 구분자, true/false);


String str = "hello/ nice/ to/ meet/ you "
StringTokenizer st1 = new StringTokenizer(str);
// 구분자를 여러 개 설정할 경우 "," 로 구분
StringTokenizer st2 = new StringTokenizer(str, "/, ");
StringTokenizer st3 = new StringTokenizer(str, "/", true);

	System.out.println("첫번째 생성자");
	while (st1.hasMoreTokens()) {
		System.out.println(st1.nextToken());
	}
	System.out.println();
	System.out.println("두번째 생성자");
	while (st2.hasMoreTokens()) {
		System.out.println(st2.nextToken());
	}
	System.out.println();
	System.out.println("세번째 생성자");
	while (st3.hasMoreTokens()) {
		System.out.println(st3.nextToken());
	}
```  

> 결과  

StringTokenizer 클래스는 분리된 문자열을 토큰에 넣어주며, nextToken() 메소드는 첫 번째 토큰을 반환하기 때문에 모든 문자열을 보기 위해서는 반복문을 사용해서 토큰을 전부 반환해야 합니다.  

![Java_String_Split(7)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/Java/Java_String_Split(7).png?raw=true)

### StringTokenizer 메소드  

리턴값|메소드명|기능
--|--|--
boolean | hasMoreTokens() | 남아있는 토큰이 있으면 true, 없으면 false 리턴
String | nextToken() | 객체에서 다음 토큰을 반환
String | nextToken(String delim) | delim 기준으로 다음 토큰을 반환
boolean | hasMoreElements() | hasMoreTokens()와 동일
Object | nextElement() | nextToken()과 동일하지만 문자열이 아닌 객체를 리턴
int | countTokens() | 총 토큰의 갯수를 리턴





<br><br><br>

# <strong>Reference</strong>  

- [String클래스의 split 메서드로 문자열 분리하는법.](https://jhnyang.tistory.com/336){:target="_blank"}  
- [메타문자란? 메타문자 split방법](https://jsj0903.tistory.com/7){:target="_blank"}  
- [정규표현식의 메타 문자 종류](https://codedragon.tistory.com/7332){:target="_blank"}   
- [문자열 앞뒤 공백 제거하기(trim()vsstrip())](https://hianna.tistory.com/526){:target="_blank"}  
- [문자열 자르기(Substring, Split) 사용법&예제](https://coding-factory.tistory.com/126){:target="_blank"}  
- [StringTokenizer 클래스로 문자열 분리하기! split 비교.](https://jhnyang.tistory.com/398){:target="_blank"}  