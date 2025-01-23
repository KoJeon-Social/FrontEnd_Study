# BEM (Block Element Modifier)

### BEM 의미

- Block, Element, Modifier로 구성된 클래스 이름을 짓는 CSS 방법론
  > BEM 방법론은 id에는 사용할 수 없고 오직 class명에만 활용 가능
  - Block : 재사용 가능한 독립적인 블록
  - Element : 블록을 구성하는 종속적인 하위 요소
  - Modifier : 블록 또는 요소의 변형 (모양, 상태, 동작)
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/d6c390a3-eb6f-4b45-a131-87c7fdec2b1d/image.png)

### BEM 특징

- 의미론적 클래스 선택자 작명 규칙
  > 약어 사용 피하기
- 다른 형식의 선택자 사용을 제한
  > `--`, `__` 형식 이외에 다른 형식의 기호 사용 제한
- 전역에서 유일한 이름 권장
- 낮은 선택자 특이성 유지
- HTML/CSS 연결이 느슨, 병렬 개발 가능

### 작명 규칙을 잘못 관리한 사례

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

### CSS 선택자 우선순위 규칙 (CSS selector specificity)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/4f599e6f-17a3-478c-94dd-957be6c612a2/image.png)

- 예시

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/8bbc91c0-8ddd-4e63-9b65-7418c34a3b8a/image.png)

### 스타일시트 분석

- 아래의 그래프는 cssstats.com에서 제공하는 웹 사이트 선택자 사용 현황 분석 기능을 사용하여 두 웹 사이트를 분석한 것이다.
  - 예시 A 사이트
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/2393a3e5-4a7b-4039-b4b6-bffcc4829ebe/image.png)
  > 평균 선택자 점수 : 58점
  > 최대 점수 : 410점
  - 예시 B 사이트
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/e1bf8a6a-504b-486b-b6c9-3eb5becc05e4/image.png)
  > 평균 선택자 점수 : 14점
  > 최대 점수 : 101점
- 선택자 점수는 낮게 유지하고 020 수준으로 유지하는 것이 좋다.
- 예시 사이트들을 비교해보면 B 사이트가 A 사이트보다 더 관리가 잘 되고 있는 사이트로 볼 수 있다.
  > CSS 선택자 분석 그래프는 낮고 평탄한게 좋다.
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/1eea72e8-44a1-480f-a9c1-60854ad01c52/image.png)

### BEM 명명 규칙

- `__` : 하위 요소를 의미
- `--` : 상태 변형을 의미
  > 하나의 이름에 요소, 변형은 각 한 번만 허용한다.
- 예시

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

> 이 형식 이외에 다른 형식은 허용 X

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

> 변형 클래스 단독 사용 불가, 한상 블록 또는 요소와 함께 사용

- 실사용 예시

```html
<div class="“card”">
  <img class="“card__image”" />
  <h2 class="“card__title”">I am a card</h2>
  <p class="“card__description”">I am the card paragraph</p>
  <!-- The button is an element inside the block -->
  <a class="“card__button”">Learn more</a>
</div>
```

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/c14bfa27-0344-43ce-abae-3cc99aa604f6/image.png)

### BEM 안티패턴

- 안티패턴 (anti-pattern)은 비효율적이거나 비생산적인 패턴을 의미
  - 잘못된 사용
  ```css
  .photo {
    ...;
  } // 특이성 10
  .photo img {
    ...;
  } // 특이성 11
  .photo figcaption {
    ...;
  } // 특이성 11
  ```
  > 선택자 특이성이 높아지는 중첩 구조, 타입 선택자는 BEM에서 안티 패턴으로 간주
  > 그러므로 타입 선택자는 가급적 피하는게 좋음
  - 올바른 사용
  ```css
  .photo {
    ...;
  } // 특이성 10
  .photo__img {
    ...;
  } // 특이성 10
  .photo__figcaption {
    ...;
  } // 특이성 10
  ```
  > 제어하려는 모든 요소에 클래스 이름을 부여하여 특이성 관리
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
  > 블록/요소 이름 생략, 요소/변형 이름 중복 금지

### 키워드 연결 방법

- 표기법
  - PascalCase
  - camelCase
  - kebab-case
  - snake_case

### 접두어 사용

- 이름 공간을 위한 접두어 사용 추천

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

> 접두어를 사용해야 다른 라이브러리와 공존 가능

> 예를 들어 접두어 없이 .btn 사용 시 bootstrap 라이브러리와 중첩될 수 있다.

### BEM 정리

- 의미론 작명법으로 읽고 이해하기 쉽다.
- 생소한 이름에 약어를 사용하지 않는다.
- 특이성을 020 보다 작게 유지한다.
- 선택자 이름은 전역 공간에서 유일하다.
- HTML/CSS 병렬 개발이 가능하다.
