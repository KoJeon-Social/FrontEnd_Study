## HTML 표준 명세

### 주요 HTML 콘텐츠 분류

---

HTML5 이전에 **Block Container**라고 부르던 대부분의 요소들은 주로 **Flow Content**라고 부르고 **Inline Container**라고 부르던 요소들은 **Phrasing Content**로 부르게 되었다.

**콘텐츠 모델이 생기면서 요소들 각자의 역할과 마크업 구조가 명확해졌다.**

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/1c9e7280-29d9-4d42-8a84-eefeff4c665d/272dc660-0a34-408e-b961-6423fe09479a/image.png)

Flow, Phrasing 이외에도 Interactive, Embedded, Metadata, Heading, Sectioning과 같은 다양한 카테고리를 가지고 있다.

### Flow Content

- body에 포함할 수 있는 모든 요소.
- base, style, title 요소를 제외한 나머지 모든 요소
- `a, abbr, address, article, aside, audio, b, bdi, bdo, blockquote, br, button, canvas, cite, code, data, datalist, del, details, dfn, dialog, div, dl, em, embed, fieldset, figure, footer, form, h1, h2, h3, h4, h5, h6, header, hgroup, hr, i, iframe, img, input, ins, kbd, label, map, mark, math, menu, meter, nav, noscript, object, ol, output, p, picture, pre, progress, q, ruby, s, samp, script, section, select, slot, small, span, strong, sub, sup, svg, table, template,textarea, time, u, ul, var, video, wbr, autonomous custom elements, text`

### Metadata Conent

- 주로 문서의 header 안에 들어가는 요소.
- 콘텐츠와 문서를 구조화 하는 요소를 의미하며 다른 콘텐츠의 표시, 동작, 관계 등을 설정한다.
- `base, link, meta, noscript, script, style, template, title`

\*\*일부 요소들 (link, meta, noscript, script, template)은 경우에 따라 Flow Content가 되기도 한다.

- 실제 화면에 출력하는 요소들이 아니기 때문에 CSS에서는 브라우저가 `display: none;` 방식으로 화면에 표시한다.

### Heading Content

- Sectioning Content의 헤더.
- Sectioning Content가 없어도 Heading Content가 있으면 암시적으로 섹션(문서의 개요)이 형성된다.
- `h1~h6, hgroup`
- CSS에서는 브라우저가 `display: block;` 방식으로 화면에 표시한다.

### Sectioning Content

- 문서의 개요를 형성한다. (대부분 HTML5에서 새롭게 추가된 요소다.)
- 헤딩, 헤더, 푸터의 범위를 정의한다.
- `article, aside, nav, section`
- 각 Sectioning Content는 암시적인 개요를 형성하고 Sectioning Content와 Heading Content를 함께 사용하면 명시적인 개요를 형성한다.
  **Sectioning Content ➜ 암시적인 개요**
  **Sectioning Content + Heading Content ➜ 명시적인 개요**
- `display: block;`으로 렌더링한다.

### Phrasing Content

- 이전에 Inline Container라고 부르던 요소들이 대부분 Phrasing Content다.
- 구문 컨텐츠와 단락을 형성하는 컨텐츠이다.
- `a, abbr, audio, b; bdi, bdo, br, button, canvas, cite, code, data, datalist, del, dfn, em, embed, i, iframe, img, input, ins, kbd, label, map, mark, math, meter, noscript, object, output, picture, progress, q, ruby, s, samp, script, select, slot, small, span, strong, sub, sup, svg, template, textarea, time, u, var, video, wbr, autonomous custom elements, text`
- Phrasing Content 요소들 중 `link, meta, noscript, script, template`는 브라우저가 `display: block;` 방식으로 화면에 표시하고 나머지 요소들은 `display: inline | inline-block;`으로 표시한다.

### Embedded Content

- 외부 자원을 참조하는 컨텐츠.
- HTML이나 CSS가 아닌 다른 이미지나 멀티미디어 요소들을 HTML에 삽입하고 싶을 때 필요한 요소들이 포함된다.
- 모든 임베디드 콘텐츠는 구문 콘텐츠다.
- 만약 외부 자원을 지원하지 않는 경우 임베디드 콘텐츠는 대체 콘텐츠를 가질 수 있다.
- `audio, canvas, embed, iframe, img, math, object, picture, svg, video`
- CSS에서는 브라우저가 `display: inline | inline-block;` 방식으로 화면에 표시한다.

### Interactive Content

- 사용자와 상호작용할 수 있는 콘텐츠. 따라서 입력 장치(키보드, 마우스)로 조작할 수 있다.
- `a, audio, button, details, embed, iframe, img, input, label, select, textarea, video`
- CSS에서는 브라우저가 `display: inline | inline-block;` 방식으로 화면에 표시한다.

### Palpable Content

- 비어 있지 않고 볼 수 있는 콘텐츠. 따라서 hidden 속성이 없다.
- 구체적으로 보여지고 들리는 등 사용자에게 감지가 되는 콘텐츠 요소로, 최소 하나 이상의 요소가 존재해야 하고 숨김 상태여서는 안된다.
- `a, abbr, address, article, aside, b, bdi, bdo, blockquote, button, canvas, cite, code, data, details, dfn, div, em, embed, fieldset, figure, footer, form, h1, h2, h3, h4, h5, h6, header, hgroup, i, iframe, img, ins, kbd, label, main, map, mark, math, meter, nav, object, output, p, pre, progress, q, ruby, s, samp, section, select, small, span, strong, sub, sup, svg, table, textarea, time, u, var, video, autonomous custom elements`

### Script-supporting element

- 화면에는 렌더링 되지 않지만 사용자에게 기능을 제공하는 요소
- `script, template`

### Transparent Content Models

- 부모 요소의 콘텐츠 모델을 따른다.
- 상위(부모, 조상) 요소의 콘텐츠 모델로 판단된다고 해서 투명 콘텐츠 모델이라 표현한다. 그렇기에 투명한 요소를 제거해도 부모와 자식 관계가 문법적으로 유효해야 한다.
- `a, ins, del, object, video, audio, map, noscript, canvas`
- 예제
  - 아래 예제처럼 “Apples”의 작성이 올바른지 확인하기 위해 콘텐츠 모델을 검사할 경우, `object`, `ins`, `map`, `a`는 모두 transparent 콘텐츠 모델이므로 상위 요소인 `p`에서 허용 여부를 확인한다. 이때, `p`는 텍스트나 문단을 의미하는 Phrasing 콘텐츠이기 때문에 텍스트인 “Apples”의 작성이 허용된다.
