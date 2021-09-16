# this

this는 실행컨텍스트가 생성되는 순간에 bind 됩니다..!!  
실행컨텍스트는 함수가 호출될때 생성된다 따라서 this는 함수가 호출될 때 결정된다.  
따라서 호출하는 방식에 따라서 this는 다른 값을 가지게 된다.

# 전역 공간에서

this는 전역객체를 가르킨다.

# 함수 호출시

this 전역 객체를 가르킨다

```js
function a() {
  console.log(this);
}

a();

function b() {
  function c() {
    console.log(this); // 여기도 전역객체!
  }
  c();
}
b();
```

# 메서드 호출시

메서드 호출주체 (메서드명 앞)이 this가 된다.

```js
const a = {
  b: function () {
    console.log(this);
  },
};
a.b(); // a가 나온다
```

## 메서드의 내부함수에서 this 바인딩 문제를 해결하는 방법

```js
const obj = {
  a: 20,
  b: function () {
    console.log(this.a);
    const that = this;

    function c() {
      console.log(that.a); // 스코프 체인을 이용해서 this를 찾아 쓰는 방법
    }
    c(); // 여기서 this가 전역에 바인딩 되는 것을 회피할 수 있다.
  },
};

obj.b();
```

## 참고 arrow function

arrow function은 this를 바인딩 하지 않기 때문에 스코프 체인에 의해서 상위 컨텍스트의 this를 참조하게 된다.

```js
const obj = {
  a: 20,
  b: function () {
    console.log(this.a);

    const c = () => {
      console.log(this.a);
    };
    c();
  },
};

obj.b();
```

# callback 호출시

기본적으로는 함수와 동일하다.  
아무런 처리도 하지 않고 콜백함수를 호출하면 this는 전역에 바인딩 된다.  
하지만 콜백함수를 호출할때 call, apply, bind를 이용해 this를 명시적으로 선언하고 호출하면 this가 다른 값에 바인딩 되어 호출된다.

결론: 콜백함수가 결정할 수 있는 부분이 아니라 콜백을 호출하는 함수에서 결정할 수 있다.  
콜백을 호출하는 함수에서 this를 바인딩하고 있을경우에도 콜백을 넣어줄때 bind를 이용해 this를 걸어 줄 수 있다.

## call, apply, bind 명시적으로 this를 바인딩 하는 방법

```js
function a(x, y, z) {
  console.log(this, x, y, z);
}

const obj = {
  a: 1,
};

a.call(obj, 1, 2, 3); // this가 obj에 바인딩 되고 나머지 인수는 매개변수의 인자이다. 실행됨
a.apply(obj, [1, 2, 3]); //this가 obj에 바인딩 되고 배열은 매개변수의 인자이다. 실행도미

const c = a.bind(obj); // this가 obj에 바인딩된 새로운 함수를 만들어 반환한다
c(1, 2, 3);

const d = a.bind(obj, 1, 2); // 매개변수에 미리 값을 넣어 둘 수 도 있다.
d(3);
```

# 생성자함수 호출시

새로 생성되는 객체가 bind된다

```js
function Person(n, a) {
  this.name = n;
  this.age = a;
  // 새로 생성된 빈 객체에 this를 바인드해서 처리한다.
}
```
