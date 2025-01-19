# HTML 기타

<br />

## HTML의 DTD

DTD란 Document Type Definition으로 마크업 언어에서 문서 형식을 정의하는 것이다.

```jsx
<!DOCTYPE html>
<!doctype HTML>
```

위와 같이 HTML5에서는 대소문자를 구분하지 않고 사용할 수 있다.

<br />

## `<img>` 요소의 필수 속성

```jsx
<img src="./images/sample.png" alt="sample" />
```

- **src 속성**: 이미지 자원의 주소
- **alt 속성**: 이미지 대체 텍스트

<br />

## `<button>` 요소의 type 속성을 생략하는 경우

`<button>` 요소는 type 속성에 따라 다른 기능을 갖는다. 만약 type 속성을 생략하면 자동으로 `type=”submit”`이 적용된다. 즉 `<form>…</form>` 요소 내부의 사용자 입력 내용을 전송하는 기능을 갖게 된다.

```jsx
// type 속성 생략
<button>전송</button>

// type 속성 명시
<button type="submit">전송</button>
```

두 코드 모두 동일하게 동작한다.

<br />

## `<table>` 콘텐츠의 제목 마크업

`<table>` 요소는 2차원의 격자형 데이터를 표시하기 위한 표 마크업으로서 `<caption>` 요소와 `<figcaption>` 요소로 표의 제목을 마크업할 수 있다.

```jsx
// caption 사용 예
<table>
  <caption>표의 제목</caption>
  <tr>
    <th>...</th>
    <td>...</td>
  </tr>
</table>

// figcaption 사용 예
<figure>
  <figcaption>표의 제목</figcaption>
  <table>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
  </table>
</figure>
```

> <table> 요소는 단 하나의 <caption> 요소만을 명시할 수 있으며 <caption> 요소는 언제나 <table> 요소 바로 다음에 위치해야 한다.

<br />

## `<fieldset>` 콘텐츠의 제목 마크업

`<fieldset>` 요소는 폼 요소를 내용에 따라 나누거나 그룹핑할 때 사용하는 요소로 그룹화 된 주위에 얇은 테두리를 이용하여 박스를 그린다. 주로 `<legend>` 요소를 통해 제목을 표시한다.

```jsx
<form>
  <fieldset>
    <legend>회원 가입(필수 양식)</legend>
  </fieldset>
  <fieldset>
    <legend>회원 가입(선택 양식)</legend>
  </fieldset>
</form>
```

<br />

## `<script>` 요소의 부모 요소로 정당하지 않은 요소

`<script>` 요소는 `<head>`, `<body>` 요소를 부모로 가질 수 있지만, `<html>`, `<noscript>` 요소는 부모가 될 수 없다.

<br />

## `<form>` 요소의 필수 속성

`<form>` 요소는 정보를 제출하기 위한 대화형 컨트롤을 포함하는 문서 구획을 나타내며 필수 속성은 없다.

선택 속성 중 **action 속성**은 `<form>` 요소에 포함된 **사용자 입력 내용을 전송받아 처리할 페이지의 URL을 명시**한다. (명시하지 않으면 현재 페이지 URL을 할당한다.)

**method 속성**은 **양식을 제출할 때 사용할 HTTP 메서드를 명시**한다. (명시하지 않으면 GET 상태가 된다.)

