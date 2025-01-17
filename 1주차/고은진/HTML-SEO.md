# HTML과 SEO

<br />

## SEO란?

**검색 엔진 최적화(Search engine optimization, SEO)**, 즉 검색엔진에서 찾기 쉽도록 사이트를 개선하는 프로세스. 웹 페이지 검색엔진이 자료를 수집하고 순위를 매기는 방식에 맞게 웹 페이지를 구성해서 검색 결과의 상위에 나올 수 있도록 한다.

> 검색엔진에 친화적인 사이트를 구축하여 **광고가 아닌 자연 검색 결과**를 통해 트래픽의 양과 질을 극대화하는 작업.
> **검색 광고 최적화**가 아닌 **검색 엔진 최적화**

<br />

## SEO에 영향을 주는 요인들

- 검색 결과 페이지(SERP) 노출 대비 클릭률
  ![image](https://github.com/user-attachments/assets/34c18e06-ee20-479e-95ee-59d7c8861b15)
  > SERP에서 ‘광고’ 혹은 ‘Ad’라는 라벨이 붙어 상단에 노출되는 링크를 광고 검색 결과 (Paid Search Result)라 하며 그 밑에 노출되는 <mark>**비광고성 링크가 자연 검색 결과 (Organic Search Result)**</mark>
  >
  >자연 검색 결과는 소비자에게 더욱 연관성이 높고 신뢰가 가는 검색 결과로 보이므로 검색 광고(PPC)에 비해 더 많은 양의 클릭을 유도한다.
  >
- 백링크(backlink): 다른 웹 페이지로부터 인용(링크)되는 횟수
- 도메인 권력(Domain authority): 검색 결과 페이지 순위 예측 점수
- 페이지 타이틀
- 메타 디스크립션
- 로딩 속도
- SSL(https) 사용 여부
- 콘텐츠의 양, 질, 개연성
- 사용자 경험: LCP(최대 콘텐츠 블럭 그리기), CLS(누적 배치 변경)
  >**LCP (Largest Contentful Paint)**
  >사용자가 URL을 요청한 시점부터 페이지 내에서 시각적으로 가장 큰 콘텐츠를 그리는 데에 걸리는 시간
  >
  >**CLS (Cumulative Layout Shift)**
  >누적 레이아웃 변경. 페이지가 덜컥거리면서 로딩됨에 따라 측정되는 점수.
  >
  >**FID (First Input Delay)**
  >웹 페이지가 사용자의 동작(링크 클릭, 버튼 탭 등)에 반응할 때까지 걸리는 시간.

*위와 같은 다양한 요인들이 있지만 실제 어느 정도의 비율로 검색 결과에 반영 되는지는 검색 엔진에서 비밀로 유지하고 있어 정확히는 알 수 없다.

<br />

## 페이지 타이틀 (Page Title)

**페이지 타이틀 - Accessibility**

**화면 낭독기 사용자는 웹 페이지 접속 시 페이지 타이틀을 음성으로 전달 받는다**. 사용자는 음성으로 전달 받은 내용을 통해 본인이 원하는 페이지에 들어왔는지 빠르게 인지할 수 있다. 만약 페이지 타이틀에 모두 똑같은 내용의 텍스트를 집어 넣는다면 화면 낭독기 사용자는 해당 페이지가 자신이 찾는 페이지인지 확신할 수 없을 것이다.

화면 낭독기 사용자는 불필요한 정보들을 빠르게 건너뛰기 위해 보통 속청으로 들으므로 타이틀 내용은 **간결하게 중요한 키워드**만 집어넣는 것이 좋다.

<br />

**페이지 타이틀 - 구분자**

`-`, `|`, `:` 을 구분자로 사용한다.

```html
Page title - Site name Page title | Site name Page title : Site name
```

- **대시(-)** 사용 시 키워드 사이의 공간이 더 크므로 가독성이 좋다.
- **파이프(|), 클론(:)** 은 장평이 적으므로 공간을 더 효율적으로 사용할 수 있다.
- **언더바(\_)** 는 인접 키워드를 하나로 연결하므로 추천하지 않는다.

<br />

**페이지 타이틀 - JavaScript**

최근 검색 엔진들은 JavaScript에 의해 동적으로 생성된 페이지 타이틀도 잘 크롤링한다.

<br />

**페이지 타이틀 - 요약 정리**

- 본문을 가장 잘 설명하는 키워드 중심
- 페이지마다 구체적이고 고유한 키워드 사용
- 페이지마다 반복하는 키워드 최소화
- 구체적인 키워드를 앞으로 배치
- 가능한 짧게

<br />

## 메타데이터 (Metadata)

메타데이터는 데이터에 대한 데이터를 의미한다. 즉 **‘어떤 목적을 가지고 만들어진 데이터’** 로 정의할 수 있다.

```html
<!-- lang 속성은 검색 엔진이 특정 언어의 웹 페이지를 검색할 때 도움을 주기도 하고 또는 화면 낭독기 사용자들이 이 웹 페이지를 읽을 때 어떤 음성 엔진을 선택해야 하는지 힌트를 주기도 합니다. 하지만 구글에서는 현재 lang 속성을 신뢰하지 않습니다.-->
<html lang="ko">
  <head>
    <!-- charset="UTF-8" 설정을 통해 전 세계의 모든 국가의 언어를 이 웹 페이지에 문제없이 표시할 수 있습니다. 'UTF-8'이 표준입니다.-->
    <meta charset="UTF-8" />

    <!-- 검색 엔진의 검색 결과 화면에 노출되는 텍스트 (사이트에 대한 설명을 표기) -->
    <meta
      name="descripton"
      content="중고 거래부터 동네 정보까지, 이웃과 함께해요. 가깝고 따뜻한 당신의 근처를 만들어요."
    />

    <!-- 모바일 디바이스에서 이 웹 페이지가 모바일에서도 볼 수 있는지 , 즉 최적화 되어 있는지에 대한 정보를 검색 엔진에 제공-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <!-- 페이지 타이틀 -->
    <title>당신 근처의 당근마켓</title>
  </head>
</html>
```

![image](https://github.com/user-attachments/assets/d6cfe3b4-c176-42c3-97e8-5b2fd75ac51c)

<br />

**Metadata - Facebook**

```html
<meta property="og:url" content="https://*.html" />
<meta property="og:title" content="..." />
<meta property="og:description" content="..." />
<meta property="og:image" content="https://*.jpg" />
```

<br />

**Metadata - Twitter**

```html
<meta name="twitter:card" content="summary" />
<meta name="twitter:title" content="..." />
<meta name="twitter:description" content="..." />
<meta name="twitter:image" content="https://*.jpg" />
```

<br />

**Metadata - Naver**

```html
<html lang="ko">
  <head>
    ...
  </head>
  <body>
    <!-- 네이버 연관 채널에 등록하기 위한 'JSON-LD 형식'의 <script> 포맷의 JavaScript -->
    <script type="application/Id+json">
      {...}
    </script>
  </body>
</html>
```

\*body 종료 직전에 넣는 것을 추천.

![image](https://github.com/user-attachments/assets/ce7d02fd-5155-4a66-92a9-9a53e3e0169e)
