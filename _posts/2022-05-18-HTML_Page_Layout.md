---
published: true
layout: single
title: "[HTML] 웹 페이지 레이아웃 잡기"
subtitle: 
categories: [html]
tag: [html, layout]
toc: true
toc_sticky: true
---  

# [HTML] 웹 페이지 레이아웃 잡기  

## HTML 레이아웃  

- 레이아웃(layout)이란, 특정 공간에 여러 구성 요소를 보기 좋게 효과적으로 배치하는 작업을 의미합니다.  
- HTML에서는 다음과 같은 방법으로 레이아웃을 작성할 수 있습니다.  

    - div 요소를 이용한 레이아웃  
    - HTML5 레이아웃  
    - table 요소를 이용한 레이아웃

<br>  

### div 요소를 이용한 레이아웃  

- div 요소는 CSS 스타일을 손쉽게 적용할 수 있으므로, 레이아웃을 작성하는데 자주 사용됩니다.  

```html  
<body>
    <div id="header">
        <h1>HEADER</h1>
    </div>
    <div id="nav">
        <h2>NAVIGATION</h2>
    </div>
    <div id="section">
        <h3>SECTION</h3>
    </div>
    <div id="footer">
        <h2>FOOTER</h2>
    </div>
</body>
```  

> 예시 사진(CSS 스타일 적용)  

![Page_Layout(1)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Page_Layout(1).png?raw=true)  

<br>  

### HTML5 레이아웃  

- HTML5 에서는 웹 페이지의 레이아웃만을 위한 별도의 요소들을 제공합니다.  

```html
<body>
    <header> <h1>HEADER</h1> </header>
    <nav><h2>NAVIGATION</h2></nav>
    <main>
        <h2>MAIN</h2>
        <section><h3>SECTION</h3></section>
        <article><h3>ARTICLE</h3></article>
        <aside><h3>ASIDE</h3></aside>
    </main>
    <footer><h3>FOOTER</h3></footer>
</body>
```  

> 예시 사진(CSS 스타일 적용)  

![Page_Layout(2)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Page_Layout(2).png?raw=true)  

<br>  

#### HTML5에 추가된 Semantic Element 의 종류  

| 태그 | 설명 |  
| :--: | -- |  
| `<article>` | 문서, 페이지, 애플리케이션, 또는 사이트 안에서 독립적으로 구분해 배포하거나 재사용할 수 있는 구획을 나타냅니다. |  
| `<aside>` | 문서의 주요 내용과 간접적으로만 연관된 부분을 나타냅니다. |  
| `<details>` | "열림" 상태일 때만 내부 정보를 보여주는 정보 공개 위젯을 제공합니다. `<summary>` 요소를 통해 요약이나 레이블을 제공할 수 있습니다. |  
| `<figcaption>` | 부모 요소인 `<figure>` 요소가 포함하는 다른 콘텐층 대한 설명 혹은 범례를 나타냅니다. |  
| `<figure>` | 독립적인 콘텐츠를 표현합니다. |  
| `<footer>` | 푸터는 일반적으로 작성자, 저작권 정보, 관련 문서 등의 내용을 담습니다. |  
| `<header>` | 소개 및 탐색에 도움을 주는 콘텐츠를 나타냅니다. |  
| `<main>` | 문서의 주요 콘텐츠를 나타냅니다. |  
| `<mark>` | 현재 맥락에 관련이 깊거나 중요해 표시 또는 하이라이트한 부분을 나타냅니다. |  
| `<nav>` | 문서의 부분 중 현재 페이지 내, 또는 다른 페이지로의 링크를 보여주는 구획을 나타냅니다. |  
| `<section>` | HTML 문서의 독립적인 구획은 나타내며, 더 적합한 의미를 가진 요소가 없을 때 사용합니다. |  
| `<summary>` | `<details>` 요소의 공개 상자에 대한 요약, 캡션 또는 범례를 지정합니다. |  
| `<time>` | 시간의 특정 지점 또는 구간을 나타냅니다. `datetime` 특성의 값을 지정해 보다 적절한 결과나, 알림 같은 특정 기능을 구현할 때 사용할 수 있습니다. |  

<br>  

### table 요소를 이용한 레이아웃  

- table 요소를 이용하여 레이아웃을 작성하는 방법은 오래전에 사용하던 방식이며, 현재는 거의 사용하지 않습니다.  
- table 요소는 레이아웃을 만들기 위해 설계된 요소가 아니므로, 테이블로 작성된 레이아웃은 수정이 매우 힘듭니다.  

```html
<body>
    <table width="100%" style="text-align:center; border:none">
        <tr>
            <td colspan="2" style="background-color:lightgrey; border: 2px solid black;"><h2>HEADER</h2></td>
        </tr>
        <tr>
            <td style="background-color:#ecb3fd; color:white; width:30%; border: 2px solid red;"><h2>NAVIGATION</h2></td>
            <td style="height:200px; text-align:left; border: 2px solid;"><p>SECTION</p></td>
        </tr>
        <tr>
            <td colspan="2" style="background-color:#FFCC00; border: 2px solid;"><h2>FOOTER</h2></td>
        </tr>
    </table>
</body>
```  

> 예시 사진(CSS 스타일 적용)  

![Page_Layout(3)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Page_Layout(3).png?raw=true)  

<br>  

## HTML5 문서 기본구조  

- HTML 은 크게 세 부분으로 나뉘어집니다.  

    - header: 메인 메뉴를 담당하는 nav, 회사 또는 사이트로고, 회원가입, 로그인, 검색창 같은 요소들이 들어갑니다.  
    - article: 본문의 내용을 담당합니다.  
    - footer: 회사 주소 또는 연락처 등의 정보를 넣습니다.  

<br>  

