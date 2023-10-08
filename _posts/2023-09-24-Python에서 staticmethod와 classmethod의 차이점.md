---
title: Python에서 staticmethod와 classmethod의 차이점
date: 2023-09-24 20:00:00 +0900
categories:
  - python
tags:
  - Python
  - 정적메서드
  - 클래스메서드
---

## 정적 메서드(Static Method)란?

`staticmethod`는 클래스의 인스턴스(instance)에 상관없이 클래스 레벨에서 호출되는 메서드입니다. 이 메서드는 클래스 내부에서 `@staticmethod` 데코레이터로 선언되며, 첫 번째 인자로 `self`나 `cls`를 받지 않습니다.

### 예시 코드

```python
class Math:
    @staticmethod
    def add(x, y):
        return x + y

result = Math.add(5, 3)  # 클래스 레벨에서 호출
```

## 클래스 메서드(Class Method)란?

`classmethod`는 클래스에 작용하는 메서드입니다. 첫 번째 인자로 클래스 자체를 받으며, 이 인자는 일반적으로 `cls`라고 명명됩니다.

### 예시 코드

```python
class Math:
    factor = 2
    
    @classmethod
    def multiply(cls, x):
        return cls.factor * x

result = Math.multiply(4)  # 클래스 레벨에서 호출
```

## 두 메서드의 차이점

1. **인자**: `staticmethod`은 `self`나 `cls`를 인자로 받지 않지만, `classmethod`는 `cls`를 첫 번째 인자로 받습니다.
2. **상속**: `staticmethod`는 상속과 관련이 없습니다. `classmethod`는 상속 시 오버라이딩(overriding)이 가능합니다.
3. **용도**: `staticmethod`는 클래스와 관련이 없는 독립적인 로직을 수행할 때 사용합니다. `classmethod`는 클래스 변수를 사용하거나 클래스 자체에 연산을 수행할 때 사용됩니다.
  
## Error: TypeError

주의해야 할 오류 중 하나는 `TypeError`입니다. 이 오류는 대게 메서드에 필요한 인자를 잘못 전달했을 때 발생합니다. 예를 들어, `staticmethod`를 `classmethod`처럼 사용하려고 하거나 반대의 경우에 이 오류가 발생할 수 있습니다.

## 정리

`staticmethod`와 `classmethod`는 클래스 레벨에서 동작하지만 서로 다른 용도와 특징을 가지고 있습니다. 어떤 메서드를 사용할지는 그 메서드가 수행해야 할 작업과 클래스 내부의 변수 사용 여부에 따라 결정됩니다.