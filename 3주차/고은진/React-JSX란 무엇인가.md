## JSX란 무엇인가?

**JSX**는 리액트 라이브러리에서 사용하는 문법으로 JavaScript를 확장한 문법이다.

JSX는 React 앨리먼트를 생성한다. 즉 React에서 앨리먼트를 만들 때 사용하는 `React.createElement`의 간편 표현식이기도 하다.

React는 JSX 사용이 필수는 아니지만 JavaScript 코드 안에서 UI 관련 작업을 할 때 시각적으로 더 도움이 된다. 또한 React가 도움이 되는 에러 및 경고 메시지를 표시할 수 있게 해준다.

## JSX 표현식

```jsx
const name = "Ko Eunjin";
const element = <h1> Hello, {name}</h1>;

ReactDOM.render(element, document.getElementById("root"));
```

JSX의 중괄호 안에는 유효한 모든 JavaScript 표현식을 넣을 수 있다.
