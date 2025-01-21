# Outline : 개요, 윤곽 (간결하게 추려 낸 주요 내용)

# Heading : 문서 개요를 형성하는 기본 아이템

- 웹 브라우저와 화면 낭독기에 문서 개요를 드러내는 방법
- HTML ↔ 브라우저 / 화면 낭독기

  - HTML

  ```html
  <h1>A</h1>
  <h1>B</h1>
  <h1>C</h1>
  ```

  - 브라우저 / 화면 낭독기

  ```html
  - A
    - B
      - C
  ```

- 즉, <Heading> 없이는 문서의 개요도 없음

<br/>

# Title과 Heading의 차이

- <title> 요소는 문서의 제목 : 문서에서 한 번만 사용할 수 있음
- <h\*> 요소는 섹션의 제목 : 문서에서 여러 번 사용할 수 있음

<br/>

# Sectioning Content

- HTML5에서 새롭게 추가된 명세
- 명시적 개요를 생성하는 개요 컨테이너이며 적절한 수준의 헤딩을 자식 요소로 사용해야 함
- 태그 종류
  - <article> : 기사, 본문, 맥락 독립적으로 배포가 가능
  - <aside> : 페이지의 주요 내용이 아닌 부수적인 부분
  - <nav> : 사이트의 주된 탐색 메뉴
  - <section> : 주제별로 나누거나 묶는


  
### HTML ↔ 브라우저 / 화면 낭독기
  - HTML
  ```html
  <h1>A</h1>
  <article>
  	<h2>B</h1>
  	<section>
  		<h3>C</h1>
  	</section>
  </article>
  ```
  - 브라우저 / 화면 낭독기
  ```html
  - A
    - B
      - C
  ```
### 명시적 섹션
  - 헤딩과 함께 섹셔닝 콘텐츠를 사용하여 섹션의 범위를 명시적으로 알 수 있는 섹션
  ```html
  <h1>A</h1>
  <article>
  	<h2>B</h1>
  	<section>
  		<h3>C</h1>
  	</section>
  </article>
  ```
### 암시적 섹션
  - 섹셔닝 콘텐츠를 사용하지 않고 헤딩만을 사용하여 암시적으로 개요가 생성된 섹션
  ```html
  <h1>A</h1>
  <h2>B</h1>
  <h3>C</h1>
  ```
### 어색한 섹션
  - HTML
  ```html
  <body>
  	<p>A</p>
  	<article>
  		<h2>B</h1>
  	</article>
  </body>
  ```
  - 브라우저 / 화면 낭독기
  ```html
  - ?
    - B
  ```
### 헤딩이 없는 경우
  - HTML
  ```html
  <article>
    <p>A</p>
    <section>
      <p>B</p>
    </section>
  </article>
  ```
  - 브라우저 / 화면 낭독기
  ```html
  - ?
     - ?
  ```
