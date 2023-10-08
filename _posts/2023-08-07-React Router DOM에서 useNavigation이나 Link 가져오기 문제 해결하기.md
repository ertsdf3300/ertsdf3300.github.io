---
title: React Router DOM에서 useNavigation이나 Link 가져오기 문제 해결하기
date: 2023-08-07 20:00:00 +0900
categories:
  - JavaScript
tags:
  - React
  - RouterDom
---

## 문제 상황

예전에는 `react-router-dom`에서 `useNavigation`이나 `Link` 컴포넌트를 가져오는 것이 문제가 되지 않았습니다. 하지만 최근에 코드에서 이들을 가져오려고 하면 오류가 발생합니다. 오류 메시지는 `Cannot destructure property 'Link' of 'react-router-dom' as it is undefined`입니다.

## 원인 파악

이 문제가 발생하는 주된 원인은 라이브러리의 버전 차이일 가능성이 높습니다. React Router DOM의 새로운 버전이 출시되면서 일부 API가 변경되거나 제거되었을 가능성이 있습니다. 

## 해결 방법 1: 라이브러리 버전 확인

첫 번째로 해야 할 일은 `package.json` 파일에서 `react-router-dom`의 버전을 확인하는 것입니다. 버전이 예전 버전이라면 최신 버전으로 업데이트해 보세요.

```bash
npm install react-router-dom@latest
```

## 해결 방법 2: API 문서 확인

두 번째로, React Router DOM의 공식 문서를 확인하여 최신 API 정보를 얻는 것입니다. `useNavigation`이나 `Link`가 여전히 지원되는지, 아니면 다른 함수나 컴포넌트로 대체되었는지를 확인하세요.

## 해결 방법 3: 올바른 import 문법 사용

세 번째로, `import` 문법이 올바른지 확인합니다. 예를 들어, 이전에는 다음과 같은 방식으로 `Link`를 가져왔을 수 있습니다.

```javascript
import { Link } from 'react-router-dom';
```

새로운 버전에서는 이것이 변경되었을 수 있으므로, 공식 문서에서 올바른 문법을 확인하세요.

## 해결 방법 4: 커뮤니티 자료 활용

마지막으로, 다른 개발자들이 이 문제에 대해 어떻게 해결했는지를 검색해 보세요. Stack Overflow 같은 개발 커뮤니티에서 유용한 정보를 얻을 수 있습니다. 단, 외부 링크를 제공할 수 없으므로 직접 검색을 해야 합니다.

## 정리

이 문제를 해결하기 위해서는 여러 방법을 시도해 볼 수 있습니다. 라이브러리의 버전을 확인하고, 필요하다면 업데이트를 하세요. 그리고 공식 문서를 통해 최신 정보를 확인하고, 커뮤니티에서 다른 개발자들의 해결 방법을 찾아보세요. 이렇게 하면 문제를 해결할 확률이 높아질 것입니다.