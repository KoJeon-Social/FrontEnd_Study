# JavaScript 식별자

<br />

## 식별자의 정의와 규칙

**식별자**는 코드 내의 변수, 함수, 혹은 속성을 식별하는 문자다.

**JavaScript의 식별자**는 대소문자를 구별하며 `유니코드 글자`, `$`, `_`, `숫자(0-9)`로 구성할 수 있지만 숫자로 시작할 수 없고 공백을 포함할 수 없다.

식별자는 코드의 일부이지만 문자열은 데이터이기 때문에 식별자와 문자열은 다르다. JavaScript에서 식별자를 문자열로 변환하는 방법은 없지만 문자열을 분석해 식별자로 사용할 수 있다.

```jsx
// age : 식별자
// 10 : 데이터
let age = 10;
```

```jsx
// person, name : 식별자
// 'Ko Eunjin': 데이터

const student = {
  name: "Ko Eunjin",

  // 아래와 같은 경우는 데이터가 코드화, 식별자화가 될 수 있는 예시입니다.
  // 그렇기에 식별자 규칙을 따르지 않아 숫자로 시작하거나 공백을 포함할 수 있습니다.
  ["studentAge"]: 28,
  ["1-Math score"]: 90,
  ["2-Eng score"]: 100,
};

// 아래와 같은 방법으로 student 객체 속성에 접근할 수 있습니다.
console.log(student.studentAge);
console.log(student["1-Math score"]);
console.log(student["2-Eng score"]);
```

<br />

## 관습적인 컨벤션

**상수**는 대문자로 작성한다.

이름이 긴 경우 단어와 단어를 구분하기 위해 **카멜 케이스(Camel case)** 또는 **스네이크 케이스(Snake case)** 와 같은 방법을 사용한다.

- 카멜 케이스(Camel case)
  ```jsx
  function setName(name) {}
  function getName() {}
  ```
- 스네이크 케이스(Snake case)
  ```jsx
  function set_name(name) {}
  function get_name() {}
  ```
