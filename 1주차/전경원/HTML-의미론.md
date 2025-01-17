### `<div>` , `<span>` 요소의 의미

- 아무런 의미가 없음
- 만약 너무 많이 사용하고 있다면 그만큼 HTML 태그를 의미 적절하게 사용하지 않고 있다는 것으로 해석
- 다른 적절한 HTML 요소를 사용할 수 없을 때 마지막으로 선택할 수 있는 태그
- 요소를 대체할 만한 요소들
  - `h1~5, p, ul, ol, li, dl, dt, dd, blockquote, pre, address, article, nav, section, hgroup, header, footer, main, figure, figcaption, details, summary, dialog, datalist ...`
  - `a, em, strong, label, q, sub, sup, ins, del, code, dfn, abbr, cite, kbd, ruby, samp, var, small, b, u, i, s, data, time, mark, output, meter, progress ...`

### Sectioning

- `article, aside, nav, section` 요소들
- `hx, hgroup, header, footer` 요소들은 섹셔닝 요소는 아니지만 함께 쓰이는 요소

### 태그들의 역할

- `<header>` : 도입부, 헤딩, 헤딩 그룹, 목차, 검색, 로고
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/75d189ad-e8f0-4554-bd53-fff51814cb72/image.png)
  > 반드시 필요한 요소는 아니지만 이런 의미일 때 div 요소 대신 사용하는 것을 권장
- `<footer>` : 저자, 저작권, 연락처, 관련 문서
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/ba27720b-cb72-4d6f-a434-b2f15e46302f/image.png)
  > 반드시 필요한 요소는 아니지만 이런 의미일 때 div 요소 대신 사용하는 것을 권장
- `<section>` : 제목이 있는 주제별 콘텐츠 그룹 또는 응용 프로그램 영역
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/1bc31bf9-6190-4dc0-9dc2-78804841c119/image.png)
  > h1 ~ h6 요소를 포함하는 것을 강력하게 권장
  > header, footer 요소를 사용하는 것은 선택 사항
- `<article>` : 섹션 요소 중 독립적으로 배포 가능한 완결형 콘텐츠, 뉴스 기사, 블로그 본문, 사용자의 댓글 등
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/06f94f13-538a-4b00-899f-8f2d65ed377a/image.png)
  > h1 ~ h6 요소를 포함하는 것을 강력하게 권장
  > header, footer 요소를 사용하는 것은 선택 사항
- `<nav>` : 현재 사이트 또는 페이지 일부를 링크하고 있는 주요 탐색 섹션
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/0a65aa04-3998-48d6-82ec-45caba45c140/image.png)
  -
  > h1 ~ h6 요소를 <as것을 강력하게 권장
  > 사이트 또는 페이지의 주요 탐색 경로에 해당하지 않는 링크, 풋터의 약관, 저작권 고지 같은 링크는 nav 요소로 적절 X
- `<aside>` : 페이지의 주된 내용과 관련이 약해서 구분할 필요가 있는 섹션으로 부수적인 콘텐츠, 관련 기사, 관고 등의 내용 포함
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/0206a5ba-d770-4a47-b413-03f8eea0e367/image.png)
  -
  > h1 ~ h6 요소를 포함하는 것을 강력 권장
- `<main>`
  - 문서의 핵심 주제 또는 애플리케이션의 핵심 기능과 직접 관련 있는 콘텐츠 영역으로 페이지마다 반복되지 않는 내용을 포함
  - 섹셔닝 콘텐츠가 아니므로 hx, header, footer 요소의 범위와는 관련 X
  - 하나의 페이지 안에서 하나의 main 요소만 표시할 수 있고 섹셔닝 관련 요소의 자식이 될 수 없음
  - body, div 요소를 제외한 다른 요소의 자손이 될 수 없음
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/ef44bbc2-4bd5-47f6-8760-7eb70343b9ee/image.png)
- `<dialog>`
  - 사용자와 상호 작용하는 응용프로그램 (대화 상자)
  - open 속성을 추가하면 대화 상자가 활성화되고 사용자가 대화 상자를 통해 상호 작용
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/e44f244e-3223-4038-8edf-ab029a5e971b/image.png)
  -
  > 보통 입력 양식과 컨트롤을 포함하고 있으며 닫기 기능 제공해야함. 그리고 키보드 초점이 dialog 요소 내부에서 순환하도록 처리
- `<figure>`
  - 문서의 주된 흐름을 위해 참조하는 독립적인 완결형 요소로서 이미지, 도표, 코드 등의 내용물과 설명을 포함
  - 선택적으로 처음 또는 마지막에 figcaption 요소를 자식 요소로 포함할 수 있고 또는 생략할 수 있음
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/87181636-598f-41ed-b02d-d49d009ef323/image.png)
  > figure 안에서 figcaption 요소가 선언된다면 한 번만 선언 가능
- `<mark>`
  - 독자의 주의를 끌기 위한 하이라이트
  - 현재 독자의 행위나 관심에 따라 강조한 것이며 검색 결과 목록에서 사용자가 입력한 키워드를 나타냄
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/4357efd2-59e4-4f24-9dac-19989790e247/image.png)
- `<address>`
  - 가까운 조상 article 또는 body 요소를 범위로 하는 관련 연락처 정보 우편 정보를 의미하는 것이 아님에 유의 (흔히 footer 요소에 나타남)
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/83ab40ae-b3c8-4463-a0f1-2b0a04d4d6f4/image.png)
  -
  > p 요소의 자손이 될 수 X
- `<ins>, <del>`
  - 각각 추가 / 삭제한 내용을 의미
  > 콘텐츠 모델이 투명해서 어떤 요소라도 포함할 수 있습니다. 단 여러 단락을 한꺼번에 포함하는 것은 부적절
- `<progress>`
  - 계산 또는 사용자 과업의 진척도
  - 원격 호스트의 응답을 기다려야 하는 경우도 있을 수 있기 때문에 진척도는 정확하지 않을 수 있음
  ![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/29f67a0d-cdfb-41bc-ba0a-5aa0b4aaac8a/1adcf1b2-139e-49a2-8766-f4e620bad86b/image.png)
  -
  > 낡은 브라우저를 위해 value 값과 별도로 콘텐츠를 제공하는 것이 좋음
- `<b>, <i>, <s>, <u>`
  - 과거에는 의미가 없는 요소였으나 현재 특별한 의미로 남아있는 요소들
  - `<b>` : 강조할 의도가 없는 볼드 / `<strong>` : 요소를 고려할 것
  - `<i>` : 현재 맥락과 다른 분위기 / `<em>` : 요소를 고려할 것
  - `<s>` : 정확하지 않거나 관련 없는 / `<del>` : 요소를 고려할 것
  - `<u>` : 오타, 중국 고유명사 등의 표기 / `<ins>` : 요소를 고려할 것
