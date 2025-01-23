# 스코프(scope) & 호이스팅(Hoisting)

# 스코프란?

스코프는 유효 범위라고도 부르며 변수가 어느 범위까지 참조되는 지를 뜻한다.

```jsx
const a = 10; // 전역 스코프(Global Scope)

{
  const b = 20; // 지역 스코프(Local Scope)

  console.log(a, b); // 10 20
}

console.log(a, b); // Error
```

만약 var를 사용하면 개발자가 예상치 못한 오류가 생길 수 있다.

```jsx
var a = 10;

{
  // 호이스팅 되어 변수 선언이 상단으로 올라가버립니다.
  var a = 20;

  console.log(a); // 10
}

console.log(a); // 10
```

> 이렇게 차이가 발생하는 이유는 var는 함수 수준의 스코프이고, let, const는 블록 수준의 스코프이기 때문

> var 사용 시 이러한 예상치 못한 오류가 생길 수 있으므로 가급적 var를 사용하지 않고 let과 const를 사용하는 것이 좋다.

<br/>

# 호이스팅이란?

호이스팅이란 변수 선언과 초기화가 동시에 이루어졌을 때, 자바스크립트 인터프리터가 변수의 선언을 함수의 맨 위로 이동시키는 동작을 뜻한다.

- 호이스팅 전

```jsx
function sayHi() {
  console.log(text); // undefinded

  var text = "hi";
}
```

- 호이스팅 후

```jsx
function sayHi() {
  var text;

  console.log(text); // undefinded

  text = "hi";
}
```

var, let, const 모두 호이스팅이 된다. 하지만 let, const는 선언만 될 뿐, 초기화가 이뤄지지 않는다. 바로 이 단계에서 TDZ(Temporary Dead Zone)에 들어가게 되는 것이다. 즉, 선언은 되어 있지만, 초기화가 되지 않아 이를 위한 자리가 메모리에 준비되어 있지 않은 상태라는 것이다.
