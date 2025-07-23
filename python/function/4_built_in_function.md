## 내장 함수Built-in function

- 파이썬이 기본적으로 제공하는 함수 (별도의 import 없이 바로 사용 가능)
- 편리하지만, 다른 언어에서 다르게 작동할 수 있기에 주의!
- 단순히 사용하기에 그치지 않고, 내부 동작 원리를 이해하면 효과적 → 더 나은 코드를 작성하기 위해!

### 자주 사용되는 내장 함수 예시

```python
numbers = [1, 2, 3, 4, 5]

print(numbers) # [1, 2, 3, 4, 5]
print(len(numbers)) # 5
print(max(numbers)) # 5
print(min(numbers)) # 1
print(sum(numbers)) # 15
print(sorted(numbers, reverse=True)) # [5, 4, 3, 2, 1]
```

- 파이썬 공식 문서에서 내장 함수와 자습서 확인해 볼 것!! 도움이 많이 된다.