---
published: true
layout: single
title: "[Tools] Visual Studio Code Extension"
subtitle: 
categories: [tools]
tag: [tools, vscode, extension]
toc: true
toc_sticky: true
---  

# [Tools] Visual Studio Code Extension  

## Auto Close Tag  

- 코드 작성 시 여는 태그와 닫는 태그를 일일이 입력할 필요없이, 여는 태그만 입력하면 자동으로 닫는 태그가 완성됩니다.  

> 사용방법  

- 여는 태그를 작성하면 자동으로 닫는 태그가 완성이 되며, `Alt+.` 을 누르면 현재 커서가 있는 태그의 닫는 태그가 생성됩니다.  

[![vscode_extension_Auto_Close_Tag](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Auto_Close_Tag.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag){:target="_blank"}  

<br>  

## Auto Rename Tag  

- 작성된 태그를 수정하는 경우 여는 태그 또는 닫는 태그를 수정하면 짝을 이루는 태그의 이름도 자동으로 수정됩니다.  

> 사용방법  

- 태그를 수정하면 짝을 이루는 태그도 자동으로 수정됩니다.  

[![vscode_extension_Auto_Rename_Tag](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Auto_Rename_Tag.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag){:target="_blank"}  

<br>  

## Bookmarks  

- 북마크 기능을 제공합니다.  

> 사용방법  

- 북마크를 지정할 코드를 선택 후 `Ctrl+Alt+K` 를 누르면 해당 줄 앞에 북마크 표시가 됩니다. 왼쪽에 있는 북마크 확장탭에서 북마크 설정된 목록을 전부 볼 수 있으며, 해당 북마크의 레이블을 수정해서 알아보기 쉽게 할 수도 있습니다. `Ctrl+Alt+J` 또는 `Ctrl+Alt+L` 을 눌러서 북마크 표시된 코드로 이동할 수 있습니다.  

[![vscode_extension_Bookmarks](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Bookmarks.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=alefragnani.Bookmarks){:target="_blank"}  

<br>  

## Bracket Pair Colorizer  

- 짝을 이루는 괄호에 같은 색을 입혀줍니다.  

- 해당 확장 플러그인은 오랫동안 인기를 얻어 VS Code의 기본 기능이 되었기 때문에 따로 설치할 필요가 없습니다.  

> 사용방법  

- 괄호를 사용하면 자동으로 괄호에 색이 입혀지며, 설정파일(settings.json)을 수정하여 괄호의 색을 변경할 수도 있습니다.  

```json
// Bracket Pair Colorizer 활성화 코드
"editor.bracketPairColorization.enabled": true,
"editor.guides.bracketPairs":"active",

// 아래 코드를 추가해서 괄호의 색상을 수정하거나 추가
"workbench.colorCustomizations": {
"editorBracketHighlight.foreground1": "#ffb86c",
"editorBracketHighlight.foreground2": "#8be9fd",
"editorBracketHighlight.foreground3": "#bd93f9",
"editorBracketHighlight.foreground4": "#50fa7b",
"editorBracketHighlight.foreground5": "#f1fa8c",
"editorBracketHighlight.foreground6": "#abb2c0",
"editorBracketHighlight.unexpectedBracket.foreground": "#ff5555"
}
```  

[![vscode_extension_Bracket_Pair_Colorize](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Bracket_Pair_Colorizer.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer-2){:target="_blank"}  

<br>  

## Code Runner  

- Java, Javascript, C/C++ 등 다양한 언어의 코드를 VSCode에서 실행할 수 있습니다.  

> 사용방법  

- Javascript를 실행하기 위해서는 node.js가 설치되어있어야 합니다. 만약 node.js가 설치되지 않은 상태에서 확장 플러그인을 설치한 경우에는 node.js를 설치 후 VSCode를 재시작하면 사용할 수 있습니다.  

- 작성된 Javascript 코드에서 실행하고 싶은 부분을 선택 후 마우스 오른쪽 클릭으로 "Run Code"를 실행하거나 `Ctrl+Alt+N` 으로 코드를 실행하면 아래에 콘솔창이 생기면서 코드 실행결과가 나옵니다. 코드 실행 중 멈추고 싶을 경우 `Ctrl+Alt+M` 으로 코드 실행을 중지할 수 있습니다. 

[![vscode_extension_Code_Runner](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Code_Runner.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner){:target="_blank"}  

<br>  

## Code Spell Checker  

- 코드 작성 시 스펠링을 확인하고 표시를 해줍니다.  

> 사용방법  

- 코드 작성 시 일반적인 단어가 아닐 경우 단어에 밑줄이 생기고, 해당 단어를 선택 후 `Ctrl+.` 를 누르면 비슷한 단어 또는 해당 단어는 프로젝트에서 무시하도록 추가할 수 있습니다.  

- settings.json 코드를 추가하여 계속 무시할 단어를 추가할 수 있습니다.  

```json
// "constanss" 라는 단어는 앞으로 스펠링 확인을 하지 않도록 목록에 추가
"cSpell.userWords": [
    "constanss"
]
```  

[![vscode_extension_Code_Spell_Checker](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Code_Spell_Checker.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker){:target="_blank"}  

<br>  

## CSS Peek  

- html 파일에서 특정 id나 class에 어떤 CSS를 적용하였는지 쉽게 확인할 수 있습니다.  

> 사용방법  

- `Ctrl`키를 누른 상태에서 id 또는 class명 위에 마우스를 올리면 현재 적용되어있는 CSS 를 보여주며, 클릭을 하면 CSS 파일에서 해당 위치로 커서가 이동합니다.  

[![vscode_extension_CSS_Peek](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_CSS_Peek.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=pranaygp.vscode-css-peek){:target="_blank"}  

<br>  

## HTML CSS Support  

- HTML 에서 CSS 에 미리 작성되어있는 ID 또는 Class 속성을 사용 시 자동완성 기능을 제공합니다.  

> 사용방법  

- HTML에서 ID 또는 Class 작성 시 CSS 에 작성되어있는 ID 또는 Class 목록을 보여주어 전체 타이핑을 할 필요가 없습니다.  

- `Ctrl+space` 를 눌러 추천 키워드 목록을 볼 수 있습니다.  

[![vscode_extension_HTML_CSS_Support](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_HTML_CSS_Support.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css){:target="_blank"}  

<br>  

## Indent-rainbow  

- 코드 작성 시 들여쓰기를 컬러로 구분하여 코드의 구조를 쉽게 분석할 수 있습니다.  

> 사용방법  

- 코드 작성 시 들여쓰기를 하면 들여쓰기 부분이 자동으로 컬러로 채워집니다.  

- settings.json 코드를 추가하여 들여쓰기 컬러를 추가하거나 수정할 수 있습니다.  

```json
// 기본 들여쓰기 색상
"indentRainbow.colors": [
    "rgba(255,255,64,0.07)",
    "rgba(127,255,127,0.07)",
    "rgba(255,127,255,0.07)",
    "rgba(79,236,236,0.07)"
],
// tab 크기의 들여쓰기가 아닌 경우(띄어쓰기 한 칸 크기)
"indentRainbow.errorColor": "rgba(128,32,32,0.6)"
```  

[![vscode_extension_indent_rainbow](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_indent_rainbow.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow){:target="_blank"}  

<br>  

## IntelliCode  

- Python, TypeScript/Javascript 또는 VSCode에서 Java 개발자를 위한 AI 지원 개발 기능을 제공합니다.  

- 코드 작성 시 현재 행에서 가장 관련이 높은 명령어를 별표 아이콘으로 추천을 해줍니다.  

> 사용방법  

- TypeScript/Javascript 의 경우 바로 코드를 작성하다보면 관련있는 명령어를 추천해줍니다.  

- 그 외 다른 언어는 각 언어에 필요한 확장 플러그인을 설치 후 코드를 작성하면 됩니다.  

[![vscode_extension_HTML_CSS_Support](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_IntelliCode.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode){:target="_blank"}  

<br>  

## Korea Language Pack for Visual Studio Code  

- 한국어 버전으로 VS Code를 사용할 수 있도록 해주는 확장 플러그인입니다.  

> 사용방법  

- `Ctrl+Shift+P` 를 눌러 "명령 팔레트"를 표시한 후 "표시 언어 구성" 명령을 선택하여 "ko"를 선택하고 프로그램을 재시작하면 한글이 적용됩니다.  

[![vscode_extension_Korean_Language_Pack](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Korean_Language_Pack.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ko){:target="_blank"}  

<br>  

## Live Server  

- HTML 코드 작성 시 수정내용이 실시간으로 브라우저에 반영되어 확인 가능하도록 하는 가상 서버입니다.  

> 사용방법  

- 우측 하단의 "Go live" 버튼을 클릭하거나, `Alt+L Alt+O`를 누르면 브라우저가 실행됩니다.  

- HTML 코드 수정 후 파일을 저장하면 브라우저에서 새로고침을 할 필요없이 수정된 내용이 바로 브라우저에 반영됩니다.  

- 종료할 경우 `Alt+L Alt+C`를 누르거나 우측 하단의 "Port:5500" 버튼을 클릭하면 됩니다.   

[![vscode_extension_Live_Server](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Live_Server.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer){:target="_blank"}  

<br>  

## Material Icon Theme  

- 아이콘 테마입니다. 여러 종류의 파일 아이콘을 지원합니다.  

> 사용방법  

- 확장 플러그인을 설치하면 자동으로 전체 파일과 폴더에 아이콘 테마가 적용이 되며, `Ctrl+Shift+P`를 눌러 명령 팔레트를 열고 "Material Icons" 를 검색하면 관련 명령이 나옵니다.  

| 명령 | 설명 |
| -- | -- |
| Activate Icon Theme | 아이콘 테마를 활성화합니다. |
| Change Folder Color | 폴더 아이콘의 색상을 변경합니다. |
| Change Folder Theme | 폴더 아이콘의 디자인을 변경합니다. |
| Change Opacity | 아이콘의 불투명도를 변경합니다. |  

[![vscode_extension_Material_Icon_Theme](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Material_Icon_Theme.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme){:target="_blank"}  

<br>  

## Material Theme  

- VSCode 의 색상 테마를 설정할 수 있습니다.  

- settings.json 코드를 추가하여 키워드의 글꼴이나 색상을 수정할 수 있습니다.  

  1. `F1`을 눌러 커맨드 창을 열고 "Developer: Inspect Editor Tokens and Scope"를 선택하면 각각의 키워드 선택 시 키워드에 적용된 색상이나 폰트 스타일 정보를 확인할 수 있습니다.  
  2. 각 키워드에서 "foreground" 부분의 속성을 확인합니다.  
  3. settings.json 에서 코드 내용을 추가합니다.  

```json
"editor.tokenColorCustomizations": {
  "textMateRules": [
      { // "keyword.control" 속성의 키워드에 대해 settings에 있는 스타일을 적용
        "scope": ["keyword.control"],
        "settings": {"foreground": "#d676e7", "fontStyle": ""}
      },
      { // "comment" 속성의 키워드에 대해 settings에 있는 스타일을 적용
        "scope": ["comment"],
        "settings": {"foreground": "#6ae3ab", "fontStyle": "italic"}
      }
  ]
}
```  

> 사용방법  

- `Ctrl+K Ctrl+T`를 누르거나 좌측 하단의 설정아이콘을 클릭하여 "색 테마"를 선택하면 여러가지 색상 테마를 설정할 수 있습니다.  

[![vscode_extension_Material_Theme](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Material_Theme.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme){:target="_blank"}  

<br>  

## Peacock  

- 메뉴 표시줄과 활동 표시줄의 테두리 색상을 지정하여 VSCode를 여러 개 실행 시 빠르게 원하는 프로젝트를 찾을 수 있습니다.  

> 사용방법  

- `F1`을 눌러 커맨드 창을 열고 "Peacock: Change to a Favorite Color"를 입력 후 목록에 있는 색상 중 원하는 색을 선택하면 적용됩니다.  

[![vscode_extension_Material_Theme](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Peacock.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=johnpapa.vscode-peacock){:target="_blank"}  

<br>  

## Prettier  

- 설정한 양식에 맞게 자동으로 코드를 정렬해줍니다.  

> 사용방법  

- 설정(`Ctrl+,`)에서 "Prettier" 를 검색 후 UI 창에서 적용할 내용을 설정해서 사용이 가능합니다.  

- Prettier의 설정은 아래의 순서로 적용이 됩니다.  
  1. 먼저 'settings.json' 에 설정한 세팅값을 적용합니다.  
  2. 만약 프로젝트에 EditorConfig의 설정파일인 '.editorconfig' 가 있으면 이 설정을 덮어씁니다.  
  3. 마지막으로 Prettier의 고유한 설정파일인 '.prettierrc' 가 프로젝트에 있으면 이 값을 최종적으로 적용하게 됩니다.  

```json
// settings.json 에서 Prettier 의 설정을 추가할 때는 "prettier.설정명"으로 코드를 작성하고 .pretierrc 에서는 prettier를 제외한 "설정명"으로 코드를 작성하면 됨
{ 
    // 한 줄이 이 글자수를 넘게 되면 줄바꿈되어 코드가 정리됨
    "prettier.printWidth": 80,

    // 탭을 눌렀을 때 몇 칸이 띄어지는지를 설정
    "prettier.tabWidth": 4,

    // 홑따옴표를 쓸건지 설정, false 설정 시 홑따옴표를 강제로 쌍따옴표로 변경
    "prettier.singleQuote": "true",

    // 객체, 배열, 함수 등의 후행에 쉼표를 찍을 지 제어(none: 쉼표를 붙이지 않음, es5: es5에서 유효한 후행쉼표 붙임, all: 가능하면 후행 쉼표를 붙임)
    "trailingComma": "all",

    // 객체 리터럴 내부의 공백을 제어
    "prettier.bracketSpacing": "true", 

    // jsx 요소의 마지막 다음 줄에 닫기를 표시함
    "prettier.jsxBracketSameLine": "false", 

    // javascript에서 사용되며 파서를 설정함
    "prettier.parser": "babylon", 

    // 문장 뒤에 세미콜론을 붙일지 뺄지를 설정
    "semi": "true",

    // true일 경우 탭이 있는 줄을 들여쓰기 함
    "useTabs": "false",

    // 마크다운은 공백 및 줄바꿈이 중요한 요소이므로 여러 줄에 걸쳐 산문을 랩핑
    "prettier.proseWrap": "preserve", 

    // 단독 화살표 함수의 매개변수 주위에 괄호를 자동으로 붙임
    "arrowParens": "avoid",

    // jsx에서 쌍따옴표 대신 홑따옴표 사용
    "prettier.jsxSingleQuote": "false", 

    // HTML 파일의 전역 공백 감도 설정
    "prettier.htmlWhitespaceSensitivity": "css", 

    // EoF 방식
    "prettier.endOfLine": "auto", 

    // 객체의 속성이 인용될 때 변경
    "prettier.quoteProps": "as-needed", 

    // prettierconfig 파일 적용여부 설정
    "prettier.requireConfig": "false", 

    // Prettier 기능을 비활성화 할 언어 ID 목록
    "prettier.disableLanguages": ["vue"]

    // prettier가 적용되지 않게 하려면 .prettierignore에 파일명을 기록
}
```  

[![vscode_extension_Prettier](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Prettier.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode){:target="_blank"}  

<br>  

## Quokka.js  

- Javascript 또는 TypeScript 작성 중 바로 코드를 실행하며 오류 및 출력내용 확인이 가능합니다.  

> 사용방법  

- `Ctrl+Shift+P` 명령팔레트에서 "Quokka" 를 입력하여 다양한 명령을 실행할 수 있습니다. `Ctrl+K L`을 눌러서 새로운 파일을 생성하거나 `Ctrl+K Q`를 눌러서 현재 파일(Javascript 또는 TypeScript)에서 출력창을 띄울 수 있습니다. 이 후 코드를 작성하면 실시간으로 오류를 검토하고 출력내용을 확인할 수 있습니다.  

[![vscode_extension_Quokka](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Quokka.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=WallabyJs.quokka-vscode){:target="_blank"}  

<br>  

## Settings Sync  

- 다른 컴퓨터에서 작업을 할 경우 개발환경 세팅을 위해 필요한 확장 플러그인들을 하나씩 새로 설치하는 것이 아니라 기존에 사용하던 플러그인들을 설정 파일 형태로 GitHub gist에 업로드해둔 후 필요할 때 다운로드하여 환경을 동기화시킬 수 있습니다. (GitHub 계정 연동 필요)  

- 해당 기능은 Visual Studio Code 에서도 지원을 합니다.(좌측 하단 관리 버튼에서 설정 동기화 켜기 실행)  

> 사용방법  

1. github에서 "Developer settings"로 이동 후 `gist`를 선택하여 "Personal access token"을 생성합니다.(기존 토큰이 있는 경우 토큰 수정에서 `gist` 선택 가능)  
2. VSCode 에서 "Settings Sync" 플러그인을 설치 후 `Ctrl+Shift+P` 명령팔레트에서 "Sync: 고급옵션" -> "Sync: 설정열기" 로 이동 후 엑세스 토큰 코드 부분에 github에서 생성한 토큰 코드를 입력하면 자동으로 "Gist ID" 생성됩니다.(Gist ID는 따로 저장)  
3. 설정이나(settings.json) 플러그인 등 변경사항이 있는 경우 `Shift+Alt+U`를 눌러 변경된 설정사항을 업로드, 업데이트를 합니다.  
4. 설정을 다운받을 경우 `Shift+Alt+D`를 눌러 github에 업로드된 설정사항을 다운로드 할 수 있습니다.  

[![vscode_extension_Settings_Sync](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/tools/vscode_extension_Settings_Sync.png?raw=true)](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync){:target="_blank"}  




<br><br><br>  

# <strong>Reference</strong>  

- [유용한 VSCode 익스텐션을 공유합니다.](https://velog.io/@boxerof8/%EC%9C%A0%EC%9A%A9%ED%95%9C-VSCode-%ED%99%95%EC%9E%A5%EC%9D%84-%EA%B3%B5%EC%9C%A0%ED%95%A9%EB%8B%88%EB%8B%A4){:target="_blank"}  
- [내가 전에 알았더라면 좋았을 최고의 VS 코드 확장](https://youtu.be/ZqW8JT1gt4U){:target="_blank"}  
- [VScode Code Formater인 Prettier 완벽 적용하기](https://uxgjs.tistory.com/150){:target="_blank"}  
- [vscode 설정 저장(Settings Sync) 동기화 사용하기](https://kimyang-sun.tistory.com/entry/VSCode-vscode-%EC%84%A4%EC%A0%95-%EC%A0%80%EC%9E%A5Settings-Sync-%EB%8F%99%EA%B8%B0%ED%99%94-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0){:target="_blank"}  
- [Visual Studio Code 주석 및 키워드 글꼴 스타일 설정하기](https://dearmycode.tistory.com/8){:target="_blank"}  