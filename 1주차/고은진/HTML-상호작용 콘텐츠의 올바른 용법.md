# HTML 상호작용 컨텐츠의 올바른 용법

<br />

## 인터렉티브 컨텐츠(Interactive Content)

인터렉티브 컨텐츠는 사용자와 상호 작용할 수 있는 컨텐츠를 의미하며 입력 장치(키보드, 마우스)로 조작할 수 있다.

`a, audio, button, details, embed, iframe, img, input, label, select, texture, video`

<br />

## `<a>`와 `<button>` 요소의 차이

`<a>`와 `<button>` 요소는 쓰임이 비슷해 보이지만 다른 용도로 사용된다. `<a>` 요소는 실행 결과를 가리킬 수 있는 URL이 있을 때 사용한다. 반대로 참조할 URL이 없는 경우 `<button>` 요소를 사용한다.

![image](https://github.com/user-attachments/assets/68df6fde-a47a-4acf-9f04-4d607c8803ab)

![image](https://github.com/user-attachments/assets/7e61d09b-59dc-4e3a-860b-df39b5422571)

![image](https://github.com/user-attachments/assets/52c21799-ae6a-487c-9020-f009c9b139cd)
<p align="center">
민트색 : a 태그 / 보라색 : button 태그
</p>

- 위와 같이 탭을 크릭하면 페이지 전체를 갱신하거나 URL 구조가 바뀌는 것에 `<a>` 요소를 사용한다. 타겟 URL을 설정하지 않는 상황에서는 `<button>` 요소를 사용한다.

<br />

## `<a>` 요소의 target 속성

```html
<a href="https://www.naver.com" target="_blank" />
```

새 창으로 문서를 띄우는 경우 target 속성으로 “\_blank”로 설정한다. 이때 자식 창에서 부모 창의 제어 권한을 획득할 수 있게 된다. 즉 자바스크립트를 이용해 **사용자가 모르는 사이에 부모 페이지를 다른 페이지로 바꿔치는 것**이다. 이를 <mark>**탭 가로채기(tapnabbing) 공격**</mark>이라 한다.

새 창으로 열린 외부 페이지 B는 자바스크립트 window.opener 객체를 통해 부모 페이지 A의 제어 권한을 획득한다.

> **탭 가로채기(Tabnabbing) 공격**
>
> <mark>HTML 문서 내에 링크(target이 \_blank인 Anchor 태그)를 클릭 시 새로 열린 페이지에서 기존의 문서 위치를 피싱 사이트로 변경해 정보를 탈취하는 공격 기술</mark>
>
><br />
>
> **공격 절차**
>
> 1. 사용자가 현재 합법적인 브라우저(A) 탭에서 새 탭으로 여는 웹사이트(실제로는 피싱 사이트)(B)를 클릭합니다.
>    - (B) 사이트에는 `window.opener` 속성이 존재합니다.
>    - 자바스크립트를 사용해 opener의 location을 피싱 목적으로 원래의 (A) 페이지의 `/login` 페이지로 변경합니다.
> 2. 악성 웹사이트(B)는 '합법적인 웹사이트를 가장한 Fake Website'(C)를 사용자에게 가짜 버전으로 강제로 리다이렉션 합니다.
>    - **사용자는 로그인이 풀렸다고 생각하고 다시 ID와 PW를 입력합니다.**
> 3. Fake Site(C)에서는 사용자가 입력한 계정 정보를 탈취한 뒤 원래의 합법적인(A) 웹 사이트로 리다이렉트합니다.
>    - 여기서 A 사이트에 로그인 계정 정보가 그대로 남아있으므로 C 사이트에서 입력해서 -> A의 홈으로 이동시켰을 때 자연스러운 전환이기 때문에이상한 낌새를 찾기 어려울 것입니다.

위와 같은 문제를 아래의 방식으로 해결할 수 있다.

<br />

```html
<a href="https://www.naver.com" target="_blank" rel="noopener noreferrer" />
```

- noopner 값은 window.opener 객체를 제거하여 제어가 불가능하도록 한다.
- 최신 브라우저는 target=”\_blank” 링크에 rel=”noopner” 속성을 암시적으로 적용하고 있다. 그러나 noopener를 지원하지 않는 이전 브라우저를 위해 `rel=”noopener noreferrer”` 속성을 명시하는 것이 좋다.

> **rel=noopner 속성**
>
>`rel=noopener` 속성이 부여된 링크를 통해 열린 페이지는 location 변경과 같은 자바스크립트 요청을 거부한다. 정확히 말해서 Uncaught TypeError 에러를 발생시킨다.
>
>`noopner` 속성은 보안적 측면 외에도 성능 측면에서도 이점을 가진다. `_blank` 속성으로 열린 탭은 언제든지 `opner`를 참조할 수 있다. 따라서 부모 탭과 같은 스레드에서 페이지가 동작하여 새 탭의 페이지가 리소스를 많이 사용한다면 부모 탭도 함께 느려진다.
>반면 `noopener` 속성을 사용하여 열린 탭은 부모를 호출할 일이 없으므로 새로운 페이지가 느리다고 부모 탭까지 느려질 일도 없다.

>

<br />

## `<details>`, `<summary>` 요소

- 보통 사용자가 직접 접거나 펼 수 있는 대화형 위젯에 사용하기 적합하다.
- details 요소에 open 속성을 넣으면 열린 상태로 표시된다. (open 속성이 설정되기 전까지는 화면에 보이지 않는다.)
- summary 요소는 details 요소의 나머지 부분에 대한 요약, 캡션, 범례를 의미하고 숨겨진 폼을 드러내기도 한다. (summary 요소를 클릭함으로써 details 요소를 보이도록, 혹은 숨기도록 할 수 있다.)

```html
<details>
  <summary>Details</summary>
  Something small enough to escape casual notice.
</details>
```

![image](https://github.com/user-attachments/assets/b1a4cbc8-c875-4ea6-a031-a15735cf87db)

![image](https://github.com/user-attachments/assets/f248e389-66b8-4317-92a1-c20937e67910)

<p align="center">
summary 요소 클릭 시 details 요소 보임
</p>

<br />

## `<input>` 요소

input 요소는 type 특성에 따라 현격히 달라진다.

<br />

**type 유형**

| **유형**       | **설명**                                                                                                |
| -------------- | ------------------------------------------------------------------------------------------------------- |
| button         | 기본 행동을 가지지 않으며 value 을 레이블로 사용하는 푸시 버튼                                          |
| checkbox       | 단일 값을 선택하거나 선택 해제할 수 있는 체크박스                                                       |
| color          | 색을 지정할 수 있는 컨트롤                                                                              |
| date           | 날짜를 지정할 수 있는 컨트롤                                                                            |
| datetime-local | 날짜와 시간을 지정할 수 있는 컨트롤                                                                     |
| email          | 이메일 주소를 편집할 수 있는 필드                                                                       |
| file           | 파일을 지정할 수 있는 컨트롤, accept 특성을 사용하면 허용하는 파일 유형을 지정할 수 있음                |
| hidden         | 보이지 않지만 값은 서버로 전송하는 컨트롤                                                               |
| image          | src 특성에 지정한 이미지로 나타나는 시각적 제출 버튼                                                    |
| month          | 연과 월을 지정할 수 있는 컨트롤                                                                         |
| number         | 숫자를 입력하기 위한 컨트롤                                                                             |
| password       | 값이 가려진 한 줄 텍스트 필드                                                                           |
| radio          | 같은 name 값을 가진 여러 개의 선택 중에서 하나의 값을 선택하게 하는 라디오 버튼                         |
| range          | 디폴트 값이 중간값인 범위 위젯으로 표시, 접속사 min 과 max 사이에 수용되며 수용 가능한 값의 범위를 정의 |
| reset          | 양식의 내용을 디폴트값으로 초기화하는 버튼                                                              |
| search         | 검색 문자열을 입력하는 한 줄 텍스트 필드                                                                |
| submit         | 양식을 전송하는 버튼                                                                                    |
| tel            | 전화번호를 입력하는 컨트롤                                                                              |
| text           | 디폴트 값, 한 줄의 텍스트 필드                                                                          |
| time           | 시간대가 없는 시간 값을 입력하는 컨트롤                                                                 |
| url            | URL을 입력하는 필드                                                                                     |
| week           | 시간대가 없는 주-년 값과 주의 값을 구성하는 날짜를 입력하는 컨트롤                                      |

<br />

**required 속성**

required 속성이 명시되어 있는 `<input>` 요소에 사용자가 내용을 작성하지 않으면 브라우저에 내장된 에러 또는 도움말 메시지를 표시해 준다.

```html
<input type="text" required />
<input type="password" required />
```

![image](https://github.com/user-attachments/assets/d2fd8497-a777-4436-9747-628eb8d4d798)


<br />

**placeholder 속성**

컨트롤에 초기값이 없을 때 사용자에게 데이터 입력을 지원하기 위해 제공하는 짧은 힌트. (label 대안으로 사용하지는 말 것)

```html
<input type="email" placeholder="sample@gmail.com" />
```

![image](https://github.com/user-attachments/assets/680445ec-521f-4bfc-81ca-7987dfd894f9)

<br />

## `<datalist>` 요소

datalist 요소는 다른 컨트롤을 위해 미리 정의된 옵션 세트를 의미한다.

```html
<label for="ice-cream-choice">Choose a flavor:</label>
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice" />

<datalist id="ice-cream-flavors">
  <option value="Chocolate" />
  <option value="Coconut" />
  <option value="Mint" />
  <option value="Strawberry" />
  <option value="Vanilla" />
</datalist>
```

- input 요소의 list 속성 값 === datalist 요소의 id 값
- 두 값이 동일해야 연결된다.

![image](https://github.com/user-attachments/assets/e393e418-f5e0-4acd-b7b4-2acf8ae43200)
