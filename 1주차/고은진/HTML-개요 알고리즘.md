# HTML 개요 알고리즘

## Outline이란

- 개요, 윤곽
- 간결하게 추려낸 주요 내용
- 웹 문서의 개요는 <mark>**헤딩**</mark>과 <mark>**섹션**</mark>으로 형성

|                           헤딩이 잘 구성된 구조                            |                       헤딩이 잘 구성되지 않은 구조                       |
| :------------------------------------------------------------------------: | :--------------------------------------------------------------------: |
| ![image](https://github.com/user-attachments/assets/29e39b87-a769-49b2-a153-20055fa9fd04) | ![image](https://github.com/user-attachments/assets/dcf0b92a-d901-45dd-876f-1cc316a1bb96) |

<br />

## Heading이란

Heading은 문서 개요를 형성하는 기본 아이템으로, 웹 브라우저와 화면 낭독기에 문서 개요를 제공한다. 문서의 골격을 설명하는 중요한 태그이므로 생략해서는 안된다.

**HTML**

```jsx
<h1>A</h1>
<h2>B</h2>
<h3>C</h3>
```

**브라우저 / 화면낭독기**

```jsx
-A - B - C;
```

- 위와 같이 Heading 없이는 문서의 개요 또한 없는 것이다.

<br />

## Title과 Heading의 차이

- `<title>`: 문서의 제목. 문서에서 **한 번만** 사용할 수 있다.
- `<h*>`: 섹션의 제목. 문서에서 **여러 번** 사용할 수 있다.

<br />

## Sectioning Content

Sectioning Content는 HTML5에서 새롭게 추가된 명세다. 명시적 개요를 생성하는 개요 컨테이너이며 적절한 수준의 헤딩을 자식 요소로 사용해야 한다.

- `<article>`: 독립적으로 배포가 가능한 콘텐츠 (기사, 본문, 맥락, 댓글도 독립적으로 볼 수 있다.)
- `<aside>`: 페이지의 주요 내용이 아닌 부수적인 부분 (배너, 연관 컨텐츠)
- `<nav>`: 사이트의 주된 탐색 메뉴 (footer에 있는 바로가기 링크는 주된 탐색 메뉴가 아니다.)
- `<section>`: 주제별로 나누거나 묶는 용도 (article과의 차이점은 독립성이다.)

> 위의 태그를 사용했는데 Heading을 명시하지 않았다면 어색한 마크업이 된다. 따라서 Heading이 눈에 보이지 않더라도 마크업하고 CSS로 가리는 방식으로 작업해야 한다.

**HTML**

```jsx
<h1>A</h1>
<article>
  <h2>B</h2>
  <section>
    <h3>C</h3>
  </section>
</article>
```

**브라우저 / 화면낭독기**

```jsx
-A - B - C;
```

- 섹셔닝 요소를 적극 사용하되 아웃라인 알고리즘(섹셔닝 루트, 헤딩 수준 자동 보정) 명세에 의존하지 말 것.

<br />

## 명시적 섹션

명시적 섹션은 헤딩과 함께 섹셔닝 콘텐츠(article, aside, nav, section)를 사용하여 섹션의 범위를 명시적으로 알 수 있는 섹션이다.

```jsx
<h1>A</h1>
<article>
  <h2>B</h2>
  <section>
    <h3>C</h3>
  </section>
</article>
```

<br />

## 암시적 섹션

암시적 섹션은 섹셔닝 콘텐츠(article, aside, nav, section)를 사용하지 않고 헤딩만을 사용하여 암시적으로 개요가 생성된 섹션이다.

```jsx
<h1>A</h1>
<h2>B</h2>
<h3>C</h3>
```

<br />

## **어색한 섹션**

<mark>**최상위 헤딩이 없는 경우(H1 없이 H2가 있는 경우)**</mark>

**HTML**

```html
<body>
  <p>A</p>
  <article>
    <h2>B</h2>
  </article>
</body>
```

**브라우저 / 화면낭독기**

```html
- ? - B
```

<br />

<mark>**헤딩이 없는 경우**</mark>

**HTML**

```html
<article>
  <p>A</p>
  <section>
    <p>B</p>
  </section>
</article>
```

**브라우저 / 화면낭독기**

```html
- ? - ?
```
