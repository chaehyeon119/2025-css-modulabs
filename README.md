# 2025 CSS Guide

> ✍️ **Author:** 김채현
> 📅 **Date:** 2025.07.24 ~
> 🎓 **Bootcamp:** 모두의연구소 프론트엔드 스쿨

---

## 📘 Overview

CSS(Cascading Style Sheets)는 HTML 문서의 스타일과 레이아웃을 정의하는 언어입니다. 색상, 크기, 여백, 폰트 등 시각적 요소를 조정하여 웹페이지를 아름답게 만들 수 있습니다.

---

## 📗 1. What is CSS?

### 1.1 CSS의 역사와 철학

- 🎉 **출시:** 1996년 W3C에서 CSS1 표준 제정
- 🔄 **목표:** HTML 구조와 시각 표현 분리
- ♻️ **장점:** 유지보수 용이, 재사용 가능, 일관성 유지

### 1.2 Cascading(계단식)의 의미

스타일이 충돌할 때 우선순위를 따져 적용되며, 이를 통해 예측 가능한 스타일링이 가능합니다.

---

## 📘 2. CSS Syntax & 작성 위치

### 2.1 기본 문법

```css
selector {
  property: value;
}
```

- `selector`: HTML 요소 선택자
- `property`: 스타일 속성
- `value`: 속성에 적용할 값

### 2.2 위치

- `<head>` 내부에 `<link>` 또는 `<style>` 작성 권장 → 렌더링 최적화

### 2.3 CSS 속성 참고

- 📚 [CSS 속성 목록](https://www.cssportal.com/css-properties/index.php)
- 🌐 [브라우저 호환성](https://caniuse.com/)

---

## 📙 3. CSS 구조 및 지시문

### 3.1 At-rules

- `@import`, `@font-face`, `@media`, `@keyframes`, `@supports`, `@charset` 등

### 3.2 link vs @import

- `@import`: 모듈화에 유리하나 성능 불리
- `<link>`: 렌더링 우선 적용, 프로덕션 추천

### 3.3 상속 제어 키워드

- `inherit`, `initial`, `unset`, `revert`

---

## 📒 4. 선택자 정리

### 4.1 전체 선택자 `*`

```css
* {
  margin: 0;
  padding: 0;
}
```

- 모든 요소에 스타일 적용 (주의: 성능 저하)

### 4.2 타입 선택자 `태그명`

```css
h1 {
  color: blue;
}
```

### 4.3 ID 선택자 `#id`

```css
#header {
  background: gray;
}
```

### 4.4 클래스 선택자 `.class`

```css
.text-bold {
  font-weight: bold;
}
```

### 4.5 속성 선택자 `[attr]`

속성을 기준으로 특정 요소를 선택합니다.

```css
[title] {
  border-bottom: 2px dotted #333;
}
[class="text"] {
  color: lime;
}
[class*="text"] {
  background: pink;
}
```

예시 HTML:

```html
<p title="Hello" class="text title">This paragraph has a title.</p>
<p class="text">This paragraph doesn't have a title.</p>
<a href="#" title="Link" class="link title">This is a link</a>
```

### 4.6 그룹 선택자

```css
h1,
h2,
h3 {
  font-family: sans-serif;
}
```

### 4.7 복합 선택자

```css
section p      /* 자손 */
section > p    /* 자식 */
section + p    /* 인접 형제 */
section ~ p    /* 일반 형제 */
```

---

## 📕 5. 선택자 우선순위 (Specificity)

### 5.1 적용 우선순위

1. `!important`
2. 구체성(Specificity)
3. 작성 순서 (후자 우선)

### 5.2 구체성 계산표

| 선택자 유형             | 점수 |
| ----------------------- | ---- |
| 인라인 스타일           | 1000 |
| ID 선택자 `#id`         | 100  |
| 클래스/속성/가상 클래스 | 10   |
| 태그/가상 요소          | 1    |
| 전체 선택자 `*`         | 0    |

### 5.3 `!important`

가장 높은 우선순위를 가지지만 남용 시 유지보수 악화.

---

## 🎨 6. 폰트 & 텍스트

### 6.1 `currentColor`

```css
border: 1px solid currentColor;
```

- color 값을 다른 속성에 재활용할 수 있음

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

- 한글과 영문 혼용 시: `'영문 폰트', '한글 폰트', generic`
- 공백 포함 글꼴은 반드시 따옴표로 감싸야 함

---

## 🔠 7. Font Size 단위

### 7.1 px / em / rem 비교

```css
html {
  font-size: 62.5%; /* = 10px if 기본 16px */
}
body {
  font-size: 1.6rem; /* = 16px */
}
```

- `px`: 고정
- `em`: 부모 기준
- `rem`: root 기준 (권장)

💡 유지보수를 고려할 때 `rem` 사용이 유리

---

## 🔗 8. 참고 사이트

- 🍽️ [CSS Diner](https://flukeout.github.io/)
- 🏃 [CSS Speedrun](https://css-speedrun.netlify.app/)
- 📊 [명시도 계산기](https://specificity.keegan.st/)
- ✍️ [눈누 한글 폰트](https://noonnu.cc/)
- 🔤 [Google Fonts](https://fonts.google.com/)


<img width="714" height="1125" alt="image" src="https://github.com/user-attachments/assets/76bde055-9e27-4eaf-b18c-63dc66113a78" />

---
