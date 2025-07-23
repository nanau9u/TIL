# Packing & Unpacking

## Packing

- 여러 개의 데이터를 하나의 컬렉션으로 모아 담는 과정
- 기본 원리
    - 여러 개의 값을 하나의 튜플로 묶는 파이썬의 기본 동작
    - 한 변수에 콤마 ( , ) 로 구분된 값을 넣으면 자동으로 튜플로 처리

```python
packed_values = 1, 2, 3, 4, 5
print(packed_valuse) # (1, 2, 3, 4, 5)
```

### ‘*’ 을 활용한 패킹 (함수 매개변수 작성 시)

- 남는 위치 인자들을 튜플로 묶기
- *를 붙인 매개변수가 남은 위치 인자들을 모두 모아 하나의 튜플로 만듦

```python
def my_func(*args):
		print(args) # (1, 2, 3, 4, 5)
		print(type(args)) # <class 'tuple'>
		
my_func(1, 2, 3, 4, 5)
```

### ‘**’을 활용한 패킹 (함수 매개변수 작성 시)

- 남는 키워드 인자들을 딕셔너리로 묶기
- **를 붙인 매개변수가 남는 키워드 인자들을 모두 모아 하나의 딕셔너리로 만듦

```python
def my_func2(**kwargs):
		print(kwargs) # {'a': 1, 'b': 2, 'c': 3}
		print(type(kwargs)) # <class 'dict'>

my_func2(a=1, b=2, c=3)
```

## Unpacking

- 컬렉션에 담겨 있는 데이터들을 개별 요소로 펼쳐 놓는 과정
- 기본 원리
    - 튜플이나 리스트 등의 객체의 요소들을 개별 변수에 할당
    - ‘시퀀스 언패킹(Sequence Unpacking)’또는 ‘다중 할당(Multiple Assignment)라고 부름

```python
packed_values = 1, 2, 3, 4, 5

# (1, 2, 3, 4, 5) 튜플의 각 요소들이
# a, b, c, d, e 변수에 순서대로 '언패킹'되어 할당됨
a, b, c, d, e = packed_values

print(a, b, c, d, e) # 1 2 3 4 5
print(a) # 1
```

### ‘*’ 을 활용한 언패킹 (함수 인자 전달)

- 리스트나 튜플 앞에 *를 붙여 각 요소를 함수의 개별 위치 인자로 전달

```python
def my_function(x, y, z, k):
		print(x, y, z, k)
		
names = ['Leo', 'Lukas', 'Elias', 'Narke']
my_function(*names) # Leo Lukas Elias Narke
```

### ‘**’을 활용한 언패킹 (딕셔너리 → 함수 키워드 인자)

- 딕셔너리 앞에 **를 붙여 {키: 값} 쌍을 키=값 형태의 키워드 인자로 전달

```python
def my_function(x, y, z):
		print(x, y, z)
		
my_dict = {'x': 1, 'y': 2, 'z': 3}
my_function(**my_dict) # 1 2 3 
```

### 📦 Packing & Unpacking, * & ** 정리

| 구분 | 상황 | `*` 연산자 | `**` 연산자 |
| --- | --- | --- | --- |
| 패킹 | 함수 정의 시 | 여러 위치 인자를 하나의 튜플로 받음 | 여러 키워드 인자를 하나의 딕셔너리로 받음 |
| 언패킹 | 함수 호출 시 | 리스트/튜플을 개별 위치 인자로 전달 | 딕셔너리를 개별 키워드 인자로 전달 |