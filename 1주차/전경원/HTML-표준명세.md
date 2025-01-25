### HTML5 이전에 Block Container라고 부르던 대부분의 요소들은 주로 Flow Content라고 부르고, Inline Container라고 부르던 요소들은 Phrasing Content로 대부분 들어가게 되었음

<aside>

Block Container → Flow Content

Inline Container → Phrasing Content

</aside>

Flow, Phrasing 외에도 interactive, Embedded, Metadata, Heading, Sectioning과 같은 다양한 카테고리를 가지고 있음

### Flow Content : body에 포함할 수 있는 모든 요소 (base, style, title 요소를 제외한 나머지 모든 요소)
  - `a, abbr, address, article, aside, audio, b, bdi, bdo, blockquote, br, button, canvas, cite, code, data, datalist, del, details, dfn, dialog, div, dl, em, embed, fieldset, figure, footer, form, h1, h2, h3, h4, h5, h6, math, menu, meter, nav, noscript, object, ol, output, p, picture, pre, progress, q, ruby, s, samp, script, section, select, slot, small, span, strong, sub, sup, svg, table, template, textarea, time, u, ul, var, video, wbr, autonomous custom elements, text`

### Metadata Content : 주로 문서의 header 안에 들어가는 요소들로 콘텐츠와 문서를 구조화 하는 요소를 의미하고 다른 콘텐츠의 표시, 동작, 관계 등을 설정
  - `base, link, meta, noscript, script, style, template, title`
  - 일부 요소들 (`link, meta, noscript, script, template`)은 경우에 따라 Flow Content가 되기도 함
  - 실제 화면에 출력하는 요소들이 아니기 때문에 CSS에서는 브라우저가 `display:none;` 방식으로 화면에 표시
### Heading Content : Sectioning Content의 헤더로 Sectioning Content가 없어도 Heading Content가 있으면 암시적으로 섹션이 형성
  - `h1, h2, h3, h4, h5, h6, hgroup`
  - CSS에서는 브라우저가 `display: block;` 방식으로 화면에 표시

### Sectioning Content : 문서의 개요를 형성하며 헤딩, 헤더, 풋터의 범위가 되기도 함
  - `article, aside, nav, section`
  - 각 Sectioning Content는 암시적인 개요를 형성하고 Sectioning Content와 Heading Content를 함께 사용하면 명시적인 개요를 형성
    <aside>
    
    Sectioning Content → 암시적인 개요
    
    Sectioning Content + Heading Content → 명시적인 개요
    
    </aside>
    
    - CSS에서는 브라우저가 `display: block;` 방식으로 화면에 표시

### Phrasing Content : 예전에 Inline Container라고 부르던 요소들 대부분으로 구문 컨텐츠와 단락을 형성하는 콘텐츠
  - `a, abbr, audio, b, bdi, bdo, br, button, canvas, cite, code, data, datalist, del, dfn, em, embed, i, iframe, img, input, ins, kbd, label, map, mark, math, meter, noscript, object, output, picture, progress, q, ruby, s, samp, script, select, slot, small, span, strong, sub, sup, svg, template, textarea, time, u, var, video, wbr, autonomous custom elements, text`
  - Phrasing Content 요소들 중 `link, meta, noscript, script, template` 는 브라우저가 `display: block;` 으로 표시하고 나머지 요소들은 `display: inline | inline-block` 으로 표시

### Embedded Content : 외부 자원을 참조하는 컨텐츠로 HTML이나 CSS가 아닌 다른 이미지나 멀티미디어 요소들을 HTML에 삽입하고 싶을 때 필요한 요소들이 포함되어 있고, 모든 입베디드 콘텐츠는 구문 콘텐츠이다. 만약 외부 자원을 지원하지 않는 경우 재체 자원을 명시할 수 있음
  - `audio, canvas, embed, iframe, img, math, object, picture, svg, video`
  - CSS에서는 브라우저가 `display: inline | inline-block;` 방식으로 화면에 표시

### Interactive Content : 사용자와 상호 작용할 수 있는 콘텐츠로 입력 장치 (키보드, 마우스)로 조작할 수 있음
  - `a, audio, button, details, embed, iframe, img, input, label, select, textarea, video`
  - CSS에서는 브라우저가 `display: inline | inline-block;` 방식으로 화면에 표시

### Palpable Content : 비어있지 않은, 볼 수 있는 콘텐츠로 hidden 속성이 없음
  - `a, abbr, address, article, aside, b, bdi, bdo, blockquote, button, canvas, cite, code, data, details, dfn, div, em, embed, fieldset, figure, footer, form, h1, h2, h3, h4, h5, h6, header, hgroup, i, iframe, img, ins, kbd, label, main, map, mark, math, meter, nav, object, output, p, pre, progress, q, ruby, s, samp, section, select, small, span, strong, sub, sup, svg, table, textarea, time, u, var, video, autonomous custom elements`

### Script-supporting element : 화면에는 렌더링 되지 않지만 사용자에게 기능을 제공하는 요소
  - `script, template`

### Transparent Content Models : 투명 콘텐츠 모델로 부모의 콘텐츠 모델을 따르기 때문에 투명한 요소를 제거해도 부모와 자식 관계가 문법적으로 유효해야 함
  - `a, ins, del, object, video, audio, map, noscript, canvas`
