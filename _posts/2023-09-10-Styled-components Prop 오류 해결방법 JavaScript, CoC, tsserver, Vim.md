---
title: Styled-components Prop 오류 해결방법 JavaScript, CoC, tsserver, Vim
date: 2023-09-10 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 자바스크립트
  - CoC
  - tsserver
  - Vim
---

## 오류 상황 설명

문제는 Vim 편집기에서 CoC(Conqueror of Completion)와 tsserver(TypeScript Server)를 사용하면서 "Styled-components" 라이브러리를 사용할 때 발생합니다. 특정 상황에서 `Prop type error`라는 오류 메시지가 출력되며 이로 인해 코드의 정상적인 작동이 방해됩니다. 여기서 `Prop type error`는 프로퍼티의 자료형이 잘못되었다는 것을 의미합니다.

## 원인 분석

이 문제는 주로 TypeScript와 styled-components가 함께 사용될 때 자주 발생합니다. CoC와 tsserver는 코드 자동완성 및 오류 체크를 제공하는 도구입니다. 이 도구들이 styled-components의 프로퍼티 자료형을 정확히 판단하지 못해 오류를 발생시킵니다.

## 해결 방안 1: CoC 설정 변경

첫 번째 해결 방안은 CoC의 설정을 조정하는 것입니다. CoC 설정 파일을 열고, TypeScript에 대한 옵션을 조정해야 합니다. 주로 `coc-settings.json` 파일에서 이를 설정할 수 있으며, 이 파일은 `~/.config/nvim/coc-settings.json`에 위치합니다.

1. `coc-settings.json` 파일을 열어주세요.
2. TypeScript 관련 설정을 찾아 수정합니다.
3. 저장한 뒤 Vim을 재시작합니다.

## 해결 방안 2: tsserver 업데이트

두 번째 방법은 tsserver를 최신 버전으로 업데이트하는 것입니다. 가끔 오류는 tsserver의 이전 버전에서 발생할 수 있기 때문입니다.

1. 터미널을 열어 `npm install -g typescript` 명령어를 실행합니다.
2. 설치가 완료되면 Vim을 재시작합니다.

## 해결 방안 3: styled-components 설정 수정

세 번째 방법은 styled-components 라이브러리 자체의 설정을 수정하는 것입니다.

1. `tsconfig.json` 파일을 열어주세요.
2. `compilerOptions` 부분에 `"jsx": "react"`를 추가합니다.
3. 저장한 뒤 프로젝트를 재실행합니다.

이렇게 세 가지 방안을 시도해보면 `Prop type error` 문제를 해결할 수 있을 것입니다. 각 방안은 서로 다른 환경과 설정에 따라 더 효과적일 수 있으니, 여러 가지를 시도해보는 것이 좋습니다.