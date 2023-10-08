---
title: React Query 초기 데이터 가져오기 막고, 다시 가져오기 활성화하는 방법
date: 2023-08-04 20:00:00 +0900
categories:
  - JavaScript
tags:
  - React
  - Query
---

## 문제 상황 소개

React Query를 사용하면서 초기 데이터를 가져오는 것을 막고, 나중에 다시 가져올 수 있는 기능을 활성화하고 싶은데 어떻게 할까요? 이 문제는 개발자들이 흔히 직면하는 문제 중 하나입니다. Stack Overflow에도 이와 관련된 다양한 의견과 해결책이 있습니다.

## 해결방법 1: `enabled` 옵션 사용

가장 쉬운 방법은 React Query의 `useQuery` 또는 `useMutation` 훅에서 `enabled` 옵션을 사용하는 것입니다. 이 옵션을 `false`로 설정하면 초기 데이터 가져오기를 막을 수 있습니다. 나중에 다시 데이터를 가져오고 싶을 때 `enabled`를 `true`로 바꿔주면 됩니다.

```javascript
const { data, refetch } = useQuery('myQueryKey', fetchFunction, {
  enabled: false,
});
```

이 코드에서 `enabled: false`는 초기에 데이터를 가져오지 않도록 설정합니다. `refetch` 함수를 사용하여 나중에 데이터를 다시 가져올 수 있습니다.

## 해결방법 2: `skip` 변수 활용

`skip`이라는 변수를 활용해 조건부로 쿼리를 실행할 수도 있습니다. 이 방법은 `enabled` 옵션을 동적으로 변경하는 것과 유사합니다.

```javascript
const skip = someCondition;
const { data } = useQuery('myQueryKey', fetchFunction, {
  enabled: !skip,
});
```

이렇게 하면 `someCondition`이 `true`일 때 쿼리가 실행되지 않습니다.

## 에러 처리: `Error Fetching`

데이터를 가져오는 과정에서 에러가 발생할 경우, React Query는 `Error Fetching` 이라는 에러 메시지를 띄울 수 있습니다. 이 에러는 데이터 가져오기가 실패했을 때 나타나며, 해결 방법은 주로 API 서버나 네트워크 상태를 확인하는 것입니다.

## 정리

React Query에서 초기 데이터 가져오기를 막고 다시 가져오기를 활성화하는 방법은 주로 `enabled` 옵션을 사용하거나, 동적으로 이 옵션을 제어하는 것입니다. 이를 통해 더 유연하고 효율적인 데이터 관리가 가능해집니다. 이러한 기능은 사용자 경험을 높이는 데 크게 기여할 수 있습니다.