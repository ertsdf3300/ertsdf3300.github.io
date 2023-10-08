---
title: Telegram에서 Gram.js API로 모든 메시지에서 값 검색하기
date: 2023-08-10 20:00:00 +0900
categories:
  - JavaScript
tags:
  - Telegram
  - GramJS
---

## 문제 설명

Stackoverflow에는 Gram.js API를 사용하여 Telegram에서 모든 메시지에 포함된 특정 값을 검색하는 방법에 대한 질문이 올라왔습니다. 이 문제는 메시지 로그에서 특정 단어나 문장을 찾아야 하는 경우에 유용할 것입니다.

## Error Name

`Not Specified`

## 해결 방안

### 메서드 호출하기

Gram.js API에서는 `client.getMessages` 메서드를 사용하여 채널, 그룹, 또는 개인 대화의 메시지를 검색할 수 있습니다. 이 메서드를 이용하면 메시지 로그를 가져와서 검색을 수행할 수 있습니다.

```python
from gramjs import TelegramClient

async with TelegramClient('anon', api_id, api_hash) as client:
    messages = await client.getMessages('some_channel', limit=100)
```

### 메시지 필터링하기

가져온 메시지에서 원하는 값을 찾기 위해서는 Python의 `for` 루프와 `if` 문을 사용하여 메시지를 필터링합니다.

```python
target_value = 'search_this'

for message in messages:
    if target_value in message.text:
        print(f"Found: {message.text}")
```

### 전체 코드

```python
from gramjs import TelegramClient

target_value = 'search_this'

async with TelegramClient('anon', api_id, api_hash) as client:
    messages = await client.getMessages('some_channel', limit=100)
    
    for message in messages:
        if target_value in message.text:
            print(f"Found: {message.text}")
```

## 결론

이 방법을 통해 Gram.js API를 사용하여 Telegram의 모든 메시지에서 특정 값을 쉽게 찾을 수 있습니다. Python의 기본 구문만을 사용하여 메시지를 필터링하므로, 복잡한 알고리즘은 필요하지 않습니다.