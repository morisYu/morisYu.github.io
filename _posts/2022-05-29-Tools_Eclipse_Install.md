---
published: true
layout: single
title: "[Tools] Eclipse 설치 및 설정"
subtitle: 
categories: [tools]
tag: [tools, eclipse]
toc: true
toc_sticky: true
---  

# [Tools] Eclipse 설치 및 설정  

### 설치파일 다운로드  

> 이클립스 다운로드 페이지에 접속하여 Download Packages 페이지로 이동합니다.  

- [이클립스 다운로드 페이지](https://www.eclipse.org/downloads/){:target="_blank"}  

![eclipse_install(1).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(1).png?raw=true)  

<br>  

> Download Packages 페이지에서 최신 버전의 Eclipse 를 설치할 수도 있지만,  Eclipse 버전 별 지원하는 JDK의 버전이 다르기 때문에 사용하는 JDK 버전을 확인하여 그에 맞는 Eclipse 버전을 설치해야 합니다. 이전 버전의 Eclipse 는 Download Packages 페이지의 우측 하단에서 "Older Versions"를 선택하면 모든 버전의 Eclipse 를 볼 수 있습니다.  

- [이클립스 버전별 지원하는 JDK 버전 확인](https://wiki.eclipse.org/Eclipse/Installation){:target="_blank"}  

![eclipse_install(2).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(2).png?raw=true)  

<br>  

> 원하는 버전의 Eclipse 를 선택하면 여러 Packages 를 볼 수 있는데 내용을 확인 후 "Eclipse IDE for Java EE Developers" 를 운영체제에 맞게 다운로드 해줍니다.  

- Eclipse IDE for Java Developers 는 자바만을 사용한 개발을 위한 통합 개발 환경입니다.   

- Eclipse IDE for Java EE Developers 는 기본적인 자바 개발 및 웹 개발(Servlet, JSP 등)을 위한 통합 개발 환경입니다.  

- 저는 웹 개발을 함께 진행하기 때문에 Eclipse IDE for Java EE Developers 를 다운로드 했습니다.  

![eclipse_install(3).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(3).png?raw=true)  

<br>  

### Eclipse 설치  

> Eclipse 의 최신 버전을 설치할 경우 설치파일이 다운로드 되면 설치파일을 실행하여 "Eclipse IDE for Java EE Developers" 를 선택 후 원하는 경로에 파일을 설치합니다. 구 버전의 경우 압축파일로 다운로드가 되는데 원하는 경로에 압축파일을 해제하고 압축파일 안에 있는 "eclipse.exe" 를 실행하면 바로 이클립스를 사용 가능합니다.  

- 여러 버전의 Eclipse를 사용할 경우 같은 경로 안에 여러 버전의 Eclipse 폴더를 넣어두는 것이 관리하기 좋습니다.  

![eclipse_install(4).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(4).png?raw=true)  

<br>  

![eclipse_install(5).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(5).png?raw=true)  

<br>  

![eclipse_install(6).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(6).png?raw=true)  

<br>  

![eclipse_install(7).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(7).png?raw=true)  

<br>  

### Eclipse 실행 및 환경설정  

> 설치한 Eclipse IDE 를 실행하면 workspace 를 선택하는 창이 뜨는데 "Browse..." 을 선택하여 다른 workspace 를 선택할 수 있습니다.  

- 여러 버전의 Eclipse IDE 를 사용하는 경우 가능하면 같은 workspace 를 사용하지 않도록 프로젝트별로 다른 workspace 를 만들어줍니다.  

![eclipse_install(8).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(8).png?raw=true)  

<br>  

> Eclipse 가 실행되면 Welcome 페이지가 뜨면서 Eclipse 설명이 나오는데 이 창을 닫고 프로젝트를 시작할 수 있습니다.  

- "Eclipse IDE for Java EE Developers" 를 설치했기 때문에 기본적으로 웹 개발을 할 수 있는 java EE perspective 가 활성화되어 있는데 웹 개발을 여기에서 하면 됩니다.  

- Java 만을 사용해서 개발하기 위해서는 Java perspective 를 활성화 해야 합니다.  

- 메뉴바에서 Window → Perspective → Open Perspective → Java 를 선택해서 perspective 를 추가 후 메뉴의 가장 오른쪽 끝에 있는 perspective 아이콘을 선택하여 Java 또는 Java EE perspective 로 변경할 수 있습니다.  

![eclipse_install(9).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(9).png?raw=true)  

<br>  

#### JDK 버전 추가  

> Eclipse 에서 여러 버전의 JDK 를 사용하는 경우 JDK 버전을 추가해야 합니다.  

- 메뉴바에서 Window → Preferences → Java → Installed JREs 선택  

![eclipse_install(10).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(10).png?raw=true)  

<br>  

- Add 버튼을 누르고 Standard VM 을 선택하여 "Next" 를 눌러주면 "JRE home" 을 선택할 수 있습니다. (JDK 가 설치된 경로를 찾아서 선택하면 됨)  

- 추가된 JDK 버전을 선택해주면 기본으로 설정됩니다.  

![eclipse_install(11).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(11).png?raw=true)  

<br>  

- Window → Preferences → Java → Compiler 를 선택 후 변경된 JRE 버전에 맞게 JDK Compiler compliance level 를 바꿔줍니다.  

![eclipse_install(12).png](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/eclipse_install(12).png?raw=true)  

<br>  

#### 환경설정(인코딩)  

- 작업하는 환경에 따라 유니코드의 인코딩 방식이 다를 수 있는데, 서로 다른 인코딩 방식을 사용하는 경우 한글이 깨지는 경우가 발생합니다. 따라서 인코딩 방식을 일치할 필요가 있는데 가장 많이 사용되는 UTF-8 인코딩 방식으로 변경을 하도록 합니다.  

1. Window → Preferences 에서 필터에서 "encoding" 을 검색합니다.  

2. General → Content Types → Text 에서 encoding 을 "UTF-8" 로 작성 후 Update  

3. General → Workspace 에서 encoding 을 "UTF-8" 선택 후 Apply  

4. General → Web 에서 "CSS Files", "HTML Files", "JSP Files" 의 encoding 을 "ISO 10646/Unicode(UTF-8)" 로 선택 후 Apply  

5. General → XML 에서 "XML Files" 의 encoding 을 "ISO 10646/Unicode(UTF-8)" 로 선택 후 Apply  

6. General → Editors → Text Editors → Spelling 에서 encoding 을 "UTF-8" 로 선택 후 Apply  

- 개별 프로젝트나 개별 파일의 경우 해당 프로젝트 폴더나 파일을 우클릭하여 Properties → Resource 에서 encoding 을 "UTF-8" 선택 후 Apply 해서 각 프로젝트나 파일별로 encoding 설정을 바꿀 수 있습니다.  

#### 환경설정(초기 세팅)  

> Validation(유효성 검사) 해제

- 작업 시 Validating 으로 인해 작업이 느려지는 경우 해당 설정을 끄면 됩니다.  

- Window → Preference → Validation 에서 Build 컬럼의 모든 체크를 해제합니다.  

- 설정 후에 "Validation Settings Changed" 경고창이 뜨면 "No" 를 선택하면 됩니다. (Validation 설정을 다시 원래대로 하겠다는 뜻입니다.)  

> 자동 업데이트 해제  

- Window → Preferences → Install/Update → Automatic Updates 에서 체크를 해제합니다.  

> Heap 메모리 상태 표시  

- 이클립스 우측 하단에 최대 Heap size 와 현재 사용중인 Heap size 를 볼 수 있습니다.  

- Window → Preferences → General 에서 "Show heap status" 를 체크합니다.  

> 테마 설정  

- 이클립스에 기본 저장되어있는 테마를 선택할 수도 있고, Plug in 을 설치할 수도 있습니다.  

- Help → Eclipse Marketplace → Find → "Darkest Dark Theme" 검색 후 설치하면 바로 테마를 설정할 수 있고 재시작하면 적용됩니다.  

- Window → Preferences → General → Appearance 에서 테마를 다시 선택할 수 있습니다.  

### Java 프로젝트 생성  

1. Java perspective 가 활성화 된 상태에서 File → New → Java Project 선택  

2. 프로젝트 생성 창이 뜨면 프로젝트 명, 자바 버전을 선택 후 프로젝트를 생성합니다.  

3. 생성한 프로젝트 폴더 안에 있는 src 폴더를 우클릭 후 New → Package 를 선택하여 패키지를 생성합니다.  

4. 생성한 패키지를 우클릭 후 새로운 파일을 생성합니다.  

### Web 프로젝트 생성  

1. Java EE perspective 가 활성화 된 상태에서 File → New → Dynamic Web Project 선택  

2. "Target runtime" 에서 Tomcat 이 제대로 선택되어있는지 확인 후 Next 를 눌러줍니다.  

3. 디렉토리 구조를 확인 후 마지막에 web.xml 파일을 생성하기 위해 체크박스를 선택합니다.  
    
    - Eclipse 버전에 따라 디렉토리 구조가 다르게 생성됩니다.  
        
        - 프로젝트 폴더 > src > main > webapp 으로 생성되면 webapp 에 파일을 생성해서 작업하면 됩니다.  

        - 프로젝트 폴더 > WebContent 로 생성되면 WebContent 에 파일을 생성해서 작업하면 됩니다.  

#### 프로젝트의 자바 버전 변경  

1. 자바 버전을 변경하고자 하는 프로젝트를 우클릭 후 Properties → Project Facets 에서 "Java" 의 버전을 변경해줍니다.  

2. Build Path 변경을 위해 프로젝트의 Properties → Java Build Path → Libraries 에서 현재 JRE 버전을 더블클릭하면 "Edit Library" 창이 뜹니다.  

3. "Alternate JRE" 의 목록을 보면 추가한 JDK 버전을 확인할 수 있고, 변경한 자바 버전을 선택해줍니다.  





<br><br><br>  

# <strong>Reference</strong>  

- [이클립스 설치 방법](https://parkjye.tistory.com/33){:target="_blank"}  
- [이클립스 JDK 버전 설정하기](https://0jaeyoung.tistory.com/3){:target="_blank"}  
- [이클립스 "UTF-8" 인코딩 설정](https://parkjye.tistory.com/35){:target="_blank"}  
- [여러가지 초기 세팅](https://inseok9068.github.io/eclipse/eclipse-setting/){:target="_blank"}  
- [프로젝트 자바버전 바꾸기](https://yongtech.tistory.com/98){:target="_blank"}  