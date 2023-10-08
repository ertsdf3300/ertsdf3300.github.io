---
title: 파이썬에서 if __name__ == __main__의 의미와 사용법
date: 2023-09-15 20:00:00 +0900
categories:
  - python
tags:
  - Python
---

## 이 코드 라인이 왜 중요한가?

파이썬 프로그래밍에서 `if __name__ == "__main__":` 구문을 종종 볼 수 있습니다. 이 코드 라인은 주로 스크립트 파일이 독립적으로 실행될 때만 특정 코드 블록을 실행하도록 하는데 사용됩니다.

## `__name__` 변수의 역할

파이썬에서 `__name__`은 내장 변수로, 현재 모듈의 이름을 나타냅니다. 이 변수의 기본 값은 `"__main__"`입니다. 하지만 이 스크립트가 다른 스크립트에서 `import`로 가져와졌다면, `__name__` 변수는 원래 모듈의 이름을 갖게 됩니다.

## 코드 예제와 설명

```python
# 파일 이름: my_module.py

def function_one():
    print("Function One is called")

def function_two():
    print("Function Two is called")

if __name__ == "__main__":
    function_one()
    function_two()
```

위 코드에서 `if __name__ == "__main__":` 구문 아래의 `function_one()`과 `function_two()` 함수는 다음 두 가지 상황에 따라 다르게 작동합니다.

1. **독립적으로 실행**: `my_module.py`를 직접 실행하면 `__name__` 변수의 값은 `"__main__"`이 됩니다. 따라서 `function_one()`과 `function_two()`가 실행됩니다.
2. **모듈로서 호출**: 다른 파이썬 스크립트에서 `import my_module`을 사용해 호출하면, `__name__`은 `"my_module"`로 설정됩니다. 이 경우 `if __name__ == "__main__":` 아래의 코드는 실행되지 않습니다.

## 실용적인 적용

이 구문은 코드를 모듈로 사용할 때와 독립적인 스크립트로 사용할 때를 구분하기 위해 매우 유용합니다. 따라서 이를 통해 코드의 재사용성을 높이고 가독성을 개선할 수 있습니다.

코드의 품질과 효율성을 높이기 위해 `if __name__ == "__main__":`은 꼭 알아두어야 할 파이썬의 기본 구문 중 하나입니다. 이 구문을 이해하고 올바르게 사용하면, 코드가 더욱 유연하고 확장 가능해집니다.