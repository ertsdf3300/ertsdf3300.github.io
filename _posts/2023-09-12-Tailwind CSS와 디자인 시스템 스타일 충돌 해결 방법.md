---
title: Tailwind CSS와 디자인 시스템 스타일 충돌 해결 방법
date: 2023-09-12 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Tailwind
  - CSS
---

## 문제 정의: 스타일 충돌 (Style Conflict)

Tailwind CSS는 유틸리티 기반의 CSS 프레임워크입니다. 그런데 때로는 기존의 디자인 시스템과 스타일이 충돌할 수 있습니다. 이 문제는 특히 프로젝트에 Tailwind CSS를 새로 도입하거나 기존 시스템과 통합할 때 발생할 수 있습니다.

## 해결책 1: 특성 범위 (Scope) 설정

Tailwind CSS의 설정 파일에서 `prefix` 옵션을 사용하여 Tailwind의 클래스 이름에 접두사를 추가할 수 있습니다. 이렇게 하면 Tailwind의 클래스가 기존 CSS와 충돌하는 것을 피할 수 있습니다. 

```javascript
// tailwind.config.js
module.exports = {
  prefix: 'tw-',
}
```

## 해결책 2: PurgeCSS 활용

PurgeCSS는 사용되지 않는 CSS를 제거해주는 도구입니다. Tailwind CSS와 함께 사용되면, 특정 컴포넌트나 라이브러리의 스타일을 무시하도록 설정할 수 있습니다. 

```javascript
// tailwind.config.js
module.exports = {
  purge: {
    options: {
      safelist: [/^your-class-name-/],
    },
  },
}
```

## 해결책 3: 레이어 (Layer) 활용

Tailwind CSS는 `base`, `components`, `utilities`라는 세 가지 레이어를 제공합니다. 이 레이어를 사용하여 기존 스타일보다 우선순위가 높거나 낮은 스타일을 적용할 수 있습니다.

```javascript
// tailwind.config.js
module.exports = {
  layerOrder: ['base', 'your-layer', 'components', 'utilities'],
}
```

## 예외 처리: `!important`

`!important`는 CSS에서 다른 스타일을 덮어쓸 때 사용하는 명령입니다. 그러나 이 방법은 마지막 수단으로 사용되어야 하며, 가능하면 피하는 것이 좋습니다. 왜냐하면 `!important`는 코드의 유지보수를 어렵게 만들기 때문입니다.

## 결론

Tailwind CSS와 기존 디자인 시스템의 스타일 충돌은 다양한 방법으로 해결할 수 있습니다. 이러한 해결책을 적용하면 프로젝트의 유지보수성을 높이고, 코드의 품질을 향상시킬 수 있습니다.