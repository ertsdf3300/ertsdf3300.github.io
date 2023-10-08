---
title: Google Maps 마커 색상 변경하기 속성 기반
date: 2023-09-06 20:00:00 +0900
categories:
  - JavaScript
tags:
  - 구글맵API
  - Google
---

## 문제 상황

Google Maps API를 이용하여 웹페이지에 지도를 표시하고 있습니다. 여기에 여러 개의 마커를 표시하려고 하는데, 마커의 색상을 그 마커의 특정 속성에 따라 다르게 하고 싶습니다. 예를 들어, '평점'이라는 속성이 높을수록 파란색으로, 낮을수록 빨간색으로 마커를 표시하려고 합니다.

## 코드 오류

스택오버플로우의 원문에 따르면, 사용자는 이 문제를 해결하려고 시도했지만 `Uncaught TypeError` 라는 오류에 직면했습니다.

## 해결 방법

### 데이터 준비하기

먼저, 마커의 정보가 담긴 객체 배열을 준비합니다. 이 객체에는 '평점' 같은 속성도 포함되어야 합니다.

```javascript
const markersData = [
  { lat: 37.5665, lng: 126.9780, rating: 5 },
  { lat: 35.6895, lng: 139.6917, rating: 3 },
  // ... (이하 생략)
];
```

### Google Maps API 사용하기

Google Maps API를 이용하여 지도를 생성하고, 마커를 추가하는 코드를 작성합니다.

```javascript
const map = new google.maps.Map(document.getElementById("map"), {
  center: { lat: 37.5665, lng: 126.9780 },
  zoom: 8,
});
```

### 마커 색상 변경하기

마커를 추가할 때, '평점' 속성을 확인하여 색상을 설정합니다.

```javascript
markersData.forEach((data) => {
  const color = data.rating > 4 ? 'blue' : 'red';
  new google.maps.Marker({
    position: { lat: data.lat, lng: data.lng },
    map,
    icon: {
      path: google.maps.SymbolPath.CIRCLE,
      scale: 7,
      fillColor: color,
      fillOpacity: 1.0,
      strokeWeight: 0,
    },
  });
});
```

이렇게 하면 평점에 따라 마커의 색상이 파란색 또는 빨간색으로 표시됩니다.

## 요약

Google Maps에서 마커의 색상을 특정 속성에 따라 변경하는 것은 복잡하지 않습니다. 적절한 데이터 구조와 Google Maps API의 옵션을 활용하면 쉽게 구현할 수 있습니다. 이러한 방법을 통해 사용자에게 더 직관적인 정보를 제공할 수 있습니다.