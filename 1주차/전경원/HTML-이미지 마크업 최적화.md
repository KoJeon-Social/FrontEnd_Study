# 이미지 마크업 최적화

### 이미지 마크업 최적화로 얻을 수 있는 것
- 이미지 파일을 최적화시키고 이미지 마크업 `<picture>` 요소를 잘 활용한다면 이러한 이득을 얻어 올 수 있음
- 대표적으로 서버 비용 절약과 사용자 경험을 아주 작은 기법만으로도 크게 향상시킬 수 있다는 점이 있음

### 이미지 포맷 비교
- .jpg / .png : 모든 브라우저에서 지원하는 폴백 이미지
- .webp : jpg/png 대비 30~70% 수준의 용량      
     > 알파 채널, IE 미지원
      > 
- .avif : 저용량 + 고품질
        
  > 알파 채널, 크롬/삼성 인터넷 지원
        > 
- 효율적인 이미지 제공 로직
    
    ```jsx
    if ('avif'를 지원하면) {
      // 'avif' 이미지 포맷 파일 출력
    } else if ('webp'를 지원하면) {
      // 'webp' 이미지 포맷 파일 출력
    } else {
      // 'jpg' 이미지 포맷 파일 출력
    }
    ```
    
### `<picture>`  요소
  - type 분기
    
    ```jsx
    <picture>
      <source srcset="sample.avif" type="image/avif" />
      <source srcset="sample.webp" type="image/webp" />
      <img src="sample.jpg" alt="sample" />
    </picture>
    ```
    
    > 반드시 하나의 이미지만 화면에 표시함. 즉, 사용자 환경에 알맞은 최적의 이미지만 화면에 노출하는 기능 탐지를 `<picture>` 요소가 제공
    > 
    
    > `<picture>` `<source>` 요소들들은 화면에 출력되는 요소는 아님. 단지  `<img>` 의 소스를 제공하기 위한 요소
    > 
- media 분기
    
    ```jsx
    <picture>
      <source srcset="small-sample.webp" media="(max-width: 960px)" />
      <img src="large-sample.webp" alt="large sample" />
    </picture>
    ```
    
    > `<picture>` 요소는 media 해상도 구간을 이용해서 이미지를 분기할 수 있음
    > 
- `<picture>` `<img>` 요소 resolution 분기
    
    ```jsx
    <picture>
      <source srcset="2x.webp 2x, 1x.webp" type="image/webp" />
      <img srcset="2x.jpg 2x" src="1x.jpg" alt="sample" />
    </picture>
    
    ```
    
    > `<picture>` `<img>` 요소는 사용자의 해상도 resolution, 즉 해상력으로도 분기 가능
    > 

<aside>

요즘에는 **레티나 디스플레이**라고 부르는 고해상력을 가진 모니터 화면 또는 스마트폰 디스플레이들이 있다. 이런 레티나 디스플레이의 특징은 일반적인 이미지보다 두 배 더 큰 이미지를 제공해서 강제로 작게 리사이징한 다음에 화면에 출력하면 더 선명하게 보인다는 것이다. 그럴 때 레티나 디스플레이를 분기할 수 있는 값의 작성 방법이 바로 ‘2x’ 이다. 이렇게 작성하면 레티나 디스플레이 해상도에서만 이 소스를 다운로드해서 화면에 출력합니다.

</aside>

### `<img>` 요소의 성능
    
    ```jsx
    <img
      loading="lazy"    // 로딩 지연
      decoding="async"  // 디코딩 지연
      alt="sample"
    />
    ```
    
  - **loding=”lazy”** 속성을 사용하면 이미지를 지연 로딩
        
    > 웹 페이지를 화면에 출력할 때 보통 뷰포트 안에 보이는 이미지만 먼저 출력하고 뷰포트 아래쪽에 있는, 화면 바깥쪽의 보이지 않는 이미지들은 로딩하지 않는다. 로딩하거나 출력하지 않다가 사용자가 브라우저를 스크롤 해서 위로 올리면 아래쪽에 있는 이미지가 올라오면서 다운로드하기 시작하고 화면에 표시하기 시작하는 것이다. 이것을 **이미지 지연 로딩(lazy loading)** 이라고 한다.
        > 
    - **decoding=”async”** 속성을 사용하면 이미지 디코딩을 병렬로 처리
        
        > 이미지 외의 다른 콘텐츠가 웹 페이지에 빠르게 표시되는 것을 도와줌
        > 
### 이미지 요소 디버깅
![image](https://github.com/user-attachments/assets/f35678ee-eeb0-4375-8e2d-af825875cfa7)
    
  - 위와 같이 이미지 요소를 디버깅하면 이 이미지가 현재 어떤 소스를 선택해서 출력하고 있는지 알 수 있다.
    
![image](https://github.com/user-attachments/assets/b9766d79-2b1c-4948-a172-60eb0150566a)

    
### 내용 정리
- .avif 포맷을 제공하고 webp, jpg를 대체 수단으로 제공헤라
- `<picture>` `<source>` `<img>` 요소와 srcset, type, media 속성을 적극 활용해라
- 빠른 로딩 속도를 통해 UX를 개선하고 이미지 전송 비용을 절약해라
