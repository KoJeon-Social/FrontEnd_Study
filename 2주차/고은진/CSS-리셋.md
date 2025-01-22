# CSS 리셋

## CSS 리셋이란?

각 브라우저마다 HTML 요소에 설정되어 있는 기본 스타일이 존재한다. 브라우저마다 설정되어 있는 스타일은 조금씩 다르며 이는 크로스 브라우징을 방해한다. 이러한 점을 개선하기 위해 **CSS 스타일 속성을 초기화** 해야 한다.

![Image](https://github.com/user-attachments/assets/58590fbe-c15a-4d9c-a531-929b7d0f9ed1)

<br />

**크로스 브라우징(Cross Browsing)**

웹 표준 기술을 사용하여 다른 기종/플랫폼/브라우저에 따라 어느 한쪽에 최적화 되어 치우치지 않도록 공통 요소를 사용하여 웹 페이지를 제작하는 기법이다.
즉 어느 브라우저 또는 기기를 사용하든 웹 사이트가 동일하게 보여지고 작동되도록 하는 기법이다.

![Image](https://github.com/user-attachments/assets/223558a8-a47a-4fa3-9890-a83cf5f646e5)

> **user agent stylesheet**
>
> ![Image](https://github.com/user-attachments/assets/d2d0ffe7-0109-488d-a117-d09c5af94772)
>
> 위의 예시와 같이 img에 별도의 CSS를 주지 않았는데 user agent stylesheet이 적용되는 경우가 있다.
> user agent stylesheet란 <mark>사용자 에이전트/브라우저에서 기본스타일을 제공하는 기본 스타일시트</mark>로, 모든 문서에 존재한다.
>
> **Origin 우선순위**
>
> Origin은 어떤 원천으로부터 적용되었는지, CSS 규칙이 어디서 왔는지를 의미한다. CSS를 제공하는 곳으로 이해할 수 있으며 다음과 같다.
>
> **1. User Agent Stylesheet**
>
> - 사용자 에이전트나 브라우저에 기본적으로 내장된 스타일시트를 말한다.
> - 브라우저마다 기본 스타일이 조금씩 다르기 때문에 퍼블리싱 할 때 `normalize.css`나 `reset.css` 처럼 공통 속성을 재정의하는 css를 작성하곤 한다.
>
> **2. Author Stylesheet**
>
> - 가장 일반적인 유형의 CSS로 웹 개발자가 작성한 스타일시트를 말한다.
> - link로 import 해서 사용하거나, `<style>` 블록에서 사용하거나, 인라인 스타일로 작성된 스타일시트를 모두 포함한다.
>
> **3. User Stylesheet**
>
> - 개발자가 아닌 웹 사이트 사용자가 설정하는 스타일시트를 말한다.
> - 일부 사용자는 시각적 불편을 줄이기 위한 목적 등으로 자신만의 스타일시트를 브라우저에 적용할 수 있다.
>
> Origin에 따른 일반적인 CSS 우선순위는 다음과 같다.
>
> **Author Stylesheet > User Stylesheet > User Agent Stylesheet**
>
> 만일 `!important`가 포함된 속성이라면 우선순위는 다음과 같다.
>
> **User Agent Stylesheet > User Stylesheet > Author Stylesheet**
>
> **CSS의 Cascading**
>
> CSS는 **Cascading Style Sheets**의 약자로, CSS의 네이밍에서부터 녹아 있는 캐스캐이딩 개념은 스타일 규칙이 계단식으로 적용되는 방식을 말한다.
>
> CSS는 스타일을 적용하는 과정에서 캐스캐이딩 알고리즘을 사용하여 스타일 규칙의 우선순위를 결정한다.
>
> 이 과정에서 Origin, Specification, 스타일 적용 방법 등을 고려하여 우선순위를 판단한다.
>
> 캐스캐이딩의 전체 과정은 다음과 같다.
>
> 1. 스타일 규칙과 요소가 매치되었는지를 검사하여 해당 요소와 **관련된** 스타일 속성만 선별한다.
> 2. **Origin** 및 `!important` 속성에 따른 우선순위
>    - User Agent vs. Author vs. User stylesheet 간 우선순위를 판별한다.
>    - `!important` 속성 사용 여부에 따라 우선순위가 달라질 수 있다.
> 3. **Specification** 우선순위
>    - ID 카테고리 > CLASS 카테고리 > TYPE 카테고리 순으로 우선순위가 정해진다.
> 4. **작성 순서**
>    - 같은 요소에 동일한 속성이 선언되었을 경우, 나중에 선언된 스타일이 적용된다.

<br />

## CSS 리셋 방법

**reset.css**

- HTML 파일에 `link` 태그를 이용하는 방법

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/reset-css@5.0.1/reset.min.css"
/>
```

- CSS 파일에 직접 적용하는 방법

```css
/* http://meyerweb.com/eric/tools/css/reset/
   v2.0 | 20110126
   License: none (public domain)
*/

html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}
body {
  line-height: 1;
}
ol,
ul {
  list-style: none;
}
blockquote,
q {
  quotes: none;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
```

> https://meyerweb.com/eric/tools/css/reset/

**normalize.css**

- HTML 파일에 link 태그를 이용하는 방법

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/normalize.css@8.0.1/normalize.min.css"
/>
```

- CSS 파일에 직접 적용하는 방법

```css
/*! normalize.css v8.0.1 | MIT License | github.com/necolas/normalize.css */

/* Document
   ========================================================================== */

/**
 * 1. Correct the line height in all browsers.
 * 2. Prevent adjustments of font size after orientation changes in iOS.
 */

html {
  line-height: 1.15; /* 1 */
  -webkit-text-size-adjust: 100%; /* 2 */
}

/* Sections
   ========================================================================== */

/**
 * Remove the margin in all browsers.
 */

body {
  margin: 0;
}

/**
 * Render the `main` element consistently in IE.
 */

main {
  display: block;
}

/**
 * Correct the font size and margin on `h1` elements within `section` and
 * `article` contexts in Chrome, Firefox, and Safari.
 */

h1 {
  font-size: 2em;
  margin: 0.67em 0;
}

/* Grouping content
   ========================================================================== */

/**
 * 1. Add the correct box sizing in Firefox.
 * 2. Show the overflow in Edge and IE.
 */

hr {
  box-sizing: content-box; /* 1 */
  height: 0; /* 1 */
  overflow: visible; /* 2 */
}

/**
 * 1. Correct the inheritance and scaling of font size in all browsers.
 * 2. Correct the odd `em` font sizing in all browsers.
 */

pre {
  font-family: monospace, monospace; /* 1 */
  font-size: 1em; /* 2 */
}

/* Text-level semantics
   ========================================================================== */

/**
 * Remove the gray background on active links in IE 10.
 */

a {
  background-color: transparent;
}

/**
 * 1. Remove the bottom border in Chrome 57-
 * 2. Add the correct text decoration in Chrome, Edge, IE, Opera, and Safari.
 */

abbr[title] {
  border-bottom: none; /* 1 */
  text-decoration: underline; /* 2 */
  text-decoration: underline dotted; /* 2 */
}

/**
 * Add the correct font weight in Chrome, Edge, and Safari.
 */

b,
strong {
  font-weight: bolder;
}

/**
 * 1. Correct the inheritance and scaling of font size in all browsers.
 * 2. Correct the odd `em` font sizing in all browsers.
 */

code,
kbd,
samp {
  font-family: monospace, monospace; /* 1 */
  font-size: 1em; /* 2 */
}

/**
 * Add the correct font size in all browsers.
 */

small {
  font-size: 80%;
}

/**
 * Prevent `sub` and `sup` elements from affecting the line height in
 * all browsers.
 */

sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}

sub {
  bottom: -0.25em;
}

sup {
  top: -0.5em;
}

/* Embedded content
   ========================================================================== */

/**
 * Remove the border on images inside links in IE 10.
 */

img {
  border-style: none;
}

/* Forms
   ========================================================================== */

/**
 * 1. Change the font styles in all browsers.
 * 2. Remove the margin in Firefox and Safari.
 */

button,
input,
optgroup,
select,
textarea {
  font-family: inherit; /* 1 */
  font-size: 100%; /* 1 */
  line-height: 1.15; /* 1 */
  margin: 0; /* 2 */
}

/**
 * Show the overflow in IE.
 * 1. Show the overflow in Edge.
 */

button,
input {
  /* 1 */
  overflow: visible;
}

/**
 * Remove the inheritance of text transform in Edge, Firefox, and IE.
 * 1. Remove the inheritance of text transform in Firefox.
 */

button,
select {
  /* 1 */
  text-transform: none;
}

/**
 * Correct the inability to style clickable types in iOS and Safari.
 */

button,
[type="button"],
[type="reset"],
[type="submit"] {
  -webkit-appearance: button;
}

/**
 * Remove the inner border and padding in Firefox.
 */

button::-moz-focus-inner,
[type="button"]::-moz-focus-inner,
[type="reset"]::-moz-focus-inner,
[type="submit"]::-moz-focus-inner {
  border-style: none;
  padding: 0;
}

/**
 * Restore the focus styles unset by the previous rule.
 */

button:-moz-focusring,
[type="button"]:-moz-focusring,
[type="reset"]:-moz-focusring,
[type="submit"]:-moz-focusring {
  outline: 1px dotted ButtonText;
}

/**
 * Correct the padding in Firefox.
 */

fieldset {
  padding: 0.35em 0.75em 0.625em;
}

/**
 * 1. Correct the text wrapping in Edge and IE.
 * 2. Correct the color inheritance from `fieldset` elements in IE.
 * 3. Remove the padding so developers are not caught out when they zero out
 *    `fieldset` elements in all browsers.
 */

legend {
  box-sizing: border-box; /* 1 */
  color: inherit; /* 2 */
  display: table; /* 1 */
  max-width: 100%; /* 1 */
  padding: 0; /* 3 */
  white-space: normal; /* 1 */
}

/**
 * Add the correct vertical alignment in Chrome, Firefox, and Opera.
 */

progress {
  vertical-align: baseline;
}

/**
 * Remove the default vertical scrollbar in IE 10+.
 */

textarea {
  overflow: auto;
}

/**
 * 1. Add the correct box sizing in IE 10.
 * 2. Remove the padding in IE 10.
 */

[type="checkbox"],
[type="radio"] {
  box-sizing: border-box; /* 1 */
  padding: 0; /* 2 */
}

/**
 * Correct the cursor style of increment and decrement buttons in Chrome.
 */

[type="number"]::-webkit-inner-spin-button,
[type="number"]::-webkit-outer-spin-button {
  height: auto;
}

/**
 * 1. Correct the odd appearance in Chrome and Safari.
 * 2. Correct the outline style in Safari.
 */

[type="search"] {
  -webkit-appearance: textfield; /* 1 */
  outline-offset: -2px; /* 2 */
}

/**
 * Remove the inner padding in Chrome and Safari on macOS.
 */

[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}

/**
 * 1. Correct the inability to style clickable types in iOS and Safari.
 * 2. Change font properties to `inherit` in Safari.
 */

::-webkit-file-upload-button {
  -webkit-appearance: button; /* 1 */
  font: inherit; /* 2 */
}

/* Interactive
   ========================================================================== */

/*
 * Add the correct display in Edge, IE 10+, and Firefox.
 */

details {
  display: block;
}

/*
 * Add the correct display in all browsers.
 */

summary {
  display: list-item;
}

/* Misc
   ========================================================================== */

/**
 * Add the correct display in IE 10+.
 */

template {
  display: none;
}

/**
 * Add the correct display in IE 10.
 */

[hidden] {
  display: none;
}
```

> https://github.com/necolas/normalize.css

<br />

## reset.css와 normalize.css의 차이점

**reset.css**는 아예 완전히 백지 상태로 초기화시켜 사용하는 스타일 시트인 반면 **normalize.css**는 기존의 브라우저별 스타일을 모두 리셋시키는 방법이 아닌, 이를 유지하고 이용하려는 스타일 시트다.

<br />

## CSS 리셋의 문제점

reset 스타일 시트와 normalize 스타일 시트의 경우 현재 시점에서 굳이 선언하지 않아도 되는 스타일이 대부분이다. 따라서 **Unused CSS**, **Overridden CSS**가 발생한다. 즉 사용되지 않거나 또는 그냥 덮어쓰기 되어 버리는 스타일들이 생기는 문제가 발생한다.
