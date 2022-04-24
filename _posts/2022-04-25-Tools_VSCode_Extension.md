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

## Korea Language Pack for Visual Studio Code  

- 한국어 버전으로 VS Code를 사용할 수 있도록 해주는 확장 플러그인입니다.  

> 사용방법  

- `Ctrl+Shift+P` 를 눌러 "명령 팔레트"를 표시한 후 "표시 언어 구성" 명령을 선택하여 "ko"를 선택하고 프로그램을 재시작하면 한글이 적용됩니다.  

[![vscode_extension_Korean_Language_Pack]()](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ko){:target="_blank"}  

<br>  

## Auto Close Tag  

- 코드 작성 시 여는 태그와 닫는 태그를 일일이 입력할 필요없이, 여는 태그만 입력하면 자동으로 닫는 태그가 완성됩니다.  

> 사용방법  

- 기본적으로 여는 태그를 작성하면 자동으로 닫는 태그가 완성이 되며, `Alt+.` 을 누르면 현재 커서가 있는 태그의 닫는 태그가 생성됩니다.  

[![vscode_extension_Auto_Close_Tag]()](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ko){:target="_blank"}  

<br>  

## Auto Rename Tag  

- 작성된 태그를 수정하는 경우 여는 태그 또는 닫는 태그를 수정하면 짝을 이루는 태그의 이름도 자동으로 수정됩니다.  

> 사용방법  

- 기본적으로 태그를 수정하면 짝을 이루는 태그도 자동으로 수정됩니다.  

[![vscode_extension_Auto_Rename_Tag]()](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ko){:target="_blank"}  

<br>  

## Bracket Pair Colorizer  

- 짝을 이루는 괄호에 같은 색을 입혀줍니다.  

- 해당 확장 플러그인은 오랫동안 인기를 얻어 VS Code의 기본 기능이 되었기 때문에 따로 설치할 필요가 없습니다.  

> 사용방법  

- 괄호를 사용하면 자동으로 괄호에 색이 입혀지며, 설정파일(settings.json)을 수정하여 설정을 변경할 수도 있습니다.  

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

[![vscode_extension_Bracket_Pair_Colorize]()](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ko){:target="_blank"}  

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
// settings.json 에서 Prettier 의 설정을 추가할 때는 "perttier.설정명"으로 코드를 작성하고 .pretierrc 에서는 prettier를 제외한 "설정명"으로 코드를 작성하면 됨
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
    "prettier.bracketSpacing": "true", // 기본설정

    // jsx 요소의 마지막 다음 줄에 닫기를 표시함
    "prettier.jsxBracketSameLine": "false", // 기본설정

    // javascript에서 사용되며 파서를 설정함
    "prettier.parser": "babylon", // 기본설정

    // 문장 뒤에 세미콜론을 붙일지 뺄지를 설정
    "semi": "true",

    // true일 경우 탭이 있는 줄을 들여쓰기 함
    "useTabs": "false",

    // 마크다운은 공백 및 줄바꿈이 중요한 요소이므로 여러 줄에 걸쳐 산문을 랩핑
    "prettier.proseWrap": "preserve", // 기본설정

    // 단독 화살표 함수의 매개변수 주위에 괄호를 자동으로 붙임
    "arrowParens": "avoid",

    // jsx에서 쌍따옴표 대신 홑따옴표 사용
    "prettier.jsxSingleQuote": "false", // 기본설정

    // HTML 파일의 전역 공백 감도 설정
    "prettier.htmlWhitespaceSensitivity": "css", // 기본설정

    // EoF 방식
    "prettier.endOfLine": "auto", // 기본설정

    // 객체의 속성이 인용될 때 변경
    "prettier.quoteProps": "as-needed", // 기본설정

    // prettierconfig 파일 적용여부 설정
    "prettier.requireConfig": "false", // 기본설정

    // Prettier 기능을 비활성화 할 언어 ID 목록
    "prettier.disableLanguages": ["vue"]

    // prettier가 적용되지 않게 하려면 .prettierignore에 파일명을 기록
}
```  

[![vscode_extension_Prettier]()](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-ko){:target="_blank"}  

<br>  

## 




<br><br><br>  

# <strong>Reference</strong>  

- [유용한 VSCode 익스텐션을 공유합니다.](https://velog.io/@boxerof8/%EC%9C%A0%EC%9A%A9%ED%95%9C-VSCode-%ED%99%95%EC%9E%A5%EC%9D%84-%EA%B3%B5%EC%9C%A0%ED%95%A9%EB%8B%88%EB%8B%A4){:target="_blank"}  
- [VScode Code Formater인 Prettier 완벽 적용하기](https://uxgjs.tistory.com/150){:target="_blank"}  