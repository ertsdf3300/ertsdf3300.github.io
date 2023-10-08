---
title: Chrome 확장 프로그램의 Firebase SDK 문제 해결
date: 2023-08-21 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Chrome
  - FirebaseSDK
---

## Firebase SDK와 Chrome 확장 프로그램 충돌 이슈

StackOverflow에서 다룬 문제에 따르면, Chrome 확장 프로그램을 개발할 때 Firebase SDK를 사용하면서 발생하는 문제점이 있습니다. 확장 프로그램을 Chrome 웹스토어에 제출할 때 거부 당하는 이슈가 발생했는데, 이는 대체로 `EvalError: Refused to evaluate a string as JavaScript`라는 에러 때문입니다. 이 에러는 보안을 위해 JavaScript 코드를 문자열로 평가하는 것을 금지하는 Chrome의 정책과 관련이 있습니다.

## 해결 방법 1: Content Security Policy (CSP) 설정 변경

Content Security Policy (CSP)는 웹 보안 규칙을 정의하는 것입니다. Chrome 확장 프로그램의 `manifest.json` 파일에 있는 CSP 설정을 변경하여 이 문제를 해결할 수 있습니다. 

```json
{
  "content_security_policy": "script-src 'self' https://www.gstatic.com/; object-src 'self'"
}
```

위 코드를 `manifest.json` 파일에 추가하면 Firebase SDK와 관련된 문제를 해결할 수 있습니다. 

## 해결 방법 2: 패키지 버전 일치

Firebase SDK와 Chrome 확장 프로그램 간에 버전 충돌이 일어날 수 있습니다. 이런 문제를 해결하기 위해서는 개발 환경에서 사용하는 Firebase SDK 버전과 확장 프로그램에서 사용하는 버전이 일치해야 합니다.

## 해결 방법 3: 코드 최적화

코드의 효율성을 높이는 것도 중요합니다. 예를 들어, 필요한 Firebase 서비스만을 import 하여 불필요한 코드를 줄이면, 에러 발생 확률을 낮출 수 있습니다.

```javascript
// 나쁜 예
import * as firebase from "firebase/app";
// 좋은 예
import firebase from "firebase/app";
import "firebase/auth";
```

이 방법으로 코드의 효율성을 높이고, 에러 발생을 줄일 수 있습니다.

## 정리

Firebase SDK를 사용하여 Chrome 확장 프로그램을 개발할 때 발생할 수 있는 문제와 그 해결 방법에 대해 알아보았습니다. CSP 설정을 조정하거나, 패키지 버전을 일치시키거나, 코드를 최적화하는 등 다양한 방법이 있습니다. 이러한 방법들을 통해 확장 프로그램 제출 시 발생하는 문제를 해결할 수 있습니다.