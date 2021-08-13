# flex-box

Flexbox는 모던 웹을 위하여 제안된 기존 layout보다 더 세련된 방식의 니즈에 부합하기 위핸 CSS의 layout 방식이다.

요소의 사이즈가 불명확하거나 동적으로 변화할 때도 유연한 레이아웃을 실현할 수 있다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Flexbox Layout Example</title>
    <style>
      .flex-container {
        margin: 10px;
        padding: 15px;
        border-radius: 5px;
        background: #60b99a;
      }

      .flex-item {
        margin: 10px;
        padding: 20px;
        color: #fff;
        text-align: center;
        border-radius: 5px;
        background: #4584b1;
      }
    </style>
  </head>
  <body>
    <div class="flex-container">
      <div class="flex-item">1</div>
      <div class="flex-item">2</div>
      <div class="flex-item">3</div>
      <div class="flex-item">4</div>
      <div class="flex-item">5</div>
    </div>
  </body>
</html>
```

위 코드의 flex-item 요소들은 block 레벨 요소이기 때문에 당연히 세로로 쌓이게 된다

이 요소들을 수평 정렬 하기 위해서 부모요소에 display: flex를 추가해준다.

```css
.flex-container {
  display: flex;
}
```

css 코드 한줄로 요소를 수평 정렬하는데 성공 했다.

flex box의 장점은 다음과 같다.

- 1줄의 코드로 수평 정렬이 가능하다.
- 요소의 상하좌우 정렬, 순서 변경이 간단한다.
- 요소의 간격 조절이 간단하다.
- 서로 다른 height을 가지는 요소의 수평정렬시 간단히 상하중앙 정렬이 가능하다.

## 부모요소가 inline일 경우

부묘요소가 inline요소일 경우 inline-flex를 지정해 주면 된다.

```css
.flex-container {
  display: inline-flex;
}
```

# flex container 속성

## flex-direction

flex-direction 속성은 flex 컨테이너의 주축 방향을 결정한다.

```css
.flex-container {
  flex-direction: row; /*좌에서 우로 수평 정렬*/
}
```

```css
.flex-container {
  flex-direction: row-reverse; /*우에서 좌로 수평 정렬*/
}
```

```css
.flex-container {
  flex-direction: column; /*위에서 아래로 수평 정렬*/
}
```

```css
.flex-container {
  flex-direction: column-reverse; /*아래에서 위로 수평 정렬*/
}
```

## flex-wrap

flex-wrap 속성은 flex 컨테이너의 복수 flex-item을 1행으로 또는 복수행으로 배치할 지를 결정하는 속성이다. flex 컨테이너의 width보다 item의 width의 합이 더 클경우 개행을해서 배치를 할지 width를 줄여서 1줄에 배치할 지를 결정하는 속성이다.

```css
.flex-container {
  flex-wrap: nowrap; /*개행하지 않고 1행에 배치 flex-item의 width가 줄어든다*/
}
```

```css
.flex-container {
  flex-wrap: wrap; /*개행하여 배치한다 */
}
```

```css
.flex-container {
  flex-wrap: wrap-reverse; /*넘칠경우 아래에서 위로 배치한다. */
}
```

## justify-content

main축을 기준으로 flex-item을 정렬해주는 속성이다

```css
.flex-container {
  justify-content: start; /*좌에서 우측 정렬*/
}
```

```css
.flex-container {
  justify-content: end; /*우측 정렬*/
}
```

```css
.flex-container {
  justify-content: center; /*가운데 정렬*/
}
```

```css
.flex-container {
  justify-content: space-between; /*처음과 끝이 양끝에 배치되고 나머지와 균등한 간격 배치*/
}
```

```css
.flex-container {
  justify-content: space-around; /*모두 균등한 간격으로 배치*/
}
```

## align-items (한줄 짜리 box에서만 사용!)

메인 축에 수직인 방향으로 정렬하는 속성

```css
.flex-container {
  align-items: stretch; /*모든 item에 flexbox의 height과 일치하게 된다.*/
}
```

```css
.flex-container {
  align-items: flex-start; /*모든 item에 flexbox의 시작점 기준으로 정렬*/
}
```

```css
.flex-container {
  align-items: flex-end; /*모든 item에 flexbox의 끝점 기준으로 정렬*/
}
```

```css
.flex-container {
  align-items: center; /*모든 item이 중앙 정렬*/
}
```

```css
.flex-container {
  align-items: baseline; /*모든 item이 baseline에 맞춰서 정렬*/
}
```

## align-content(여러줄 짜리 박스에서만 사용!)

```css
.flex-container {
  align-content: stretch; /*균등하게 배치*/
}
```

```css
.flex-container {
  align-content: flex-start; /*위쪽으로 붙어서 배치*/
}
```

```css
.flex-container {
  align-content: flex-end; /*끝쪽으로 붙어서 배치*/
}
```

```css
.flex-container {
  align-content: center; /*중앙에 배치*/
}
```

```css
.flex-container {
  align-content: space-between; /*시작 끝 빼고 균등하게 배치*/
}
```

```css
.flex-container {
  align-content: space-around; /*균등하게 배치*/
}
```

# flexbox item 속성

```css
.flex-item {
  order: 정수 값; /*html 코드 조작 없이 배치를 바꿀 수 있음*/
}
```

```css
.flex-item {
  flex-grow: 양의 정수 값; /*flex item이 늘어날때 차지하는 위치 비율 클수록 더 커짐*/
}
```

```css
.flex-item {
  flex-shrink: 양의 정수값; /*flex item이 줄어들때 차지하는 위치 비율 클수록 더 커짐
    0을 지정하면 축소가 해제되어 원래 크기로 돌아온다.
  */
}
```

```css
.flex-item {
  flex-basis: 크기 단위; /*item의 기본 크기를 지정한다.*/
}
```
