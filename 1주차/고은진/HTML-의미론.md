# HTML 의미론

> **시맨틱 태그**

HTML의 시맨틱 태그란 ‘의미론적인 태그’라는 뜻으로, 이름만으로도 해당 태그가 문서에서 어떤 역할을 하는지 쉽게 파악할 수 있는 태그를 말한다. HTML5 이전 버전의 HTML에서도 문단(<p>), 제목(<h>), 목록(<ul>과 <ol>) 등을 나타내는 의미론적인 태그들이 존재하고 있었지만 그 종류가 제한적이었다. 최신 웹 표준 HTML5에서는 이 점을 보완해 여러 종류의 시맨틱 태그를 추가했고, 사용 빈도는 증가하고 있다.

>

## <div>, <span> 요소의 의미

<div>, <span> 요소는 의미를 가지고 있지 않다. 만약 두 요소를 너무 많이 사용하고 있다면 HTML 태그를 적절하게 사용하지 않고 있다는 것이다. 따라서 <div>, <span>는 다른 적절한 HTML 요소를 사용할 수 없을 때 마지막으로 선택할 수 있는 태그다.

**<div> 요소를 대체할 만한 요소들**

`h1, h2, h3, h4, h5, p, ul, ol, li, dl, dt, dd, blockquote, pre, address, article, nav, section, hgroup, header, footer, main, figure, figcaption, details, summary, dialog, datalist …`

**<span> 요소를 대체할 만한 요소들**

`a, em, strong, label, q, sub, sup, ins, del, code, dfn, abbr, cite, kbd, ruby, samp, var, small, b, u, i, s, data, time, mark, output, meter, progress …`

## Sectioning

`article`, `aside`, `nav`, `section` 요소들이 해당된다. `hx`, `hgroup`, `header`, `footer` 요소들은 섹셔닝 요소는 아니지만 함께 쓰이는 요소다.

## 태그들의 역할

- `<header>`: 도입부, 헤딩, 헤딩 그룹, 목차, 검색, 로고
  - 검색 엔진의 검색에 참고가 되는 중요한 자료로써 사용되기도 한다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/5f7c1559-85b9-4f98-82c3-fcd9abc83e20/image.png)

- `<footer>`: 저자, 저작권, 연락처, 관련 문서

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/218b1477-a5b2-4f33-9ce1-01ff033b379c/image.png)

- `<section>`: 제목이 있는 주제별 콘텐츠 그룹 또는 응용 프로그램 영역
  - 결과 화면만 놓고 보면 <div> 태그와 아무런 차이가 없다. 하지만 <div> 태그는 내부에 포함된 요소들에 대해 아무런 정보도 나타내지 않는 반면 <section> 태그는 관련된 콘텐츠가 묶여 있음을 명시적으로 나타낸다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/0a973459-4cf0-4519-b888-275a3e31e53f/image.png)

> h1 ~ h6 요소를 포함하는 것을 권장한다. header, footer 요소를 사용하는 것은 선택 사항이다.

- `<article>`: 섹션 요소 중 독립적으로 사용 가능한 완결형 콘텐츠, 뉴스 기사, 블로그 본문, 사용자의 댓글 등
  - <section> 태그와 <article> 태그 모두 연관된 콘텐츠를 묶는 태그이지만 <article> 태그는 **‘독립적으로 사용할 수 있는’** 연관 콘텐츠를 묶는다는 점에서 <section> 보다 구체적인 내용을 담는다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/0c2ac246-6a88-45a8-8f19-b951d703bde8/image.png)

> h1 ~ h6 요소를 포함하는 것을 권장한다. header, footer 요소를 사용하는 것은 선택 사항이다.

- `<nav>`: 현재 사이트 또는 현재 페이지 일부를 링크하고 있는 주요 탐색 섹션

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/42ddd168-b968-4080-9fea-a774cd8b5fee/image.png)

> h1 ~ h6 요소를 포함하는 것을 권장한다. 사이트 또는 페이지의 주요 탐색 경로에 해당하지 않는 링크, 푸터의 약관, 저작권 고지와 같은 링크는 nav 요소로 적절하지 않다.

- `<aside>`: 페이지의 주된 내용과 관련이 약해 구분할 필요가 있는 섹션. 부수적인 콘텐츠, 관련 기사, 광고 등의 내용을 포함할 수 있다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/2134f9c3-b5f0-459b-990c-ebc7853c9912/image.png)

> h1 ~ h6 요소를 포함할 것을 권장한다.

