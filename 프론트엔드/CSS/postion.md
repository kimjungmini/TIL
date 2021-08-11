# position

position 속성은 요소를 배치할 때 사용하면 좋은 속성이다.  
top, bottom, left, right 속성과 함께 사용하여 위치를 지정한다.

---

## static (기본 위치)

---

static은 position의 기본 값이다.  
기본적으로 위에서 아래로 왼쪽에서 오른쪽으로 배치되며 **부묘 요소 내부의 자식요소로서 존재할 경우**에는 부모 요소의 위치를 기준으로 배치 된다.

기본적으로 이 값을 사용할 일은 별로 없지만, 이미 설정된 position을 무력화 하기 위해서 사용한다. 좌표 속성(top ,bottom, left, right)사용 불가능하며 사용하더라도 무시 된다.

static을 지정하는것이 의미가 있는 경우는 거의 없으므로 일단 예제 코드는 생략

## relative (상대 위치)

---

기본위치(static)이 지정되었을 때를 기준으로 좌표 속성을 이용하여 위치를 이동 시킨다. static과의 차이는 좌표 속성의 동작 여부이며 그 이외에는 동일하게 동작한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        margin: 0;
      }
      .parent {
        width: 150px;
        height: 150px;
        background: #bcbcbc;
        border: 1px solid #bcbcbc;
        margin: 50px;
      }
      .relative-box {
        position: relative;
        top: 50px;
        left: 50px;
        background: #2e303d;
        color: #e55c3c;
        font-weight: bold;
        text-align: center;
        line-height: 150px;
      }
    </style>
  </head>
  <body>
    <div class="parent">
      <div class="relative-box">relative box</div>
    </div>
  </body>
</html>
```

## absolute (절대 위치)

---

부모요소 또는 가장 가까이 있는 조상요소(static 제외)를 기준으로 좌표 프로퍼티 만큼 이동한다.즉 relative absolute fixed 프로퍼티가 선언되어 있는 조상 요소를 기준으로 위치가 결정된다.

만일 부모 또는 조상요소가 static인 경우 document body를 기준으로하여 좌표 프로퍼티대로 위치하게 된다.

따라서 부모요소를 기준으로 삼기 위해서는 부모요소에 relative를 지정해 주는 것이 좋다.

이때 다른 요소가 위치를 점유하고 있어도 뒤로 밀리지않고 덮어쓰게 된다.

absolute 선언 시, block 레벨 요소의 width는 inline 요소와 같이 content에 맞게 변화하므로 적절한 width를 설저아혀야 한다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      body {
        margin: 0;
      }
      .parent {
        width: 200px;
        height: 200px;
        background: #bcbcbc;
        border: 1px solid #bcbcbc;
        margin: 50px 0 0 300px;
        position: relative;
      }
      .absolute-box {
        position: absolute;
        height: 200px;
        width: 200px;
        top: 50px;
        left: 50px;
        color: #e55c3c;
        font-weight: bold;
        text-align: center;
        background: #2e303d;
        line-height: 200px;
      }
    </style>
  </head>
  <body>
    <div class="parent">
      <div class="absolute-box">absolute box (in parent)</div>
    </div>
    <div class="absolute-box">absolute box (no parent)</div>
  </body>
</html>
```

**relative VS absolute**

---

relative 속성은 기본 위치를 기준으로 좌표 속성을 사용하여 위치를 이동시킨다. 따라서 무조건 부모를 기준으로 위치하게 된다.

absolute 속성은 부모에 static 이외에 프로퍼티가 지정되어 있을 경우에만 부모를 기준으로 위치하게 된다.

absolute 요소는 부모 요소의 영역을 벗어나 자유롭게 배치가 가능하다.

## fixed 고정위치

---

부모 요소와 상관없이 브라우저의 viewport를 기준으로 좌표속성을 사용하여 위치를 이동시킨다.

스크롤이 되더라도 화면에서 사라지지 않고 같은 위치에 존재한다.

fixed 속성 선언시 block 요소의 width 는 inline 요소처럼 content 에 맞게 변화하므로 width 지정이 필요하다.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    body { margin: 0; }
    .fixed-box {
      position: fixed;
      color: #e55c3c;
      font-weight: bold;
      text-align: center;
      background: #2E303D;
    }
    .sidebar {
      width: 50px;
      height: 100%;
      top: 0;
      right: 0;
      padding-top: 100px;
    }
    .footer {
      width: 200px;
      width: 100%;
      height: 50px;
      bottom: 0;
      left: 0;
      line-height: 50px;
    }
  </style>
</head>
<body>
  <div class="fixed-box sidebar">fixed box (side-bar)</div>
  <div class="fixed-box footer">fixed box (footer)</div>
</body>
</html>
```

## z-index 속성

z-index 속성에 큰 숫자값을 지정할수록 화면 전면에 출력된다. position이 static이 아닌 요소에만 적용된다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      .normal-box {
        width: 100px;
        height: 100px;
      }
      .absolute-box {
        width: 100px;
        height: 100px;
        position: absolute;
      }
      /* z-index는 positon 프로퍼티가 static 이외인 요소에만 적용된다. */
      .orange {
        background-color: orange;
        z-index: 1000;
      }
      .red {
        background-color: red;
        left: 50px;
        top: 50px;
        z-index: 100;
      }
      .green {
        background-color: green;
        left: 100px;
        top: 100px;
        z-index: 10;
      }
      .blue {
        background-color: blue;
        left: 150px;
        top: 150px;
        z-index: 1;
      }
    </style>
  </head>
  <body>
    <div class="normal-box orange"></div>
    <div class="absolute-box red"></div>
    <div class="absolute-box green"></div>
    <div class="absolute-box blue"></div>
  </body>
</html>
```

## overflow 속성

overflow 속성은 자식 요소가 부모 요소의 영역을 벗어났을 때 처리하는 방법

| 값      | 설명                                       |
| ------- | ------------------------------------------ |
| visible | 영역 벗어난 부분 표시                      |
| hidden  | 영역 벗어난 부분 잘라내어 보이지 않게 함   |
| scroll  | 영역을 벗어난 부분이 없어도 스크롤 표시    |
| auto    | 영역을 벗어난 부분이 있을때만 스크롤 표시. |

특정 방향으로만 하고 싶을때는 overflow-x overflow-y를 이용한다.
