---
title: Express-validator와 XML 입력 값 검증 이슈 해결하기
date: 2023-08-18 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Express-validator
---

## 문제 상황 및 오류 코드

다수의 개발자들이 `Express-validator` 라이브러리를 사용하여 API에서 받은 입력 값을 검증합니다. 그러나 XML 데이터를 다루는 경우, 이 라이브러리가 필수 필드가 누락되었는지를 올바르게 감지하지 못하는 문제가 발생할 수 있습니다. 특히, "fields are missing"와 같은 오류 메시지가 나타나지 않을 수 있습니다.

## Express-validator의 작동 원리

`Express-validator`는 JSON 형식의 데이터를 주로 다루며, 요청 본문에서 특정 필드를 검증합니다. 이 라이브러리는 HTTP 요청의 `body`, `cookies`, `headers`, `params`, `query` 등을 검증할 수 있습니다. 

## XML과의 호환성 문제

XML 데이터는 구조적으로 JSON과 다르기 때문에 `Express-validator`가 직접 지원하지 않습니다. 따라서, XML 데이터를 올바르게 처리하려면 추가적인 설정이 필요합니다.

## 해결 방안

1. **XML을 JSON으로 변환:** XML 데이터를 먼저 JSON 형식으로 변환한 뒤 `Express-validator`를 적용할 수 있습니다. 여러 npm 패키지가 이 작업을 도와줍니다.

2. **커스텀 미들웨어 사용:** 직접 작성한 미들웨어를 통해 XML 데이터의 유효성을 검증할 수 있습니다. 이 미들웨어를 `Express-validator` 이전에 위치시킵니다.

3. **다른 라이브러리 고려:** XML 데이터에 특화된 다른 유효성 검증 라이브러리를 사용하는 것도 좋은 선택입니다.

## 정리

`Express-validator`는 JSON 데이터에 최적화되어 있어 XML 데이터에 대한 직접적인 지원이 부족합니다. 이 문제를 해결하기 위해 XML을 JSON으로 변환하거나, 커스텀 미들웨어를 사용하거나, 다른 유효성 검증 라이브러리를 고려할 수 있습니다. 이러한 방법들을 통해 "fields are missing"와 같은 오류 메시지를 정확하게 출력할 수 있습니다.