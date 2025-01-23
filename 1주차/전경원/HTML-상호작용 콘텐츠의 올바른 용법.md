# HTML 상호작용 콘텐츠의 올바른 용법

# 인터렉티브 콘텐츠 (Interactive Content)
  - 인터렉티브 콘텐츠는 사용자와 상호 작용할 수 있는 콘텐츠를 의미
- `a, audio, button, details, embed, iframe, img, input, label, select, texture, video`
    
    > 입력 장치 (키보드, 마우스) 로 조작 가능
    >

<br/>

# `<a>` 와 `<button>` 요소의 차이
  - 비슷해 보이지만 전혀 다른 용도로 사용되기 때문에 용도에 따라 구별해서 사용해야 함
  - `<a>` 요소는 실행 결과를 가리킬 수 있는 URL이 있을 때 사용
  - `<button>` 요소는 참조할 URL이 없으면 사용

<br/>

![image](https://github.com/user-attachments/assets/7a5c3019-a537-4fcb-8a35-3976a1d9a12a)
![image](https://github.com/user-attachments/assets/b833dfdf-868a-412a-986b-868ba5d6bef9)
![image](https://github.com/user-attachments/assets/7ee5fad1-2171-4171-8b21-7f5e80aa4b1c)

  > 민트색 : `<a>` / 보라색 : `<button>`
  - 위와 같이 탭을 클릭하면 페이지 전체를 갱신하거나 URL 구조가 바뀌는 것에 `<a>` 요소 사용
  - 타켓 URL을 설정하지 않는 상황에서는 `<button>` 요소 사용

<br/>

# HTML 상호작용 콘텐츠의 올바른 용법

### 인터렉티브 콘텐츠 (Interactive Content)
  - 인터렉티브 콘텐츠는 사용자와 상호 작용할 수 있는 콘텐츠를 의미
  - `a, audio, button, details, embed, iframe, img, input, label, select, texture, video`
  > 입력 장치 (키보드, 마우스) 로 조작 가능
### `<a>` 요소의 target 속성
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

<br/>

# `<details>` `<summary>` 요소
  - 열림 상태일 때 정보를 표시하는 위젯에 사용하기 적합
  - details 요소에 open 속성을 넣으면 열린 상태로 표시
  - summary 요소는 details 요소의 나머지 부분에 대한 요약, 캡션, 범례를 의미하고 숨겨진 폼을 드러내기도 함
  ```html
  <details>
    <summary>Details</summary>
    Something small enough to escape casual notice.
  </details>
  ```
 ![image](https://github.com/user-attachments/assets/1f8f4753-b918-4d24-971c-d7b397a941cd)
 
![image](https://github.com/user-attachments/assets/15a8d04d-4f54-4e97-88cb-8169e86305e6)

<br/>

# `<input>` 요소
  - `<input>` 요소의 동작 방식은 type에 따라 현격히 달라짐
  - **type 유형**
  ![image](https://github.com/user-attachments/assets/7ae50ace-b32d-4d87-9c21-1b21ab695192)

<br/>
                                
# required 속성
  - required 속성이 명시되어 있는 `<input>` 요소에 사용자가 그 input을 작성하지 않으면 브라우저에 내장된 에러 또는 도움말 메시지 표시
  ```html
  <input type="text" required />
  <input type="password" required />
  ```
 ![image](https://github.com/user-attachments/assets/4ce17543-9667-4843-9ccf-10299fab3f97)

<br/>

# placeholder 속성
  - 컨트롤에 초기 값이 없을 때 사용자에게 데이터 입력을 지원하기 위해 제공하는 짧은 힌트나 샘플
  > label 대안으로는 사용하지 말 것.
  ```html
  <input type="email" placeholder="sample@gmail.com" />
  ```
 ![image](https://github.com/user-attachments/assets/ecf3753f-a23f-4ae9-be59-05812b9b839d)

<br/>

# `<datalist>` 요소
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
    
  ![image](https://github.com/user-attachments/assets/3212df9d-59ba-44e6-b75a-bcab49f1b3e6)

