# 스코프(Scope) & 호이스팅(Hoisting)

<br />

## 스코프

**스코프(Scope)**는 유효 범위라고도 부르며 변수가 어느 범위까지 참조되는지를 뜻한다.

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
  // 호이스팅 되어 변수 선언이 상단으로 올라간다.
  var a = 20;

  console.log(a); // 20
}

console.log(a); // 20
```

- var는 함수 수준의 스코프를 가지므로 코드 블록 내부와 외부에서 동일한 변수 a가 영향을 받는다.

```jsx
let a = 10;

{
  let a = 20;
  console.log(a); // 20
}

console.log(a); // 10
```

- let, const는 블록 수준의 스코프를 가지므로 블록 내부의 let a가 별도의 스코프를 가지게 되어 전역 변수 a에 영향을 주지 않는다.

var 사용 시 이러한 예상치 못한 오류가 발생할 수 있으므로 가급적 var를 사용하지 않고 let, const를 사용하는 것이 좋다.

<br />

## 호이스팅

**호이스팅(Hoisting)**이란 변수 선언과 초기화가 동시에 이루어졌을 때 자바스크립트 인터프리터가 변수의 선언을 함수의 맨 위로 이동시키는 동작을 뜻한다.

- 호이스팅 전

  ```jsx
  function sayHi() {
    console.log(text); // undefined

    var text = "hi";
  }
  ```

- 호이스팅 후

  ```jsx
  function sayHi() {
    var text;

    console.log(text); // undefined

    text = "hi";
  }
  ```

- const, let으로 선언한 변수 호이스팅
  ```jsx
  console.log(name); // ReferenceError
  const name = "James";
  ```
  ```jsx
  console.log(name); // ReferenceError
  let name = "James";
  ```

<mark>var, let, const는 모두 호이스팅이 된다. 하지만 let과 const는 선언만 될 뿐 초기화가 이루어지지는 않는다.</mark>

> var 키워드는 선언과 함께 undefined로 초기화되어 메모리에 저장되는 반면 **let과 const는 초기화되지 않은 상태로 선언만 메모리에 저장(=TDZ, Temporary Dead Zone)**된다.

let과 const 사용 시 호이스팅은 되지만 접근은 불가능하다. 따라서 name의 선언문이 나오기 전까지는 name에 접근할 수 없다.
