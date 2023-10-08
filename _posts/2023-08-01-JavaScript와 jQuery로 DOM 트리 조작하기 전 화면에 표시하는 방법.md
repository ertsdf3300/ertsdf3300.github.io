---
title: JavaScript와 jQuery로 DOM 트리 조작하기 전 화면에 표시하는 방법
date: 2023-08-01 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트
  - JQUERY
---

## DOM 트리란 무엇인가?

DOM(Document Object Model) 트리는 웹 페이지의 구조를 표현하는 모델입니다. 웹 페이지의 모든 요소와 속성, 텍스트 등이 DOM 트리의 노드로 표현됩니다. 여기서 '노드'는 웹 페이지의 개별 구성 요소를 의미합니다. 

## 화면에 표시되기 전 DOM 트리 조작의 필요성

웹 페이지가 로딩될 때, 사용자에게 보이기 전에 DOM 트리를 수정하거나 조작하는 것이 유용한 경우가 많습니다. 예를 들어, 브라우저가 페이지를 완전히 불러오기 전에 특정 요소를 숨기거나, 스타일을 미리 적용해야 할 때가 있습니다.

## `DOMContentLoaded` 이벤트 사용하기

`DOMContentLoaded` 이벤트는 HTML 문서가 완전히 로딩되고 DOM 트리가 완성되었을 때 발생합니다. 이 이벤트를 이용하면 화면에 표시되기 전에 DOM을 조작할 수 있습니다. 

```javascript
document.addEventListener('DOMContentLoaded', function() {
    // DOM 조작 코드
});
```

## jQuery `$(document).ready()` 메소드 활용

jQuery를 사용하고 있다면 `$(document).ready()` 메소드를 사용할 수 있습니다. 이 메소드는 DOM이 준비되면 지정한 함수를 실행합니다.

```javascript
$(document).ready(function() {
    // DOM 조작 코드
});
```

## 주의 사항: `$(window).load()`와의 차이점

`$(window).load()`는 모든 리소스(이미지, 스크립트 등)가 로딩된 후에 실행됩니다. 따라서 DOM만 조작하려면 `$(document).ready()`나 `DOMContentLoaded` 이벤트를 사용하는 것이 더 효율적입니다.

## 결론

화면에 표시되기 전에 DOM 트리를 조작하는 것은 웹 개발에서 중요한 작업 중 하나입니다. JavaScript의 `DOMContentLoaded` 이벤트나 jQuery의 `$(document).ready()` 메소드를 활용하여 이 작업을 수행할 수 있습니다. 이를 통해 더 빠른 페이지 로딩과 사용자 경험을 제공할 수 있습니다.