### HTML 문서 패턴  

- `<aside>` 는 웹사이트의 사이드 바 부분을 담당합니다. 서브메뉴나 광고 또는 부가적인 정보가 들어갑니다.  
- `<article>` 은 본문으로 `<h1>`, `<h2>` 같은 제목이 들어갈 수 있고 `<section>` 으로 별도의 섹션을 만들 수 있습니다.  
- `<figure>` 는 이미지 설명을 위해 추가할 수도 있습니다.  

> 예시 1  

![Page_Layout(4)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Page_Layout(4).png?raw=true) 

<br>  

> 예시 2  

![Page_Layout(5)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Page_Layout(5).png?raw=true)  

<br>

## 웹 페이지의 HTML 구조  

- 웹 페이지를 설계할 때, 먼저 할 일은 페이지를 가장 큰 단위로 나누는 것입니다.  
- 정해진 규칙은 없고 사이트의 목적에 따라 다양한 형태가 존재하지만 일반적으로는 `<header>`, `<main>`, `<footer>` 로 나누어집니다.  
- 모든 영역을 `<div>` 태그로 만드는 방법도 있지만 검색 엔진 최적화(SEO: Search Engine Optimization)를 위해 HTML5 의 Semantic Element를 활용하는 것이 좋습니다.  

<br>  

### 네이버 사이트의 HTML 구조 확인  

- 네이버 사이트를 위의 3가지 영역으로 나누면 아래와 같습니다.  
- 3 개의 큰 단위로 나뉘어진 영역의 내부는 다시 작은 단위의 영역으로 나뉘어집니다.  

![Naver_Layout(1)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Naver_Layout(1).png?raw=true)  

<br>  

> Header 영역  

- 사이트의 로고, 검색을 위한 입력, 여러 항목으로 이동할 수 있는 네비게이션 등 여러 부분으로 나뉘어집니다.  

![Naver_Layout(2)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Naver_Layout(2).png?raw=true)  

<br>  

> Main 영역  

- 메인은 다시 왼쪽과 오른쪽으로 나누어 준 후 각각 작은 부분으로 나뉘어집니다.  
- 왼쪽은 뉴스기사, 읽을거리 등의 항목으로 나뉘어집니다.  
- 오른쪽은 로그인, 광고, 쇼핑 등의 항목으로 나뉘어집니다.  

![Naver_Layout(3)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Naver_Layout(3).png?raw=true)  

<br>  

> Footer 영역  

- 푸터에서는 공지사항, 제작자 및 파트너 등의 항목으로 나뉘어집니다.  

![Naver_Layout(4)](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/html/Naver_Layout(4).png?raw=true)  

<br>  

### 사이트에서 HTML 구조를 확인하는 방법  

- 소스 코드 보기(단축키 `Ctrl+U`)를 사용해서 소스 코드로 HTML 구조를 확인할 수 있지만, 개발자 도구(단축키 `F12`)를 사용해서 좀 더 직관적으로 확인할 수 있습니다.  

    1. 분석하고자 하는 페이지에서 `F12` 를 눌러 개발자 도구를 실행합니다.  
    2. `Elements` 항목을 클릭하면 해당 페이지의 소스 코드를 볼 수 있습니다.  
    3. 소스 코드 위에 마우스를 가져가면 해당 코드가 표시되는 부분이 표시가 됩니다.  
    4. 소스 코드를 선택하게 되면 해당 부분의 CSS 코드도 확인이 가능합니다.  
    5. 페이지에서 소스 코드를 바로 찾으려면 개발자 도구창의 왼쪽 위에 `요소 선택` 버튼을 눌러줍니다.  
    6. 페이지에서 확인하고 싶은 요소를 클릭하면 관련된 코드가 선택이 됩니다.  

<br>  

- HTML 구성요소의 테두리를 설정하여 각 요소들의 배치를 확인할 수 있습니다.(사이트에 따라 적용이 되지 않는 곳도 있습니다.)  

    - 영역을 구분하기 위해 사용되는 태그 요소들을 DOM으로 조작하여 테두리의 설정을 바꿔줍니다.  
    - 개발자 도구의 `console` 창에 아래의 코드를 입력하여 실행합니다.  
    - 아래의 태그 외 다른 태그가 있는 경우 추가를 하거나 태그별로 색상을 바꿔줄 수 있습니다.  

```javascript
    ['div', 'span', 'ul', 'li', 'dd', 'dl', 'section', 'h1', 'a', 'img', 'form', 'button', 'header', 'footer', 'input', 'p'].forEach(e => {
    document.querySelectorAll(e).forEach(element => {
        element.style.outline = "1px solid dodgerblue"
    })
})
```  





<br><br><br>

# <strong>Reference</strong>  

- [레이아웃](http://www.tcpschool.com/html/html_space_layouts){:target="_blank"}  
- [HTML Semantic Elements](https://www.w3schools.com/html/html5_semantic_elements.asp){:target="_blank"}  
- [Semantics](https://developer.mozilla.org/ko/docs/Glossary/Semantics){:target="_blank"}  
- [HTML5의 기본 구조잡기, 많이 사용하는 문서패턴, 새로 추가된 태그](https://wonyoung2257.tistory.com/9){:target="_blank"}  
- [웹페이지 HTML 구조 한눈에 보는 꼼수](https://velog.io/@oneook/%EC%9B%B9%ED%8E%98%EC%9D%B4%EC%A7%80-HTML-%EA%B5%AC%EC%A1%B0-%ED%95%9C%EB%88%88%EC%97%90-%EB%B3%B4%EB%8A%94-%EA%BC%BC%EC%88%98){:target="_blank"}  
- [웹페이지 소스코드 보기](https://smorning.tistory.com/11){:target="_blank"}  