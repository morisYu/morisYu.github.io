---
published: true
layout: single
title: "[Tools] 여러 버전의 JDK 설치"
subtitle: 
categories: [tools]
tag: [tools, jdk]
toc: true
toc_sticky: true
---  

# [Tools] 여러 버전의 JDK 설치  

### 설치파일 다운로드 및 설치  

> ORACLE 홈페이지에서 Java Downloads 페이지로 이동합니다.  

- [https://www.oracle.com/java/technologies/downloads/#jdk18-windows](https://www.oracle.com/java/technologies/downloads/#jdk18-windows){:target="_blank"}    

<br>  

> "Java archive" 를 클릭 후 원하는 버전의 JDK 설치파일을 다운로드 받습니다.  

- 자바 프로그래밍 언어의 플랫폼은 여러 종류가 있는데 가장 대중적으로 사용되는 SE 플랫폼을 설치할 것입니다.  

    - Java SE (Standard Edition)  
    - Java EE (Enterprise Edition)  
    - Java ME (Micro Edition)  
    - Java FX

- Java 버전 중 일부 버전들은 LTS (Long Term Support) 로 해당 버전은 장기적으로 지원을 해주기 때문에 LTS 버전을 다운로드 받는 것이 좋습니다.  

    - [Oracle Java SE Support Roadmap](https://www.oracle.com/java/technologies/java-se-support-roadmap.html){:target="_blank"}  

- 이전 버전의 JDK 를 다운로드 할 때는 Oracle 사이트에 로그인을 해야 합니다.  

![JDK_Install(1)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(1).png)  

<br>  

![JDK_Install(2)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(2).png)  

<br>  

> 다운로드 받은 설치파일을 실행하여 JDK 를 설치합니다.  

- JDK 설치 시 버전마다 뜨는 창이 약간 차이가 있지만 설치 경로만 잘 확인 후 Next 로 진행합니다.  

- 다른 버전의 JDK 를 여러 개 설치 시 같은 경로 안에 JDK 를 설치합니다.  

![JDK_Install(3)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(3).png)  

<br>  

![JDK_Install(4)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(4).png)  

<br>  

![JDK_Install(5)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(5).png)  

<br>  

### Java 환경변수 설정  

> 컴퓨터의 어느 경로에서든지 운영체제가 Java 를 인식하도록 하기 위해 환경변수를 설정합니다.  

- 내 PC 우클릭 → 속성 → 고급 시스템 설정 → 고급 → 환경 변수 로 이동해서 시스템 변수를 "새로만들기"로 추가합니다.  

    - 변수 이름: JAVA_HOME  
    - 변수 값: JDK 설치 경로  
    - 여러 버전의 JDK 를 설치 시 가장 많이 사용하는 버전의 JDK 만 변수에 추가합니다.  

![JDK_Install(6)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(6).png)  

<br>  

- 시스템 변수의 Path 를 더블클릭하여 Java 의 실행파일이 있는 경로를 추가합니다.  

    - "새로만들기"로 `%JAVA_HOME%\bin` 을 경로에 추가합니다.  
    - Java 를 인식하는 경로가 여러 개 있는 경우 가장 위에서부터 인식을 하기 때문에 새로 추가한 경로를 "위로 이동" 버튼을 눌러서 가장 위로 이동시켜 줍니다.  

![JDK_Install(7)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(7).png)  

<br>  

### Java 버전 변경을 위한 설정  

> 여러 버전의 Java 를 실행하기 위해서는 다른 버전을 사용할 때마다 시스템 변수에서 경로를 변경해주어야 하는데 번거롭기 때문에 명령 프롬프트에서 간단히 경로를 변경할 수 있도록 스크립트를 작성합니다.  

- 여러 버전의 JDK 가 설치되어 있는 폴더에 "scripts" 폴더를 생성 후 시스템 변수의 Path 에 추가합니다.  

![JDK_Install(8)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(8).png)  

<br>  

- 설치된 JDK 의 버전별로 `.bat` 파일을 만들어 줍니다. 

- text 파일을 생성하고 저장할 때 파일형식을 "모든파일"로 선택 후 파일명에 `.bat` 를 붙이면 `.bat` 파일이 생성됩니다.   

- `.bat` 파일을 scripts 폴더 안에서 생성할 경우 오류가 날 수 있기 때문에 외부에서 파일 생성 후 scripts 폴더로 이동합니다.  

```bat
:: bat 파일 작성 내용
@echo off
:: Path 를 변경하는 부분
set JAVA_HOME={JDK 주소}
set Path=%JAVA_HOME%\bin;%Path%
:: 아래 내용을 출력 및 실행
echo Java {JDK version} activated.
java -version

:: java8.bat 파일 내용
@echo off
set JAVA_HOME=C:\Program Files\Java\jdk1.8.0_202
set Path=%JAVA_HOME%\bin;%Path%
echo Java 8 activated.
java -version

:: java17.bat 파일 내용
@echo off
set JAVA_HOME=C:\Program Files\Java\jdk-17.0.3.1
set Path=%JAVA_HOME%\bin;%Path%
echo Java 17 activated.
java -version
```  

- 명령 프롬프트를 실행해서 "java8" 또는 "java17" 로 명령어를 입력하면 해당 bat 파일이 실행되면서 JDK 경로가 변경됩니다.  

![JDK_Install(9)](https://raw.githubusercontent.com/morisYu/morisyu.github.io/74a0c5f5ae8bee468beb0f7164a293a543b00179/assets/images/tools/JDK_Install(9).png)  

<br>  





<br><br><br>  

# <strong>Reference</strong>  

- [Java EE 와 SE 의 개념과 차이](https://doozi316.github.io/java/2020/07/01/WEB20/){:target="_blank"}  
- [환경변수를 설정하는 이유](https://www.lifencoding.com/software/26?p=1){:target="_blank"}  
- [설치한 여러 JDK 간편하게 전환](https://computer-science-student.tistory.com/467){:target="_blank"}  