- `<main>`:
  - 문서의 핵심 주제 또는 애플리케이션의 핵심 기능과 직접 관련 있는 콘텐츠 영역 의미
  - 페이지마다 반복되지 않는 내용을 포함해야 한다.
  - 섹셔닝 콘텐츠가 아니므로 hx, header, footer 요소의 범위와는 관련이 없다.
  - 하나의 페이지 안에서 하나의 main 요소만 표시할 수 있고 섹셔닝 관련 요소 (article, aside, nav, section, header, footer)의 자식이 될 수 없다.
  - body, div 요소를 제외한 다른 요소의 자손이 될 수 없다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/d08cf185-afae-4323-ac9a-866e9263b112/image.png)

- `<dialog>`: 사용자와 상호 작용하는 응용 프로그램(대화상자) 의미. open 속성을 추가하면 대화 상자가 활성화되고 사용자가 대화 상자를 통해 상호 작용할 수 있다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/01cd6876-336b-472b-9f50-3f1db104d4f9/image.png)

> 보통 입력 양식과 컨트롤을 포함하고 있으며 닫기 기능을 제공해야 한다. 또한 키보드 초점이 dialog 요소 내부에서 순환하도록 처리해야 한다.

- `<figure>`: 문서의 주된 흐름을 위해 참조하는 독립적인 완결형 요소로서 이미지, 도표, 코드 등의 내용물과 설명(figcaption)을 포함한다. 처음 또는 마지막에 figcaption 요소를 자식 요소로 포함하거나 생략할 수 있다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/350c26d9-61bf-4bff-bfa1-5a2e7e3790ea/image.png)

> figure 안에서 figcaption 선언 시 한 번만 선언할 수 있다.

- `<mark>`: 독자의 주의를 끌기 위한 하이라이트. 현재 독자의 행위나 관심에 따라 강조한 것이며 검색 결과 목록에서 사용자가 입력한 키워드를 나타낸다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/f44dd189-8eaa-4f31-8a98-caa38dfdcf2b/image.png)

- `<address>`: 문서나 글의 저자 또는 회사와 연락할 수 있는 정보를 명시할 때 사용한다. <body> 요소 안에 존재하는 <address> 요소는 해당 문서의 연락 정보를 나타내며, <article> 요소 안에 존재하는 <address> 요소는 해당 글에 대한 연락 정보를 나타낸다. 흔히 footer 요소에 나타난다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/73b4f274-05df-4709-873f-a087a65e7de1/image.png)

> p 요소의 자손이 될 수 없다.

- `<ins>, <del>`
  - `<ins>`: 추가한 내용
  - `<del>`: 삭제한 내용

> 콘텐츠 모델이 투명하므로 어떤 요소라도 포함할 수 있다. 단 여러 단락을 한꺼번에 포함하는 것은 부적절하다.

- `<progress>`: 계산 또는 사용자 과업의 진척도 의미. 원격 호스트의 응답을 기다려야 하는 경우도 있을 수 있으므로 진척도는 정확하지 않을 수 있다.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/bc413b2b-93fa-4510-8fbb-b6669f565979/image.png)

> value 값과 별도의 컨텐츠를 제공하는 것이 좋다.

- `<b>, <i>, <s>, <u>`
  과거에는 의미가 없는 요소였으나 현재 특별한 의미로 남아있는 요소들.
  - `<b>`: 부가적인 목적 없이 단순히 굵게 표현되는 텍스트 / `<strong>`: 요소를 고려할 것
    > HTML5에서 제목(heading)은 <h1>부터 <h6> 태그로, 강조된 텍스트는 <em> 태그로, 중요한 의미를 가지는 텍스트는 <strong> 태그로, 마지막으로 하이라이트된(highlighted) 텍스트는 <mark> 태그로 표현되어야 합니다.
    >
    > 따라서 위의 태그들에서 적절한 태그를 찾을 수 없을 때만 마지막 선택지로 <b> 태그를 사용해야 합니다.
  - `<i>`: 현재 맥락과 다른 분위기나 음성을 위한 텍스트 영역을 정의할 때 사용 / `<em>`
    > 다음과 같은 의미 요소(semantic element) 중에서 사용하기에 적당한 요소를 찾지 못했을 때만 <i> 요소를 사용할 수 있습니다.
    >
    > - <cite> : 창작물의 제목
    > - <dfn> : 용어(term)의 정의
    > - <em> : 강조된 텍스트
    > - <mark> : 하이라이트된(highlighted) 텍스트
    > - <strong> : 긴급하거나 중요한 텍스트
  - `<s>`: 정확하지 않거나 관련 없는 텍스트 / `<del>` 요소 사용하여 표현
  - `<u>`: 오타, 중국 고유명사 등의 표기 / `<ins>`
