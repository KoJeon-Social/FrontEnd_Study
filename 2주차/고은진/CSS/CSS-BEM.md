# BEM(Block Element Modifier)

<br />

## BEM의 의미

**BEM**은 Block, Element, Modifier로 구성된 클래스 이름을 짓는 CSS 방법론이다.

> BEM 방법론은 id에는 사용할 수 없고 오직 class명에만 활용할 수 있다.

![Image](https://github.com/user-attachments/assets/7e8c05e2-9e91-4042-9f05-179678491c44)

| **Block**                       | **Element**                            | **Modifier**                                |
| ------------------------------- | -------------------------------------- | ------------------------------------------- |
| 재사용 가능한 독립적인 **블록** | 블록을 구성하는 종속적인 하위 **요소** | 블록 또는 요소의 **변형**(모양, 상태, 동작) |

<br />

## BEM 특징

1. 의미론적 클래스 선택자 작명 규칙

   > 약어 사용 피하기

2. 다른 형식의 선택자 사용을 제한

   > `--`, `__` 형식 이외에 다른 형식의 기호 사용 제한

3. 전역에서 유일한 이름 권장
4. 선택자 특이성(구체성, 선택자 우선순위 규칙)을 낮은 수준으로 유지 가능
5. HTML/CSS 연결이 느슨, 병렬 개발 가능

   > HTML에서는 의미만 다루고, 스타일은 CSS에서 처리한다.

<br />

## 작명 규칙을 잘못 관리한 사례

- 의미를 파악할 수 없는 작명
  ```css
  .cnt {
    ...;
  }
  .uw {
    ...;
  }
  .sa {
    ...;
  }
  ```
- 전역 공간을 선점한 흔한 이름
  ```css
  .top {
    ...;
  }
  .content {
    ...;
  }
  .button {
    ...;
  }
  ```

<br />

## CSS 선택자 우선순위 규칙(CSS selector specificity)

| **id** | **class, [attr], :class** | **type, ::element** |
| ------ | ------------------------- | ------------------- |
| 0      | 0                         | 0                   |

**예시**

| **CSS 선택자**     | **우선순위**   |
| ------------------ | -------------- |
| a                  | 0, 0, 1 ➜ 001  |
| .a                 | 0, 1, 0 ➜ 010  |
| #a                 | 1, 0, 0 ➜ 100  |
| #a a               | 1, 0, 1, ➜ 101 |
| #a.a a             | 1, 1, 1 ➜ 111  |
| #a#b[href]::before | 2, 1, 1 ➜ 211  |

<br />

## 스타일시트 분석

아래의 그래프는 cssstats.com에서 제공하는 웹 사이트 선택자 사용 현황 분석 기능을 사용하여 두 웹사이트를 분석한 것이다.

- 예시 A 사이트
  ![Image](https://github.com/user-attachments/assets/a7f29a1a-3d36-4951-8ee5-30df41909a4b)
  - 평균 선택자 점수: 58점
  - 최대 점수: 410점
- 예시 B 사이트
  ![Image](https://github.com/user-attachments/assets/e6a5b118-d99f-4802-95b3-14878902f2cb)
  - 평균 선택자 점수: 14점
  - 최대 점수: 101점

선택자 점수는 **낮게 유지**하고 **020 수준**으로 유지하는 것이 좋다. 예시 사이트들을 비교하면 B 사이트가 A 사이트보다 더 관리가 잘 되고 있는 사이트로 볼 수 있다. (CSS 선택자 분석 그래프는 낮고 평탄한 게 좋다.)

|                | **A 사이트**         | **B 사이트** |
| -------------- | -------------------- | ------------ |
| **Max score**  | 410                  | 101          |
| **CSS 선택자** | #a #b #c #d .f {...} | #a p {...}   |

<br />

## BEM 명명 규칙

| **기호** | **의미**             |
| -------- | -------------------- |
| `__`     | 하위 **요소**를 의미 |
| `--`     | 상태 **변형**을 의미 |

- 하나의 이름에 요소, 변형은 각 한 번만 허용한다.

**예시**

```css
.block {
  ...;
}
.block__element {
  ...;
}
.block__element--modifier {
  ...;
}
.block--modifier {
  ...;
}
```

- 이 형식 이외에 다른 형식은 허용하지 않는다.

```html
// 단순 블록
<button class="btn" />

// 요소 및 변형 추가
<em class="info__label info__label--warning" />
```

```html
// 잘못된 사용
<button class="btn--submit" />

// 올바른 사용
<button class="btn btn--submit" />
```

- <mark>‘변형’ 클래스는 단독 사용이 불가하며 항상 블록 또는 요소와 함께 사용해야 한다.</mark>

**실사용 예시**

```html
<div class="“card”">
  <img class="“card__image”" />
  <h2 class="“card__title”">I am a card</h2>
  <p class="“card__description”">I am the card paragraph</p>
  <!-- The button is an element inside the block -->
  <a class="“card__button”">Learn more</a>
</div>
```

![Image](https://github.com/user-attachments/assets/9683d86e-abbc-49cb-8fdb-70ad5172a4f2)

<br />

## BEM 안티패턴

**안티패턴(anti-pattern)** 은 비효율적이거나 비생산적인 패턴을 의미한다.

- 잘못된 사용
  ```css
  .photo {
    ...;
  } /* 특이성 10 */
  .photo img {
    ...;
  } /* 특이성 11 */
  .photo figcaption {
    ...;
  } /* 특이성 11 */
  ```
  - ‘선택자 특이성’이 높아지는 중첩 구조, 타입 선택자는 BEM에서 안티 패턴으로 간주한다. 따라서 타입 선택자는 피하는 게 좋다.
- 올바른 사용
  ```css
  .photo {
    ...;
  } /* 특이성 10 */
  .photo__img {
    ...;
  } /* 특이성 10 */
  .photo__figcaption {
    ...;
  } /* 특이성 10 */
  ```
  - 제어하려는 모든 요소에 클래스 이름을 부여하여 특이성을 관리한다.
- 잘못된 사용
  ```css
  .__elem {
    ...;
  }
  .--modi {
    ...;
  }
  .block__elem1__elem2 {
    ...;
  }
  .block--modi1--modi2 {
    ...;
  }
  ```
  - 블록/요소 이름 생략, 요소/변형 이름 중복을 금지한다.

<br />

## 키워드 연결 방법

| **표기법** |
| ---------- |
| PascalCase |
| camelCase  |
| kebab-case |
| snake_case |

<br />

## 접두어 사용

이름 공간을 위한 접두어 사용을 추천한다.

```css
.lzModal {
  ...;
}
.lzModal__title {
  ...;
}
.lzBtn {
  ...;
}
.lzBtn--small {
  ...;
}
```

- 접두어를 사용해야 다른 라이브러리와 공존이 가능하다. 예를 들어 접두어 없이 .btn 사용 시 bootstrap 라이브러리와 중첩될 수 있다.
