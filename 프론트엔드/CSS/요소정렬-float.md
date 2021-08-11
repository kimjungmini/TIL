https://poiemaweb.com/css3-float 를 공부하고 정리한 문서

# float 속성

float 속성은 주로 레이아웃을 구성할 때 블록 레벨 요소를 가로 정렬하기 위해서 사용되는 중요한 기법이다. flexbox레이아웃을 사용하면 더욱 간단하게 정렬이 가능하지만 IE를 고려 해야 한다면 float 속성을 사용해야 한다.

float 속성은 본디 이미지와 택스트가 있을 때 텍스트로 이미지를 감싸기 위하여 만들어진 것이다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      img {
        float: left;
        margin-right: 10px;
      }
    </style>
  </head>
  <body>
    <img src="https://poiemaweb.com/img/doug.jpg" />
    <div>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
      tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
      veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
      commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
      velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
      cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
      est laborum.Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed
      do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad
      minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex
      ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
      velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat
      cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id
      est laborum.
    </div>
  </body>
</html>
```

float 속성은 해당 요소를 다음 요소 위에 떠있게 한다. 여기서 뜬다는 의미는 요소가 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지 왼쪽이나 오른쪽으로 이동하는 것을 말한다. float을 사용할때 postion:absolute를 사용하면 안된다.

| 값    | 설명                           |
| ----- | ------------------------------ |
| none  | 요소를 떠있게 하지 않는다      |
| left  | 요소를 왼쪽으로 이동 시킨다.   |
| right | 요소를 오른쪽으로 이동 시킨다. |

![](https://poiemaweb.com/img/float.png)

# 정렬

float 속성을 사용하지 않은 블록 요소들은 수직으로 정렬된다. float을 사용하면 가로 정렬이 된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .box {
        color: white;
        font-weight: bold;
        font-size: 50px;
        border-radius: 6px;
        width: 100px;
        height: 100px;
        margin: 10px;
        padding: 10px;
      }
      .d1,
      .d2 {
        float: left;
      }
      .d1 {
        background: red;
      }
      .d2 {
        background: orange;
      }
      .d3,
      .d4 {
        float: right;
      }
      .d3 {
        background: red;
      }
      .d4 {
        background: orange;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="box d1">1</div>
      <div class="box d2">2</div>
      <div class="box d3">3</div>
      <div class="box d4">4</div>
    </div>
  </body>
</html>
```

float은 좌측, 우측 정렬만 가능하다. 가운데 정렬을 하고 싶으면 float이 아니라 margin 속성을 이용해야 한다.

```css
div {
  width: 960px;
  margin: 0 auto;
}
```

# float 과 width

width 속성을 선언하지 않은 block 레벨 요소에 float 프로퍼티가 선언 되면 width가 inline 요소처럼 content에 맞게 최소화 된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .box {
        color: white;
        font-weight: bold;
        font-size: 30px;
        line-height: 50px;
        height: 50px;
        margin: 0 10px;
        padding: 10px;
      }
      .d1 {
        float: left;
        background: red;
      }
      .d2 {
        background: orange;
      }
    </style>
  </head>
  <body>
    <div class="box d1">float: left;</div>
    <div class="box d2">div</div>
  </body>
</html>
```

이때 d2의 width 는 100%이다. d2의 width가 100%이기 때문에 div라는 글자가 보이지 않을 거라고 생각 했는데 content는 겹치지 않고 밀리는 것 같다.

# float 문제 해결

## float 이 선언된 요소와 float이 선언되지 않은 요소간 margin이 사라지는 문제

위 코드를 브라우저에서 실행해 보면 margin이 제대로 표현되고 있지 않다. 왜냐하면 d2요소가
width가 100%가 되어 있고 d1요소가 d2요소 위에 떠있기 때문에 생기는 박스 모델 상의 문제이다. 이를 해결하기 위한 가장 쉬운 방법은 overflow:hidden을 지정해 주는 것이다.
그러면 d2요소가 넘쳐서 d1요소 밑에 깔린 부분이 안보이게 되어 정상적으로 마진이 표현된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .box {
        color: white;
        font-weight: bold;
        font-size: 30px;
        line-height: 50px;
        height: 50px;
        margin: 0 10px;
        padding: 10px;
      }
      .d1 {
        float: left;
        background: red;
      }
      .d2 {
        background: orange;
        overflow: hidden;
      }
    </style>
  </head>
  <body>
    <div class="box d1">float: left;</div>
    <div class="box d2">div</div>
  </body>
</html>
```

