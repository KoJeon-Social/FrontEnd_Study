# Atomic & Utility First CSS 란?

- CSS 선언 컨셉 중 하나로 대표적으로 Tailwind CSS가 있고 아래와 같이 사용한다

![image](https://github.com/user-attachments/assets/297ec5df-28aa-4288-ace4-408406c75bbe)


### 예시

```html
<button
  class="w-1/2 flex items-center justify-center rounded-md bg-black text-white"
>
  Click
</button>
```

- 버튼이라는 클래스 하나를 디자인하기 위해서 유틸리티 클래스들을 위와 같이 여러 개 집어넣어서 조합하는 방식으로 디자인을 완성할 수 있다.
> 이런 형식으로 HTML의 유틸리티 클래스를 사용하게 되면 HTML과 CSS의 연결은 굉장히 강력해진다. 그래서 HTML을 작성하는 사람이 반드시 CSS 개발도 같이 진행해야 한다.

### 특징

- 라이브러리 타입으로 빠른 스타일 구축이 가능
- 다른 방법론과 함께 사용 가능
- 스타일 관점의 작명을 하여 의미론 사용 X
- HTML 코드에 스타일이 강하게 연결
- HTML/CSS 병렬 개발이 불가능, 그렇기에 소규모 팀 또는 단일 엔지니어 개발에 적합

### 장단점

장점

- 편안함과 빠른 개발
- 일관된 디자인
- 쉽고 자유로운 커스텀
- 로우 레벨의 스타일 제공
- JavaScript 코드와의 분리

단점

- 클린하지 못한 코드
- 클래스명 학습의 러닝 커브
- JavaScript 코드 사용 불가
- HTML/CSS 코드 혼재
