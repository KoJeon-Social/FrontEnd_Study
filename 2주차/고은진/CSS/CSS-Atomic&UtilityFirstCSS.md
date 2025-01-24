# Atomic & Utility First CSS

<br />

## Atomic & Utility First CSS란?

Atomic & Utility First CSS란 CSS 선언 컨셉 중 하나로, 해당 컨셉으로 설계된 대표적인 CSS 라이브러리는 **Tailwind CSS**가 있다.

![Image](https://github.com/user-attachments/assets/9ab32ee6-1db0-425b-a963-9cbd5b049bbc)

```html
<button
  class="w-1/2 flex items-center justify-center rounded-md bg-black text-white"
>
  Click
</button>
```

위와 같이 버튼이라는 클래스를 디자인하기 위해 유틸리티 클래스들을 여러 개 집어 넣어 조합하는 방식으로 완성할 수 있다.

이러한 형식으로 HTML의 유틸리티 클래스를 사용하면 HTML과 CSS의 연결은 강력해진다. 따라서 HTML을 작성할 경우 CSS 개발도 함께 진행해야 한다.

<br />

## Atomic & Utility First CSS의 특징

1. 라이브러리 타입으로 빠른 스타일 구축이 가능하다.
2. 다른 방법론과 함께 사용할 수 있다.
3. 스타일 관점의 작명을 하여 의미론을 사용하지 않는다.
4. HTML 코드에 스타일이 강하게 연결된다.
5. HTML/CSS 병렬 개발이 불가능하다. 그렇기에 소규모 팀 또는 단일 엔지니어 개발에 적합하다.

<br />

## Atomic & Utility First CSS의 장단점

| 장점                                                                                                                                      | 단점                                                                                                                   |
| :---------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------- |
| 1. 편리함과 빠른 개발<br />2. 일관된 디자인<br />3. 쉽고 자유로운 커스텀<br />4. 로우 레벨의 스타일 제공<br />5. JavaScript 코드와의 분리 | 1. 클린하지 못한 코드<br />2. 클래스명 학습의 러닝 커브<br />3. JavaScript 코드 사용 불가<br />4. HTML과 CSS 코드 혼재 |