## float 속성이 선언된 자식 요소를 포함하는 부모 요소의 높이가 정상적이지 않은 문제

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .container {
        color: white;
        text-align: center;
        padding: 10px;
        background-color: #def0c2;
      }
      .d1,
      .d2 {
        float: left;
        width: 50%;
        padding: 20px 0;
      }
      .d1 {
        background-color: #59b1f6;
      }
      .d2 {
        background-color: #ffb5b4;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="d1">1</div>
      <div class="d2">2</div>
    </div>
    <div style="background:red;padding:10px;color:white;">3</div>
  </body>
</html>
```

float이 선언된 요소는 일반적인 흐름상에 존재하지 않기 때문에 float 요소의 높이를 알 수 가 없다. 이는 부모요소가 float된 자식의 높이는 고려하지 않기 때문에 생긴다.

이 문제를 해결하는 가장 쉬운 방법은 float이 선언된 요소의 부모요소에 overflow: hidden을 선언하는 것이다.

overflow: hidden; 을 부모요소에 주게 되면 같은 float된 자식요소가 같은 block formatting context를 가지게 되어 float된 요소의 height을 같이 계산하게 된다고 한다. 이를 명확하게 이해하기 위해서는 block formatting context에 대해서 잘 이해해봐야 할 거 같다.

정리하자면, float된 자식요소는 부모요소의 높이를 계산하는데 반영되지 않는다! 그러나 부모요소에 overflow:hidden을 주게 되면 float된 자식요소까지 높이를 계산하는데 반영이 된다

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .container {
        color: white;
        text-align: center;
        padding: 10px;
        background-color: #def0c2;
        overflow: hidden;
      }
      .d1,
      .d2 {
        float: left;
        width: 50%;
        padding: 20px 0;
      }
      .d1 {
        background-color: #59b1f6;
      }
      .d2 {
        background-color: #ffb5b4;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="d1">1</div>
      <div class="d2">2</div>
    </div>
    <div style="background:red;padding:10px;color:white;">3</div>
  </body>
</html>
```

또다른 방법으로는 clear 속성을 이용하여 float된 부분을 끝내주는 방법이 있다.
이때 의미없는 div요소를 사용하면 웹 접근성을 깨트리므로 ::after를 이용하여 깨트리는 방법을 적어두겠다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .container {
        color: white;
        text-align: center;
        padding: 10px;
        background-color: #def0c2;
      }
      .clearfix::after {
        content: "";
        display: block;
        clear: both;
      }
      .d1,
      .d2 {
        float: left;
        width: 50%;
        padding: 20px 0;
      }
      .d1 {
        background-color: #59b1f6;
      }
      .d2 {
        background-color: #ffb5b4;
      }
    </style>
  </head>
  <body>
    <div class="container clearfix">
      <div class="d1">1</div>
      <div class="d2">2</div>
    </div>
    <div style="background:red;padding:10px;color:white;">3</div>
  </body>
</html>
```

또 다른 방법으로 요소를 가로 정렬하는 방법으로는 inline-block 을 사용하는 건데 불필요한 공백이 들어가서 font-size를 0으로 바꾸어 주었다가 font-size를 계속 재 조정해주어야 하기 때문에 좋은 방법은 아니기 때문에 따로 정리 하지는 않겠다. 나중에 필요하면 추후 정리할 것.

개인적인 생각으로는 요즘 flex-box grid시스템등 레이아웃을 위한 좋은 프로퍼티들이 있기 때문에 이정도로만 정리하고 레이아웃을 잡기 위해 float을 쓰는 것은 이제 좋은 생각은 아닌거 같다.
