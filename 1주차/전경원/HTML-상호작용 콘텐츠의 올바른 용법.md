- `<a>` 와 `<button>` 요소의 차이
  - 비슷해 보이지만 전혀 다른 용도로 사용되기 때문에 용도에 따라 구별해서 사용해야 함
  - `<a>` 요소는 실행 결과를 가리킬 수 있는 URL이 있을 때 사용
  - `<button>` 요소는 참조할 URL이 없으면 사용
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/68955067-e4d3-4636-81be-c984e7ee6c21/image.png)
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/26e86f35-ac83-49aa-ae39-ffd1452de930/image.png)
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/f1bb66fd-ad08-418f-8824-624a7a049e81/image.png)
  > 민트색 : `<a>` / 보라색 : `<button>`
  - 위와 같이 탭을 클릭하면 페이지 전체를 갱신하거나 URL 구조가 바뀌는 것에 `<a>` 요소 사용
  - 타켓 URL을 설정하지 않는 상황에서는 `<button>` 요소 사용

### HTML 상호작용 콘텐츠의 올바른 용법

- 인터렉티브 콘텐츠 (Interactive Content)
  - 인터렉티브 콘텐츠는 사용자와 상호 작용할 수 있는 콘텐츠를 의미
  - `a, audio, button, details, embed, iframe, img, input, label, select, texture, video`
  > 입력 장치 (키보드, 마우스) 로 조작 가능
- `<a>` 요소의 target 속성
  ```html
  <a href="https://www.naver.com" target="_blank" />
  ```
  - 보통 새 창으로 문서를 띄울 때 `<a>` 요소의 target 속성에 “\_blank”로 설정하여 사용
  - 하지만 자식 창에서 부모 창의 제어 권한을 획득할 수 있는 점을 주의해야 함
  - 즉, 자바스크립트를 이용해서 사용자가 모르는 사이에 부모 페이지를 다른 페이지로 바꿔치는 것 (**탭 가로채기(tapnabbing) 공격**)
    > 새 창으로 열린 외부 페이지 B는 자바스크립트 window.opener 객체를 통해 부모 페이지 A의 제어 권한을 획득
  - 이 문제를 HTML로 해결 가능
  ```html
  <a href="https://www.naver.com" target="_blank" rel="noopener noreferrer" />
  ```
  > noopener 값은 window.opener 객체를 제거 noreferrer 값은 window.opener 제어 불능
  > 최신 브라우저는 **target=”\_blank”** 링크에 **rel=”noopener”** 속성을 암시적으로 적용하고 있다. 그러나 noopener를 지원하지 않는 낡은 브라우저를 위해 **rel=”noopener onreferrer”** 속성을 명시하는 것이 좋다
  - 이처럼 rel 속성을 설정하면 탭 가로채기 공격을 방어할 수 있다.
- `<details>` `<summary>` 요소
  - 열림 상태일 때 정보를 표시하는 위젯에 사용하기 적합
  - details 요소에 open 속성을 넣으면 열린 상태로 표시
  - summary 요소는 details 요소의 나머지 부분에 대한 요약, 캡션, 범례를 의미하고 숨겨진 폼을 드러내기도 함
  ```html
  <details>
    <summary>Details</summary>
    Something small enough to escape casual notice.
  </details>
  ```
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/ddf6d4b1-6082-4eb1-82b3-3ae93dbbe5c1/image.png)
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/4beb603e-96e6-4d63-b884-14a9cdf892b6/image.png)
- `<input>` 요소
  - `<input>` 요소의 동작 방식은 type에 따라 현격히 달라짐
  - **type 유형**
  | 유형           | 설명                                                                                                    |
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
- required 속성
  - required 속성이 명시되어 있는 `<input>` 요소에 사용자가 그 input을 작성하지 않으면 브라우저에 내장된 에러 또는 도움말 메시지 표시
  ```html
  <input type="text" required />
  <input type="password" required />
  ```
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/9f8cca16-78f2-4946-89cd-80ac32b962de/image.png)
- placeholder 속성
  - 컨트롤에 초기 값이 없을 때 사용자에게 데이터 입력을 지원하기 위해 제공하는 짧은 힌트나 샘플
  -
  > label 대안으로는 사용하지 말 것.
  ```html
  <input type="email" placeholder="sample@gmail.com" />
  ```
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/6dab5ead-0f22-4965-941a-50253fef19d5/image.png)
- `<datalist>` 요소
  - 다른 컨트롤을 위해 미리 정의된 옵션 세트
  ```html
  <label for="ice-cream-choice">Choose a flavor:</label>
  <input
    list="ice-cream-flavors"
    id="ice-cream-choice"
    name="ice-cream-choice"
  />

  <datalist id="ice-cream-flavors">
    <option value="Chocolate" />
    <option value="Coconut" />
    <option value="Mint" />
    <option value="Strawberry" />
    <option value="Vanilla" />
  </datalist>
  ```
  - input 요소의 list 속성 값 === datalist 요소의 id 값
  - 두 값이 동일해야 연결된다
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/e9e42772-69fc-4768-914d-73f9861cbbf5/image.png)
