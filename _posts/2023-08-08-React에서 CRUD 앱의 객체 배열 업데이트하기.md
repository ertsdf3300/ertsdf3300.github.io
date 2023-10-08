---
title: React에서 CRUD 앱의 객체 배열 업데이트하기
date: 2023-08-08 20:00:00 +0900
categories:
  - JavaScript
tags:
  - React
  - CRUD
---

## 배열 메소드를 이용한 객체 배열 업데이트

CRUD는 Create(생성), Read(읽기), Update(수정), Delete(삭제)의 첫 글자를 따서 만든 용어입니다. 이러한 작업을 처리하기 위해 배열 메소드를 사용할 수 있습니다. 예를 들어, JavaScript의 `map`, `filter`, `splice` 등의 메소드를 사용하면 쉽게 객체 배열을 업데이트할 수 있습니다.

### `map` 메소드를 이용한 업데이트

`map` 메소드는 배열의 각 요소에 대해 주어진 함수를 호출한 결과로 새로운 배열을 생성합니다. `map`을 사용하면, 객체 배열에서 특정 조건에 맞는 객체만 수정할 수 있습니다.

```javascript
const updateItem = (array, itemId, newValues) => {
  return array.map(item => {
    if (item.id === itemId) {
      return { ...item, ...newValues };
    }
    return item;
  });
}
```

### `filter`와 `concat` 메소드를 이용한 업데이트

`filter` 메소드는 주어진 함수의 테스트를 통과한 모든 요소를 모아 새로운 배열을 반환합니다. `concat`은 두 배열이나 값들을 하나의 새 배열에 연결합니다.

```javascript
const removeItem = (array, itemId) => {
  return array.filter(item => item.id !== itemId);
}

const addItem = (array, newItem) => {
  return array.concat([newItem]);
}
```

### 배열의 `splice` 메소드

`splice` 메소드는 배열의 내용을 변경할 수 있습니다. 이 메소드를 사용하면, 원하는 인덱스 위치에 새 요소를 추가하거나 삭제할 수 있습니다.

```javascript
const replaceItem = (array, index, newItem) => {
  array.splice(index, 1, newItem);
  return array;
}
```

## 정리

React에서 CRUD 앱을 만들 때 배열 메소드를 효율적으로 사용하면 객체 배열을 쉽고 빠르게 업데이트할 수 있습니다. 이러한 메소드들은 배열을 직접 변경하지 않고, 새로운 배열을 반환해서 React의 불변성 원칙을 지키는 것도 가능합니다. 이를 통해 성능 최적화와 더불어 코드의 가독성도 높일 수 있습니다.