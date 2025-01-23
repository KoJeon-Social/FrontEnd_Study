# HTML 기타

# HTML의 DTD
### Document Type Definition으로 마크업 언어에서 문서 형식을 정의하는 것
  ```html
  <!DOCTYPE html> <!DOCTYPE html>
  ```
  > HTML5 에서는 위와 같이 대소문자를 구분하지 않고 사용 가능
> 

<br/>

### `<img>` 요소의 필수 속성
  ```html
  <img src="./images/sample.png" alt="sample" />
  ```
  - `<img>` 요소의 필수 속성으로 이미지 자원의 주소를 위한 **src 속성**과 이미지 대체 텍스트를 위한 **alt 속성** 두 개는 필수 속성
- `<button>` 요소의 type 속성을 생략하는 경우
  - `<button>` 요소는 type 속성에 따라서 다른 기능을 갖게 된다. 그런데 만약 type 속성을 생략하면 **type=”submit”** 이 적용된다. 즉, `<form>...</form>` 요소 내부의 사용자 입력 내용을 전송하는 기능을 갖게 됩니다.
  ```html
  // type 속성 생략
  <button>전송</button>

  // type 속성 명시
  <button type="submit">전송</button>
  ```
  - 위와 같이 코드를 작성했을 때 동일하게 동작
   <br/>
- `<table>` 콘텐츠의 제목 마크업
  - 2차원의 격자형 데이터를 표시하기 위한 표 마크업으로, `<caption>` `<figcaption>` 요소로 표의 제목을 마크업할 수 있다.
  ```html
  // caption 사용 예
  <table>
    <caption>
      표의 제목
    </caption>
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
  <br/>
- `<fieldset>` 콘텐츠의 제목 마크업
  - `<fieldset>` 요소는 폼 요소를 내용에 따라 나누거나 그룹핑할 때 사용하는 요소로 `<legend>` 요소로 제목을 표시한다.
  ```html
  <form>
    <fieldset>
      <legend>회원 가입(필수 양식)</legend>
    </fieldset>
    <fieldset>
      <legend>회원 가입(선택 양식)</legend>
    </fieldset>
  </form>
  ```
  <br/>
- `<script>` 요소의 부모 요소로 정당하지 않은 요소
  - `<script>` 요소는 `<head>` `<body>` 요소를 부모로 가질 수 있지만 `<html>` `<noscript>` 요소는 부모가 될 수 X
  > `<head>` `<body>` 부모 요소로 O
  > `<html>` `<noscript>` 부모 요소로 X
  <br/>
# `<form>` 요소의 필수 속성
  - `<form>` 요소는 정보를 제출하기 위한 대화형 컨트롤을 포함하는 문서 구획을 나타내며, 필수 속성이 없다.
  ### 선택 속성 중 대표 속성
  - action 속성 : `<form>` 요소에 포함된 사용자 입력 내용을 **전송하는 페이지의 URL을 명시**하는 속성 (명시하지 않으면 현재 페이지 URL을 할당)
- method 속성 : 양식을 제출할 때 사용할 **HTTP 메서드를 명시**한다. (명시하지 않으면 GET 상태)
- onsubmit 속성 : 양식이 전송되는 순간을 제어할 수 있는 선택적 자바스크립트 이벤트 리스너
### `<form>` 요소를 전송할 때 입력 값을 서버로 전송하지 않는 요소
  ```html
  <input disabled />
  ```
  - `<form>` 요소에 포함된 사용자 입력 내용이 submit 될 때 콘트롤에 disabled 라는 속성이 포함되어 있으면 해당 요소에 입력된 value 속성의 값은 서버로 전송하지 않는다.

<br/>

# `<main>` 요소의 활용 목적
  - `<main>` 요소는 문서 또는 애플리케이션의 메인 콘텐츠로써 중심 주제 또는 핵심 기능을 의미한다. 또한 하나의 문서에 한 번만 선언할 수 있는 요소이다.
  - 단 hidden 속성으로 숨김 처리한 여러 개의 `<main>` 요소를 제공하고 단 하나의 `<main>` 요소만 화면에 표시하도록 처리하는 것을 허용

<br/>

# `<section>` 요소의 활용 목적
  - `<section>` 요소는 문서의 챕터 또는 프로그램 섹션을 의미
  - 보통 제목으로 시작하는 한 가지 주제 또는 하나의 애플리케이션 영역이기도 함
  - `<section>` 요소의 내용은 주변 맥락을 제거한 상태로 배포하기에는 적절하지 않을 수 있음
    > `<article>` 요소는 주변 맥락을 제거하고 독립적으로 배포하기에 적절하다는 점이 다름

<br/>

# `<article>` 요소의 활용 목적
  - 독립적으로 배포 혹은 재사용 할 수 있는 섹션
  - 웹 페이지 본문, 신문의 기사, 블로그 포스트 본문 또는 댓글 영역을 마크업 하기에 적절한 요소
      > `<section>` 요소는 주변 맥락을 제거하고 독립적으로 배포했을 때 보통 어색하다는 점이 다름

      <br/>
      
# `<input>` 요소의 type 종류
  - `hidden, text, search, tel, url, email, password, date, month, week, time, datetime-local, number, range, color, checkbox, radio, file, submit, image, reset, button`

<br/>

# HTML5 문법으로 유효하지 않는 코드
  - `<main>` 요소는 페이지의 핵심 콘텐츠를 의미하는 맥락이기 때문에 body, div 요소 외 다른 요소의 자식 또는 자손이 될 수 X
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
<br/>

# `<b>` ↔ `<strong>` , `<i>` ↔ `<em>` 요소들의 차이점
  - `<b>` 요소와 `<strong>` 요소는 브라우저에 표시되는 모습은 같지만 역할은 다르다.
  - 둘 다 요소에 텍스트를 넣으면 텍스트가 진하게 보이도록 bold 처리
![image](https://github.com/user-attachments/assets/a24e0fb4-3abb-4e74-a659-fb43311c5dbc)

  - `<b>` 요소는 단순히 텍스트를 진하게 표시하는 역할만 함. 따라서 서식상 다른 텍스트와 대비된 스타일로 강조를 하고 싶을 때 사용
  - `<strong>` 요소는 단순히 보여지는 강조가 아닌 실제로 페이지 내의 중요한 부분으로 브라우저에게 알려주는 역할
  > 브라우저가 `<strong>` 요소를 해석할 때 페이지 내에서 중요한 부분으로 이해하며, 이는 브라우저에서 지원되는 웹 접근성에 큰 기여를 한다.
### 스크린 리더 (Screen Reader)를 사용하는 경우
  - `<strong>` 요소를 사용하면 스크린 리더에서 해당 부분이 강조되었다고 알려주지만 `<b>` 요소는 알려주지 않는다.
### `<i>` 요소와 `<em>` 요소의 차이
  - `<i>` 요소는 브라우저에 기울임만을 나타내고 `<em>` 요소는 기울임과 함께 실질적인 강조를 의미
  > 스크린 리더기에도 동일하게 영향을 미침
### 요약 정리
  - 즉, 특정한 텍스트에 대해 실제로도 강조하고자 하는 경우 `<strong>` `<em>` 요소들을, 단순히 텍스트를 bold 처리, 기울임 처리를 하려면 `<b>` `<i>` 요소를 사용
