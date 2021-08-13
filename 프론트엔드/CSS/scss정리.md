# 변수

Sass 는 css에 변수 개념을 도입해 준다.

변수로 사용 가능한 형태는 숫자 문자열 폰트 색상 null lists 와 maps가 존재한다. 변수를 마들 때는 $ 문자를 사용한다

```scss
$primary-color: #333;

body {
  background-color: $primary-color;
}
```

## 변수 범위

scss의 변수엔 변수 범위가 존재한다. 변수를 특정 선택자 에서 선언하면 해당 선택자에서만 접근 가능하다.

```scss
$primary-color: #333;

body {
  $primary-color: #eee;
  background-color: $primary-color; //#eee
}

p {
  color: $primary-color; // #333
}
```

변수를 선언 할 때 변수를 전역으로 설정 할 때는 !global 플래그를 사용한다

```scss
$primary-color: #333;

body {
  $primary-color: #eee !global;
  background-color: $primary-color; //#eee
}

p {
  color: $primary-color; // #eee
}
```

!default 플래그는 해당 변수가 설정되지 않았거나 값이 null 일 때 값을 설정한다.

```scss
$primary-color: #333;

$primary-color: #eee !default;

p {
  color: $primary-color;
}
```

# 수학 연산자

- - / \* $ == != 연산자 사용가능

주의: + - 연산자를 사용할 때는 단위를 일치시켜 주어야 한다!

단위가 일치되지 않은 값 끼리 연산을 하려면 calc 함수를 사용해야 한다.

```scss
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}
```

# 내장함수

scss 에는 개발에 도움이 되는 내장함수가 많으니 개발하다가 어떤 기능이 필요하다고 생각되면 내장함수가 있는지 찾아보도록 하자

# 중첩

scss의 가장 큰 장점중 하나는 선언의 중첩이 가능하다는 것이다.

```css
.container {
  width: 100%;
}

.container h1 {
  color: red;
}
```

위와 같은 css 코드는 scss로 다음과 같이 작성 가능하다.

```scss
.container {
  width: 100%;

  h1 {
    color: red;
  }
}
```

부모 선택자를 참조할 때는 & 기호를 사용한다

```scss
a {
  color: black;
  &:hover {
    text-decoration: underline;
    color: gray;
  }

  &:visited {
    color: purple;
  }
}
```

# Import 불러오기

스타일을 여러 파일로 나누고 다른 파일에서 불러 와 사용 하는 기능

```scss
@import "layout.scss";
```

# Extend(상속)

scss에서 특정 선택자를 상속 할때 사용 가능

```scss
.box {
  border: 1px solid gray;
  padding: 10px;
  display: inline-block;
}

.success-box {
  @extend .box;
  border: 1px solid green;
}
```

```css
.box,
.success-box {
  border: 1px solid gray;
  padding: 10px;
  display: inline-block;
}

.success-box {
  border: 1px solid green;
}
```

Placeholder

상속을 위해서만 scss에 적어놓고 컴파일 되지 않는 선택자

```scss
%box {
  // 나중에 컴파일 X 추상 클래스 같은 존재
  padding: 0.5em;
}
```

# Mixin(믹스인)

인자를 주어서 코드를 재활용 할 수 있게 도와주는 함수 같은 기능 매우 유용하다!

```scss
@mixin headline($color, $size) {
  color: $color;
  font-size: $size;
}

h1 {
  @include headline(green, 12px);
}
```

# Function 함수

임의 함수 값을 직접적으로 반환 해줌

```scss
@function calc-percent($target, $container) {
  @return ($target / $container) * 100%;
}
```
