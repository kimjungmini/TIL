본 내용의 글은 https://poiemaweb.com/html5-syntax를 공부하며 정리하는 문서입니다.

# HTML5
HTML은 웹페이지를 기술하기 위한 마크업 언어이다.  
정확하게는 웹페이지의 **내용** **구조**를 담당하고 있다.

# Hello HTML
```html
<!DOCTYPE>
<html>
  <head>
    <meta charset="utf-8">
    <title>Hello World</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>안녕하세요! HTML5</p>
  </body>
</html>
```
- html5 문서는 반드시 <span style="color: red"><!DOCTYPE></span>으로 시작하여 문서 형식을 HTML5로 기술한다.
- 실제적인 문서는 2행부터 시작되며 <span style="color: red">\<html></span>과 <span style="color: red">\</html></span> 사이에 기술한다.
- <span style="color: red">\<head></span> 와 <span style="color: red">\</head></span> 사이에는 document title, 외부 파일의 참조, <span style="color: red">메타 데이터</span>의 설정 등이 위치하며 이 정보들은 브라우저에 표시되지 않는다.
- 웹 브라우저에 출력되는 모든 요소는 <span style="color:red">\<body></span> 와<span style="color:red">\</body></span>사이에 위치한다.

# HTML5의 기본 문법
HTML 요소는 시작태그와 종료태그 그리고 태그 사이에 위치한 content로 구성된다.

```html
<p> content </p>
```
태그는 대소문자를 구분하지 않지만 W3C에서는 소문자를 추천하고 있으므로 소문자로 추천하는것이 일반적이다.

## 요소의 중첩
---
요소는 중첩될 수 있으며 이러한 중첩 관계로 정보를 구조화 하는 것이다.
```html
<!DOCTYPE>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    <h1>안녕하세요! </h1>
    <p> 반갑습니다 </p>
  </body>
</html>
```

html 요소는 웹 페이지를 구성하는 모든 요소를 포함한다. 위 예제에서 html요소는 body요소를 포함하고 body요소는 h1요소와 p요소를 포함하고 있다.

이러한 중첩 관계를 통해서 웹 페이지의 구조를 표현하는 것이다.  
중첩관계를 시각적으로 파악하기 쉽게 indent(들여쓰기)를 활용한다. 일반적으로 2칸을 많이 사용하는 것 같다. 보기 좋은 코드는 읽기 쉬우며 **읽기 쉬운 코드**는 **좋은 코드**이다

## 빈 요소
content를 가질 수 없는 요소를 빈 요소라고 한다. 빈 요소는 content 없이 attribute만을 가진다

```html
<meta charset="utf-8">
```

대표적인 빈 요소는 아래와 같다
- br
- hr
- img
- input
- link
- meta

## Attribute
---
attribute란 요소의 성질, 특징을 정의하는 명세이다.  
요소는 attribute를 가질 수 있으며 요소에 추가적인 정보를 제공한다.
attribute는 시작태그에 위치해야 하며 이름과 값의 쌍을 이룬다.

```html
<img src="/html.jpg" width="104" height="142">
```

위 예시에서 attribute src는 이미지 파일의 경로와 파일명 width는 너비 height 높이 정보를 브라우저에 알려준다.

### 자주 사용하는 attribute
attribute | description
--|--
id | 유일한 식별자를 요소에 지정, 중복 불가능
class | stylesheet에 정의된 class를 요소에 지정 중복 가능
hidden | css의 hidden과는 다르게 의미상으로도 브라우저에 노출이 안된다.
lang | 지정된 요소의 언어를 지정한다. 검색엔진의 크롤링 시 웹페이지의 언어를 인식할 수 있게 된다.
style | 요소에 인라인 스타일을 지정한다.
tabIndex | 사용자가 키보드로 페이지를 내비게이션시 이동 순서를 지정한다
title | 요소에 관한 제목을 지정한다

## 주석
주석은 주로 개발자에게 코드를 설명하기 위해서 사용하며 브라우저는 주석을 화면에 표시하지 않는다.

```html
<!--주석은 화면에 표시되지 않는다.-->
<p>Lorem ipsum dolor sit amet</p>
```

