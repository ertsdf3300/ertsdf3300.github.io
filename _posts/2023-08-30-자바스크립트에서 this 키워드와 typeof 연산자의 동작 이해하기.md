---
title: 자바스크립트에서 this 키워드와 typeof 연산자의 동작 이해하기
date: 2023-08-30 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트
  - this키워드
  - typeof연산자
---

## `this` 키워드가 어떻게 초기화되지 않은 상태에서 작동하는가?

자바스크립트에서 `this` 키워드는 현재 실행 문맥에 따라 다른 객체를 가리킵니다. 함수 내에서 `this`를 사용하면, 함수가 호출되는 방식에 따라 `this`가 가리키는 객체가 달라집니다. 그렇다면, 변수에 값이 할당되기 전에 `typeof this`를 사용하면 어떻게 될까요?

### 초기화 되지 않은 상태에서 `this`

자바스크립트에서는 `this`가 아직 어떤 객체도 가리키지 않을 때, 기본적으로 전역 객체를 가리킵니다. 웹 브라우저 환경에서는 이 전역 객체가 `window`입니다. 따라서 초기화되지 않은 상태에서 `typeof this`를 실행하면, 전역 객체의 타입을 나타내게 됩니다.

### `typeof` 연산자의 작동 방식

`typeof` 연산자는 변수나 표현식의 타입을 문자열로 반환합니다. `typeof` 연산자는 실제 값이 아니라, 값의 '타입'만을 알려주기 때문에 초기화되지 않은 변수나 `null`, `undefined` 같은 값을 대상으로도 사용할 수 있습니다.

## 예시 코드 분석

이해를 돕기 위해 다음과 같은 코드를 살펴보겠습니다.

```javascript
console.log(typeof this); // "object"
```

여기에서 `typeof this`는 "object"를 출력합니다. 이는 `this`가 전역 객체를 가리키고 있으며, 전역 객체의 타입이 `object`라는 것을 알려줍니다.

### 예외 상황: Strict Mode

자바스크립트의 'Strict Mode'(엄격 모드)에서는 `this`의 동작이 약간 달라집니다. 엄격 모드에서는 전역 객체 대신 `undefined`를 반환합니다.

```javascript
"use strict";
console.log(typeof this); // "undefined"
```

## 정리

자바스크립트에서 `this`는 현재 실행 문맥에 따라 동적으로 바뀝니다. 초기화되지 않은 상태에서 `typeof this`를 실행하면, 기본적으로 전역 객체의 타입을 반환합니다. `typeof` 연산자는 값의 타입만을 체크하기 때문에, 초기화되지 않은 변수나 특별한 값들에 대해서도 문제없이 작동합니다.