- **GET**: 양식 데이터를 action URL과 ? 구분자 뒤에 이어 붙여서 전송
  ![image](https://github.com/user-attachments/assets/a5cb1fff-0afa-4f11-b22d-3fab49dd3601)
  GET 방식은 위와 같이 **주소에 데이터를 추가하여 전달**한다. 데이터가 주소 입력창에 그대로 나타나므로 데이터의 크기가 제한되고 민감한 정보를 전송할 땐 이러한 방식을 지양해야 한다.
- **POST**: 양식 데이터를 요청 본문으로 전송
  ![image](https://github.com/user-attachments/assets/2ae024d6-784f-46ed-9a16-a7e581b27090)
  POST 방식은 **데이터를 별도로 첨부하여 전달**한다. 데이터가 외부에 드러나지 않고 전송할 수 있는 데이터의 크기 또한 제한이 없으므로 보안과 활용성을 모두 챙길 수 있다.

**onsubmit 속성**은 양식이 전송되는 순간을 제어할 수 있는 선택적 자바스크립트 이벤트 리스너다.

<br />

> **action과 onSubmit의 차이**
>
> **action**
> form 데이터를 처리할 프로그램의 URI를 지정한다.
> action 속성에 웹문서 링크를 문자열 형태로 작성한 다음 form 데이터를 전송하면 해당 웹문서로 이동할 수 있다.
>
> **onSubmit**
> 양식 제출 이벤트가 발생할 때의 동작을 지정한다.
> form 태그 내부에서 <input type=’submit’>로 인해 발생하는 이벤트를 처리할 수 있다. 일반적으로 자바스크립트 함수를 지정해 처리하는 경우가 많으며 해당 함수에서 true를 반환하면 form이 전송되고, false를 반환하면 전송되지 않는다. 이때 이벤트 처리를 강제 종료시키므로 action이 처리되는 일은 일어나지 않는다.
>
> ```
> <form action='#' onSubmit='return test()'>
>   <input type='submit' value='submit'/>
> </form>
> ```
>
> form 안에 있는 input을 클릭하면 action이 처리되기 전에 submit 이벤트에 대한 처리가 시작된다. 따라서 test() 함수가 동작한 후 action이 역할을 하게 된다.

<br />

## `<form>` 요소 전송 시 입력 값을 서버로 전송하지 않는 요소

```jsx
<input disabled>
```

`<form>` 요소에 포함된 사용자 입력 내용이 submit 될 때 컨트롤에 disabled 속성이 포함되어 있으면 해당 요소에 입력된 value 속성의 값은 서버로 전송되지 않는다.

<br />

## `<main>` 요소의 활용 목적

`<main>` 요소는 문서 또는 애플리케이션의 메인 콘텐츠로서 중심 주제 또는 핵심 기능을 의미한다. 또한 **하나의 문서에 한 번만 선언**할 수 있다.

단 hidden 속성으로 숨김 처리한 여러 개의 `<main>` 요소를 제공하고 단 하나의 `<main>` 요소만 화면에 표시하도록 처리하는 것은 허용한다.

<br />

## `<section>` 요소의 활용 목적

`<section>` 요소는 문서의 챕터 또는 프로그램 섹션을 의미한다. 보통 제목으로 시작하는 한 가지 주제 또는 하나의 애플리케이션 영역이기도 한다. 또한 `<section>` 요소의 내용은 주변 맥락을 제거한 상태로 배포하기에는 적절하지 않을 수 있다.

> `<article>` 요소는 주변 맥락을 제거하고 독립적으로 사용할 수 있다는 점이 `<section>` 요소와의 차이점이다.

<br />

## `<article>` 요소의 활용 목적

`<article>` 요소는 독립적으로 배포 혹은 재사용 할 수 있는 섹션을 나타낸다. 웹 페이지 본문, 신문의 기사, 블로그 포스트 본문 또는 댓글 영역을 마크업하기에 적절한 요소다.

<br />

## `<input>` 요소의 type 종류

`hidden, text, search, tel, url, email, password, date, month, week, time, datetime-local, number, range, color, checkbox, radio, file, submit, image, reset, button`

<br />

## HTML5 문법으로 유효하지 않은 코드

`<main>` 요소는 페이지의 핵심 컨텐츠를 의미하므로 body, div 요소 외 다른 요소의 자식 또는 자손이 될 수 없다.

```html
// 유효한 main 요소 사용
<body>
  <main></main>
</body>

// 유효하지 않은 main 요소 사용
<section>
  <main>...</main>
</section>
```

<br />

## `<b>` ↔ `<strong>`, `<i>` ↔ `<em>` 요소들의 차이점

**`<b>` 요소와 `<strong>` 요소의 차이**

`<b>` 요소와 `<strong>` 요소는 브라우저에 표시되는 모습은 같지만 역할은 다르다.

| 요소       | 사용 예시                 | 브라우저 표시 모습 |
| ---------- | ------------------------- | ------------------ |
| `<b>`      | `<b>텍스트</b>`           | **텍스트**         |
| `<strong>` | `<strong>텍스트</strong>` | **텍스트**         |

- `<b>` 요소는 단순히 텍스트를 진하게 표시하는 역할만 한다. 따라서 서식상 다른 텍스트와 대비된 스타일로 강조하고 싶을 때 사용한다.
- `<strong>` 요소는 단순히 보여지는 강조가 아닌 실제로 페이지 내의 중요한 부분으로 브라우저에게 알려주는 역할을 한다.
  - 브라우저가 `<strong>` 요소를 해석할 때 페이지 내에서 중요한 부분으로 이해하며, 이는 웹 접근성에 큰 기여를 한다.
- 스크린 리더를 사용하는 경우 `<strong>` 요소를 사용하면 스크린 리더에서 해당 부분이 강조되었다고 알려주지만 `<b>` 요소는 알려주지 않는다.

**`<i>` 요소와 `<em>` 요소의 차이**

`<i>` 요소와 `<em>` 요소도 마찬가지로 `<i>` 요소는 브라우저에 기울임만을 나타내고 `<em>` 요소는 기울임과 함께 실질적인 강조를 의미하게 된다. 또한 스크린 리더에도 동일하게 영향을 미친다.
