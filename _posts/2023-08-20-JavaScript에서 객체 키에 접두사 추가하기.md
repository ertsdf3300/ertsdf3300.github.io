---
title: JavaScript에서 객체 키에 접두사 추가하기
date: 2023-08-20 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트
---

## 문제 해결 방법

JavaScript에서 객체의 키에 접두사를 추가하는 작업은 상당히 간단하다. 대표적으로 두 가지 방법이 있다. 하나는 `for...in` 루프를 사용하는 것이고, 다른 하나는 `Object.entries`와 `reduce` 메서드를 사용하는 것이다.

### for...in 루프 사용

`for...in` 루프를 사용해서 객체의 모든 키를 순회하면서 새로운 객체에 접두사가 붙은 키와 같은 값을 할당할 수 있다. 예를 들어, 객체가 `{a: 1, b: 2}`이고 접두사가 `'pre_'`인 경우 새로운 객체는 `{pre_a: 1, pre_b: 2}`가 될 것이다.

```javascript
const obj = { a: 1, b: 2 };
const prefix = 'pre_';
const newObj = {};

for (let key in obj) {
  newObj[prefix + key] = obj[key];
}
```

### Object.entries와 reduce 사용

`Object.entries` 메서드를 사용하면 객체의 키와 값을 쉽게 배열로 변환할 수 있다. 그 후에 `reduce` 메서드를 사용해서 새로운 객체를 생성한다.

```javascript
const obj = { a: 1, b: 2 };
const prefix = 'pre_';

const newObj = Object.entries(obj).reduce((acc, [key, value]) => {
  acc[prefix + key] = value;
  return acc;
}, {});
```

## 코드 오류 해결

만약 `'TypeError: Cannot convert undefined or null to object'` 오류가 발생한다면, `obj`가 `undefined` 또는 `null`인지 확인해야 한다. 이런 경우에는 조건문을 사용해서 `obj`가 `undefined` 또는 `null`이 아닌지 확인하면 오류를 방지할 수 있다.

## 정리

JavaScript에서 객체 키에 접두사를 추가하는 것은 복잡한 작업이 아니다. `for...in` 루프나 `Object.entries`와 `reduce` 메서드를 활용하면 간단히 해결할 수 있다. 코드에서 오류를 마주친다면, 객체가 `undefined` 또는 `null`인지 확인하는 것이 중요하다. 이를 통해 원하는 결과를 얻을 수 있다.