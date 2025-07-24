# 2025-css

CSS 학습 정리(25.07.24~)

## 1. CSS란?

CSS(Cascading Style Sheets)는 HTML 문서의 스타일과 레이아웃을 지정하는 언어입니다. 색상, 크기, 배치 등을 설정해 시각적인 웹페이지를 만들 수 있도록 도와줍니다.

### 1.1 CSS의 역사와 철학

- **등장 배경:** 1996년 W3C에서 CSS1 표준이 제정됨.
- **역할:** 구조(HTML)와 표현(CSS)을 분리해 일관성과 유지보수성 향상.
- **재사용:** 하나의 스타일시트를 여러 문서에 적용 가능.

### 1.2 Cascading(계단식) 의미

스타일이 여러 곳에서 정의되었을 경우, 우선순위에 따라 스타일이 적용되는 방식을 말합니다. CSS의 철학은 이러한 우선순위를 통해 유연하고 예측 가능한 스타일링을 가능하게 합니다.

## 2. CSS 작성과 문법

### 2.1 기본 문법

```css
selector {
  property: value;
}
```

- **선택자(selector)**: 스타일을 적용할 HTML 요소
- **속성(property)**: 변경할 스타일 종류
- **값(value)**: 적용할 스타일 값

### 2.2 CSS 속성

- CSS1은 약 50개의 속성으로 시작되었으나 현재는 350\~400여개로 확장됨
- [CSS 속성 목록 참고](https://www.cssportal.com/css-properties/index.php)
- [브라우저 호환성 확인 사이트](https://caniuse.com/)

### 2.3 위치

- 내부 스타일(`style`)과 외부 스타일(`link`)은 반드시 `<head>` 내부에 작성해야 브라우저 렌더링 성능이 향상됨

## 3. CSS 규칙과 구조

### 3.1 at-rule

CSS에서 `@`로 시작하는 특수 규칙들:

- `@charset`, `@import`, `@font-face`, `@media`, `@supports`, `@keyframes` 등

### 3.2 link vs @import

- `@import`는 모듈화에 유리하나, 성능 면에서는 `<link>`가 더 빠름
- 프로덕션 단계에서는 `<link>` 사용 권장

### 3.3 상속 제어 키워드

- `inherit`: 부모 값 상속
- `initial`: 초기값으로 설정
- `unset`: 상황에 따라 inherit 또는 initial 작동
- `revert`: 브라우저 기본 스타일로 복원

## 4. 선택자 정리

### 4.1 전체 선택자 (`*`)

모든 요소에 스타일 적용. 성능 저하를 유발할 수 있어 최소한 사용.

### 4.2 타입 선택자 (`태그명`)

특정 태그에 스타일 적용

```css
h1 {
  color: blue;
}
```

### 4.3 아이디 선택자 (`#id`)

문서 내에서 유일한 요소에 적용. 스타일링보다는 자바스크립트, 해시 링크에 사용 권장

### 4.4 클래스 선택자 (`.class`)

재사용 가능한 스타일 작성에 적합

```css
.text-bold {
  font-weight: bold;
}
```

### 4.5 속성 선택자 (`[attr]`)

속성을 기준으로 스타일 적용

```css
[title] {
  text-decoration: underline;
}
```

### 4.6 그룹 선택자 (`선택자1, 선택자2`)

중복 스타일 적용 시 유용

### 4.7 복합 선택자

- 자손 선택자: `section p`
- 자식 선택자: `section > p`
- 일반 형제: `section ~ p`
- 인접 형제: `section + p`

## 5. 선택자 우선순위

### 5.1 적용 우선순위 규칙

1. 중요성(`!important`)
2. 구체성(Specificity)
3. 후자 우선(뒤에 작성된 스타일 우선)

### 5.2 구체성 계산

| 선택자                | 가중치 |
| --------------------- | ------ |
| inline-style          | 1000   |
| id `#`                | 100    |
| class/속성/가상클래스 | 10     |
| 태그/가상요소         | 1      |
| 전체 선택자 `*`       | 0      |

### 5.3 !important

가장 우선 적용되며, 남용은 유지보수에 악영향을 줌. 제한적으로 사용.

## 6. 폰트와 텍스트 관련

### 6.1 currentColor

color 값을 다른 속성에 재사용

```css
border: 1px solid currentColor;
```

### 6.2 Generic Font Families

- serif, sans-serif, monospace, cursive, fantasy, system-ui 등

### 6.3 웹폰트 사용

```css
@font-face {
  font-family: "Pretendard";
  src: url("./fonts/Pretendard-Regular.woff") format("woff");
  font-weight: 400;
  font-style: normal;
}
```

- 한글, 영문 폰트 구분 필요 시: "영문", 한글, generic 순서로
- 공백 포함 글꼴명은 반드시 따옴표 사용

## 7. font-size 단위

### 7.1 px / em / rem

- px: 고정 크기
- em: 부모 요소 기준 상대 크기
- rem: 루트 요소 기준 상대 크기

```css
html {
  font-size: 62.5%; /* 16px * 62.5% = 10px */
}
body {
  font-size: 1.6rem; /* = 16px */
}
```

> 💡 일반적으로 rem 단위가 유지보수에 더 용이하여 많이 사용됨

## 8. 추천 학습 사이트

- [CSS Diner](https://flukeout.github.io/)
- [CSS Speedrun](https://css-speedrun.netlify.app/)
- [명시도 계산기](https://specificity.keegan.st/)
- [폰트 사이트 눈누](https://noonnu.cc/)
- [Google Fonts](https://fonts.google.com/)

---

> 작성일: 2025.07.24
> 학습자: 김채현
