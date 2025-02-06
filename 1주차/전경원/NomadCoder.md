# 데이터 타입의 종류

## Number

- 정수(integer) : 1, 2, 3, 4….
- 소수(float) : 1.555, 2.4535…

> Number 타입은 서로 연산기호를 이용하여 계산할 수 있다.

## String

처음부터 끝까지 문자(Text)로 구성되어 있다는 의미

## variables

- 변수 선언을 통해 코드를 간결하게 할 수 있다.
- JavaScript 변수명은 보통 camelCase를 사용한다.

### let

- 재선언 금지
- 재할당 가능

### const

- 재선언 금지
- 재할당 금지

### var

- 재선언 가능
- 재할당 가능

> const 항상, let 업데이트가 필요할 때, var 절대 쓰지 말기

## Boolean

- true
- false

## null/undefined

- null : 값이 없음
- undefined : 값이 정의되지 않음

## Arrays

- 선언 : const 배열명 = [1, 2, ….]
- 배열명[index]로 특정 순서 값 지정 가능
- 배열에 값 추가 : 배열명.push(값);
- 추가 및 변경 가능 : 배열명[index] = 값;

## Object

property를 가진 데이터를 저장, { } 사용

```jsx
const person = {
  name: jeon,
  age: 28,
};
```

불러오는 방법

- person.name → jeon
- person[”name”] → jeon

프로퍼티를 바꾸는 것은 가능하지만 선언된 object를 바꾸는 것은 불가능하지만 프로퍼티 추가는 가능

<br/>

# function

반복해서 쓸 수 있는 코드조각

```jsx
function 함수명(argument) {
  실행코드;
  return;
}

함수명();
```

### prompt();

- 사용자에게 창을 띄워 값을 받음
- 답을 할 때까지 코드의 실행을 멈춤
- 별로 안이쁘고 css로 바꿀 수도 없음
- string이 디폴트

string → number : parseInt();

### inNaN : 무언가가 NaN인지 판별하는 방법

- true/false로 반환

<br/>

# 조건문

```jsx
if(조건){
	실행코드 = true -> 실행
	실행코드 = false -> else 실행
} else {
	실행코드
}
```

### &&(and) : 좌항, 우항 모두 true여야 true 반환

### ||(or) : 좌항, 우항 중 하나라도 true면 true 반환

### == : 값만 같으면 true

### === : 값과 자료형 모두 같아야 true
