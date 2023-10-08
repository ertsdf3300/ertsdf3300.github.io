---
title: iOS Safari 확장 프로그램의 상단 바 숨기기
date: 2023-09-11 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Safari
  - 확장프로그램
---
## 문제점과 해결 방안 소개

iOS Safari 확장 프로그램을 사용하면서 상단 바를 숨기고 싶은 경우가 많이 있습니다. 상단 바가 화면 공간을 차지하거나 디자인에 방해가 되기 때문입니다. 이 문제를 해결하기 위한 방법을 아래에서 자세히 설명하겠습니다.

## HTML과 CSS를 이용한 상단 바 숨기기

하나의 방법은 HTML과 CSS를 이용하는 것입니다. HTML 파일에서 상단 바에 해당하는 부분을 찾아서 CSS로 `display: none;` 속성을 추가합니다. 이렇게 하면 상단 바가 렌더링되지 않을 것입니다.

```html
<div id="top-bar"> ... </div>

<style>
  #top-bar {
    display: none;
  }
</style>
```

렌더링(화면에 그려지는 것)은 사용자가 웹 페이지를 보는 것을 가능하게 하는 과정입니다.

## JavaScript를 이용한 동적 처리

또 다른 방법은 JavaScript를 이용하는 것입니다. 특정 상황에서만 상단 바를 숨기고 싶다면 JavaScript를 이용해 조건에 따라 동적으로 상단 바를 숨길 수 있습니다.

```javascript
if (someCondition) {
  document.getElementById("top-bar").style.display = "none";
}
```

동적으로는 '실행 중에 변할 수 있는'이라는 의미입니다. 즉, 코드가 실행되는 도중에 상단 바를 숨기거나 보이게 할 수 있습니다.

## 정리

iOS Safari 확장 프로그램의 상단 바를 숨기는 방법은 주로 두 가지입니다. 하나는 HTML과 CSS를 이용하여 렌더링되지 않게 하는 것이고, 다른 하나는 JavaScript를 이용하여 동적으로 처리하는 것입니다. 상황과 필요에 따라 적절한 방법을 선택하여 구현할 수 있습니다.