# 클로저(Closure)

<br />

## 클로저란?

**클로저(Closure)** 는 함수가 선언된 환경의 스코프를 기억하여 함수가 스코프 밖에서 실행될 때에도 기억한 스코프에 접근할 수 있게 만드는 문법이다.

- 클로저란, <mark>**자신이 선언된 당시의 환경을 기억**</mark>하는 함수.
- 클로저란, <mark>**생명 주기가 끝난 외부 함수의 변수에 접근**</mark>할 수 있는 내부 함수.

```jsx
function makeGreeting(name) {
  // 외부 함수의 변수
  const greeting = "Hello, ";

  // 익명함수는 클로저(내부 함수에서 외부 함수의 변수에 접근 가능)
  return function () {
    console.log(greeting + name);
  };
}

const world = makeGreeting("World!");
const eunjin = makeGreeting("Eunjin");

world(); // Hello, World!
eunjin(); // Hello, Eunjin
```

- **makeGreeting(’World!’) 호출:**
  - makeGreeting 함수가 호출되면서 name에는 ‘World!’, 그리고 greeting에는 ‘Hello, ‘가 할당된다.
  - 이 함수는 내부의 익명 함수를 반환하며 반환된 함수는 greeting과 name 변수에 대한 접근권을 가진 클로저가 된다.
  - world 변수는 이 클로저를 참조한다.
- **makeGreeting(’Eunjin’) 호출:**
  - 같은 방식으로 호출되지만 이번에는 name에 ‘Eunjin’이 할당된다.
  - 반환된 함수는 greeting과 ‘Eunjin’에 대한 접근권을 가진 또 다른 클로저이다.
  - 이제 eunjin 변수는 이 두 번째 클로저를 참조한다.
- **world() 실행:**
  - world는 ‘World!’를 기억하는 클로저이다.
  - 실행 시 greeting + name은 ‘Hello, World!’로 출력된다.
- **eunjin() 실행:**
  - eunjin은 ‘Eunjin’을 기억하는 클로저이다.
  - 실행 시 greeting + name은 ‘Hello, Eunjin’으로 출력된다.

<mark>쉽게 말하면, 외부 함수 makeGreeting은 내부 함수인 익명 함수를 반환하고 생을 마감했다. 즉 실행 후 **콜스택에서 제거**가 되었기 때문에 **생명 주기가 끝난 상태**다.</mark>

<mark>하지만 내부 함수를 호출하여 실행되면 내부 함수는 **선언된 당시의 환경을 기억**하고 있으므로 greeting과 name을 출력한다.</mark>

> **클로저의 특징**
>
> 1.  **스코프 기억**: 반환된 내부 함수는 자신이 생성된 시점의 외부 변수(greeting과 name)를 기억한다.
>
> 2.  **독립된 클로저**: makeGreeting 함수가 호출될 때마다 새로운 스코프가 생성되고, 반환된 내부 함수는 각각 독립된 클로저로 작동한다. 예: world와 eunjin은 서로 다른 스코프를 기억한다.
>
> 3.  **생명 주기**: makeGreeting 함수는 호출 후 종료되었지만 반환된 클로저가 여전히 외부 변수에 접근 가능하므로 외부 변수의 생명 주기가 연장된다.

<br />

## 은닉화

클로저를 유용하게 사용할 수 있는 방법 중 하나는 **은닉화**다. 클로저를 이용하여 내부 변수와 함수를 숨길 수 있다.

```jsx
function Counter() {
  let privateCounter = 0;

  function changeBy(value) {
    privateCounter += value;
  }

  return {
    increment: function () {
      changeBy(1);
    },
    decrement: function () {
      changeBy(-1);
    },
    getValue: function () {
      return privateCounter;
    },
  };
}

const counter = Counter();

console.log(counter.getValue()); // 0

counter.increment();
counter.increment();

console.log(counter.getValue()); // 2

counter.decrement();

console.log(counter.getValue()); // 1
```

위의 코드에서 privateCounter는 Counter 함수 내부에서 let으로 선언된 지역 변수로 **외부에서 직접 접근할 수 없다.**

또한 changeBy 함수 역시 **외부에서 직접 호출할 수 없으며** increment와 decrement 메서드가 내부적으로 changeBy를 호출한다.

반환된 객체(counter)는 increment, decrement, getValue **메서드만 노출**한다.

<mark>은닉화는 객체의 내부 상태(데이터)를 외부에서 직접 접근하지 못하도록 숨기고, 이를 제어하기 위해 제공된 메서드(함수)를 통해서만 접근할 수 있도록 하는 것이 원칙이다.</mark>

<br />

## 클로저를 잘 알아야 하는 이유

알기 힘든 버그를 수정하기 위해 사용해야 한다.

```jsx
function counting() {
  let i = 0;

  for (i = 0; i < 5; i += 1) {
    setTimeout(() => {
      console.log(i);
    }, i * 100);
  }
}

counting(); // 5 5 5 5 5
```

위의 코드에서 `i`는 `let`이 아닌 `var`처럼 함수 스코프를 가지므로 루프의 모든 반복에서 동일한 `i` 변수를 참조한다.

루프가 끝난 뒤 i는 최종 값 5가 되고, 모든 `setTimeout`에서 동일한 `i` 값을 참조하여 5만 출력된다. (`setTimeout`은 비동기로 실행되므로 루프가 끝날 때까지 대기하고, 루프 종료 후에 콜백 함수가 실행된다. 따라서 콜백이 실행될 때는 이미 `i`가 최종 값 5로 업데이트 된 상태다.)

만약 0 1 2 3 4와 같이 출력되기를 원한다면 아래와 같은 해결법이 있다.

- **루프에 let과 const 같은 블록 수준 스코프 사용**
  ```jsx
  function counting() {
    // let은 블록 수준 스코프기 때문에 매 루프마다 클로저가 생성된다.
    for (let i = 0; i < 5; i += 1) {
      setTimeout(() => {
        console.log(i);
      }, i * 100);
    }
  }

  counting(); // 0 1 2 3 4
  ```
  `for` 루프에서 `let i`를 사용하면 루프의 각 반복마다 별도의 스코프가 생성된다. 즉 `setTimeout`에서 사용하는 `i`는 각각의 루프 반복마다 고유한 값이 할당된다.
  또한 `let` 사용 시 각 루프 반복마다 고유한 클로저가 생성되므로 콜백 함수는 해당 스코프의 `i` 값을 정확히 참조할 수 있다.
- **즉시 실행 함수(Immediately-invoked function expression) 사용**
  ```jsx
  function counting() {
    let i = 0;

    for (i = 0; i < 5; i += 1) {
      (function (number) {
        setTimeout(() => {
          console.log(number);
        }, i * 100);
      })(i);
    }
  }

  counting(); // 0 1 2 3 4
  ```
  `(function (number) { ... })(i);`는 즉시 실행 함수(IIFE)로, 매 루프마다 새로운 스코프를 생성한다.
  `number` 매개변수는 현재 반복의 i 값을 복사하여 고유하게 유지된다.
  즉시 실행 함수 내부에서 `setTimeout`이 실행되고, 이 함수는 자신의 스코프와 함께 클로저를 형성한다. 따라서 콜백 함수는 각각 고유한 `number` 값을 참조하게 된다.
