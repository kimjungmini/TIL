본 문서는 https://poiemaweb.com/css3-syntax를 공부하고 내용을 정리한 문서입니다. 이 글에 작성된 모든 글 이미지의 저작권은 사이트 주인에게 있습니다.

---

CSS는 HTML이나 XML 같은 구조화된 문서가 화면 종이 등에 어떻게 렌더링 될 지를 정의하는 문서이다.

![](https://poiemaweb.com/img/html-css.png)

HTML5에서는 **HTML은 정보 구조화, CSS는 styling 정의**라는 역할이 명확히 구분 되어 있다.  
따라서 절대로 HTML에서 자체적으로 스타일을 주려는 습관을 가지지 말자.

# Selector(선택자)

스타일을 정의하기 위해서는 **스타일을 적용할 수 있는 HTML 요소를 선택할 수 있어야 한다** 셀렉터는 HTML 요소를 선택하기 위해 CSS에서 제공하는 기능이다.

```css
h1 {
  color: red;
  font-size: 12px;
}
```

위와 같은 구문을 rule set이라고 하며 이와 같은 rule set의 집합을 stylesheet라고 한다.

# 속성과 값

셀렉터로 HTML 요소를 선택하고 {} 내에 속성과 값을 지정하는 것으로 다양한 style을 정의할 수 있다. 속성은 표준스펙으로 정의되어 있는 것을 사용하여야 한다. 여러개의 프로퍼티를 동시에 지정할 수 있으며 ;로 구분한다.

```css
h1 {
  color: red; /*속성: 값*/
  font-size: 12px;
}
```

# HTML CSS 연동

## Link style

HTML 외부에 있는 CSS 파일을 로드하는 방식 가장 일반적으로 사용 됨.

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="css/style.css" />
    <!--외부에 있는 CSS 연결-->
  </head>
  <body>
    <h1>Hello CSS!</h1>
    <p>This is paragraph</p>
  </body>
</html>
```

```css
/*css/style.css*/
h1 {
  color: red;
}

p {
  background: blue;
}
```

## Embededding style

HTML 내부에 CSS를 포함시키는 방식 매우 간단한 페이지에서는 이렇게 하는 방식이 편할 수 있겠지만 실무에서는 HTML CSS를 명확하게 분리하여 따로 관리하는 것이 유지 보수에 좋음

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1 {
        color: red;
      }

      p {
        background: blue;
      }
    </style>
  </head>
  <body>
    <h1>Hello CSS!</h1>
    <p>This is paragraph</p>
  </body>
</html>
```

## Inline style

HTML요소의 style속성에 css를 기술하는 방식 js가 동적으로 css를 생성할 때 사용하는 경우가 종종 있음.

```html
<!DOCTYPE html>
<html>
  <body>
    <h1 style="color: red;">Hello CSS!</h1>
    <p style="background: aqua;">This is paragraph</p>
  </body>
</html>
```

# Reset CSS

모든 웹 브라우저는 디폴트 스타일을 가지고 있음 그래서 CSS가 없어도 잘 동작함  
하지만 웹 브라우저마다 디폴트 스타일이 제각각이기 떄문에 css를 적용하는데 어려움이 있을 수 있음 이러한 문제를 해결하기 위해서 모든 브라우저의 스타일을 초기화 시켜주는 Reset CSS를 많이 활용함

```css
/* http://meyerweb.com/eric/tools/css/reset/
  v2.0 | 20110126
  License: none (public domain)
*/

html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}
body {
  line-height: 1;
}
ol,
ul {
  list-style: none;
}
blockquote,
q {
  quotes: none;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
```
