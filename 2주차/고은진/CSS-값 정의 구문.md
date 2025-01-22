# CSS 값 정의 구문

<br />

## 결합기호 (Combinators)

| **기호** | **설명** | **예시** | **사용** |
| --- | --- | --- | --- |
| 공백 (and) | 둘 이상의 값이 필수, 순서 유지 필수 | `bold <length>, thin` |• `bold 1em, thin`<br/>• `bold 0, thin`<br/>• `bold 2.5cm, thin`<br/>• `bold 3vh, thin` |
| && (and) | 둘 이상의 값이 필수, 순서 변경 가능 | `bold && <length>` | • `bold 1em`<br/>• `bold 0`<br/>• `2.5cm bold`<br/>• `3vh bold`<br/><br/>*두 구성 요소는 한 번씩만 모두 나타나야 한다. |
| \|\| (or) | 두 값 중 하나 이상 필수, 순서 변경 가능 | `<'border-width'> \|\| <'border-style'> \|\| <'border-color'>` | • `1em solid blue`<br/>• `blue 1em`<br/>• `solid 1px yellow`<br/><br/>*하나의 구성 요소는 한 번만 나타나야 한다. `blue yellow`는 잘못된 사용 예시. |
| \| (only) | 두 값 중 하나만 | `<percentage> \| <length> \| left \| center \| right \| top \| bottom` | •`3%`<br/>• `0`<br/>• `3.5em`<br/>• `left`<br/>• `center`<br/>• `right`<br/>• `top`<br/>• `bottom`<br/><br/>*오직 하나의 구성 요소만 나타나야 한다. |
| [] (group) | 그룹 | `bold [ thin && <length>]` | • `bold thin 2vh`<br/>• `bold 0 thin`<br/>• `bold thin 3.5em`<br/><br/>*bold는 대괄호로 정의한 구성 요소와 병치했으므로 반드시 그 앞에 나타나야 한다. |

> 1 ~ 4는 우선 순위, 우선 순위가 높은 기호로 먼저 해석해야 한다.

<br />

## 증가기호 (Multipliers)

| **기호** | **설명** | **예시** | **사용** |
| --- | --- | --- | --- |
| * | 횟수 제한 없음, 0 ~ 무한으로 가능 | `bold smaller*` | • `bold`<br />• `bold smaller`<br />• `bold smaller smaller`<br />• `bold smaller smaller smaller`<br /><br />*bold는 병치이기 때문에 smaller 앞에 반드시 있어야 한다. |
| + | 1회 이상 | `bold smaller+`  | • `bold smaller`<br />• `bold smaller smaller`<br />• `bold smaller smaller smaller`<br /><br />*bold는 병치이기 때문에 smaller 앞에 반드시 있어야 한다. |
| ? | 0회 또는 1회 | `bold smaller?` | • `bold`<br />• `bold smaller`<br /><br />*bold는 병치이기 때문에 smaller 앞에 반드시 있어야 한다. |
| {N} | 정확히 N회 |  |  |
| {N1, N2} | 최소 N1회, 최대 N2회 | `bold smaller{1,3}` | • `bold smaller`<br />• `bold smaller smaller`<br />• `bold smaller smaller smaller`<br /><br />*smaller는 최대 3회까지만 나타나야 한다. |
| {N,} | 최소 N회 필요, 최대값 무제한 |  |  |
| # | 1회 이상, 값을 콤마(,)로 분리, 횟수 제한 가능 | `bold smaller#` | • `bold smaller`<br />• `bold smaller, smaller`<br />• `bold smaller, smaller, smaller`<br /><br />*bold는 병치이기 때문에 smaller 앞에 반드시 있어야 한다. |
| []! | 그룹에서 적어도 1회 이상 | `[bold? smaller?]!` | • `bold`<br />• `smaller`<br />• `bold smaller`<br /><br />*bold와 smaller는 단 한 번만 나타나야 한다. |

> 반복 제한 횟수보다 많은 값을 선언하면 무시된다.

> **CSS 명세 읽는 예시**
>
> ```css
> [<'font-style'>||<'font-weight'>]?<'font-size'>[/<'line-height'>]?<'font-family'>
> ```
>
> 그룹 뒤 물음표는 0 또는 1회만 사용하면 되므로 생략이 가능하다. 따라서 필수로 작성해야 하는 것은 `font-size`와 `font-family`
> 둘 사이에 공백이 있으므로 순서를 유지해서 작성한다.
>
> ```css
> font: 16px Sans-serif;
> font: bold 16px Sans-serif;
> font: bold italic 16px Sans-serif;
> font: italic bold 16px/24px Sans-serif;
> ```
