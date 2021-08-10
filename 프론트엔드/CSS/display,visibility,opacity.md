# display 속성

| 속성값 키워드 | 설명                                                           |
| ------------- | -------------------------------------------------------------- |
| block         | block 특성을 가지는 요소로 지정                                |
| inline        | inline 특성을 가지는 요소로 지정                               |
| inline-block  | inline-block 특성을 가지는 요소(inline-block 레벨 요소)로 지정 |
| none          | 해당 요소를 화면에 표시하지 않는다 (공간조차 사라진다)         |

> display 속성은 상속되지 않는다!

## block 요소

---

block 특성을 가지는 요소는 다음과 같은 특징을 가진다.

- 항상 새로운 라인에서 시작한다.
- 화면 크기 전체의 가로폭을 차지한다. (width: 100%)
- width, height, margin, padding 프로퍼티 지정이 가능하다.
- block 레벨 요소 내에 inline 레벨 요소를 포함할 수 있다

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div:nth-of-type(1) {
        background-color: #ffa07a;
        padding: 20px;
      }
      div:nth-of-type(2) {
        background-color: #ff7f50;
        padding: 20px;
        width: 300px;
      }
    </style>
  </head>
  <body>
    <div>
      <h2>블록 레벨 요소</h2>
      <p>width, height 미지정 → width: 100%; height: auto;</p>
    </div>
    <div>
      <h2>블록 레벨 요소</h2>
      <p>width: 300px → width: 300px; height: auto;</p>
    </div>
  </body>
</html>
```

## inline 요소

---

inline 특성을 가지는 요소는 다음과 같은 특징을 가진다.

- 새로운 라인에서 시작하지 않고 문장의 중간에 들어갈 수 있다. 줄을 바꾸지 않고 다른 요소와 한 행에 위치한다.
- content크기 만큼 가로폭을 차지한다.
- width, height, margin-top, margin-bottom 프로퍼티를 지정할 수 없다 상,하 여백은 line-height로 지정한다.
- inline 레벨 요소 뒤에 공백(엔터, 스페이스 등)이 있는 경우, 정의하지 않은 space(4px)가 자동 지정된다.
- inline 레벨 요소 내에 block 레벨 요소를 포함할 수 없다. inline 레벨 요소는 일반적으로 block 레벨 요소에 포함되어 사용된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      span {
        background-color: red;
        color: white;
        padding: 10px;
        line-height: 50px; /*인라인 요소의 상하 여백은 line-height으로 지정한다!*/
      }
    </style>
  </head>
  <body>
    <h1>My <span>Important</span> Heading</h1>
    <span>Inline</span>
    <span>Inline</span><span>Inline</span>
  </body>
</html>
```

## inline-block

---

inline요소 처럼 한 줄에 표시되면서, width height margin 속성을 지정할 수 있다.

- 기본적으로 inline 레벨 요소와 흡사하게 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치시킬 수 있다.
- block 레벨 요소처럼 width, height, margin, padding 프로퍼티를 모두 정의할 수 있다. 상, 하 여백을 margin과 line-height 두가지 프로퍼티 모두를 통해 제어할 수 있다.
- content의 너비만큼 가로폭을 차지한다.
- inline-block 레벨 요소 뒤에 공백(엔터, 스페이스 등)이 있는 경우, 정의하지 않은 space(4px)가 자동 지정된다. 이것을 회피 방법은 Fighting the Space Between Inline Block Elements를 참조하기 바란다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .wrapper {
        font-size: 0; /*inline-block 요소 사이 공백 제거 하기 위해서*/
      }
      .inline-block {
        display: inline-block;
        vertical-align: middle; /*inline-block요소 수직 정렬*/
        border: 3px solid #73ad21;
        font-size: 16px;
      }
      .box1 {
        width: 300px;
        height: 70px;
      }
      .box2 {
        width: 300px;
        height: 150px;
      }
    </style>
  </head>
  <body>
    <div class="inline-block box1">inline-block height 70px</div>
    <div class="inline-block box2">inline-block height 150px</div>

    <div class="wrapper">
      <div class="inline-block box1">inline-block height 70px</div>
      <div class="inline-block box2">inline-block height 150px</div>
    </div>
  </body>
</html>
```

## Visibility 속성

요소의 렌더링 여부를 결정하는 속성

| 값       | 설명                                                                                                                                                     |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| visible  | 보이게한다. (기본값)                                                                                                                                     |
| hidden   | 해당요소를 안보이게한다. **display:none; 은 해당 요소의 공간까지 사라지게 하지만 visibility: hidden;은 해당 요소의 공간은 사라지지 않고 남아있게 된다.** |
| collapse | table요소에 사용하여 행이나 열을 안보이게한다.                                                                                                           |
| none     | table요소의 row나 column을 보이지 않게한다, IE, 파이어폭스에서만 동작하며 크롬에서는 hidden과 동일하게 동작                                              |

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .visible {
        visibility: visible;
      }
      .hidden {
        visibility: hidden;
      }

      table,
      td {
        border: 1px solid black;
      }

      .collapse {
        visibility: collapse;
      }
    </style>
  </head>
 <body>
  <h1 class="visible">visibility: visible</h1>
  <h1 class="hidden">visibility: hidden</h1>
  <h1 style="display:none">display:none</h1>

  <table>
    <tr>
      <td>A</td>
      <td>B</td>
    </tr>
    <tr class="collapse">
      <td>C</td>
      <td>D</td>
    </tr>
  </table>
</html>
```

## opacity 속성

---

opacity 속성은 요소의 투명도를 정의한다. 0.0~ 1.0의 값을 의미하며 0은 투명 1은 불투명이다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div,
      img {
        float: left;
        width: 150px;
        height: 150px;
        margin: 30px;
        background-color: blue;
        color: white;
        opacity: 0.5;
        transition: opacity 1s;
      }
      div:hover,
      img:hover {
        opacity: 1;
      }
    </style>
  </head>
  <body>
    <div>opacity: 0.5</div>
    <img src="https://poiemaweb.com/img/doug.jpg" alt="doug" />
  </body>
</html>
```
