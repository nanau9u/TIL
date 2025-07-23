# 매개변수와 인자

### 매개변수

- 함수를 정의할 때, 함수가 받을 값을 나타내는 변수

### 인자

- 함수를 호출할 때, 실제로 전달되는 값

```python
def add_numbers(x, y): # x와 y는 매개변수(parameter)
		result = x + y
		return result
		
a = 2
b = 3

sum_result = add_numbers(a, b) # a와 b는 인자(argument)

```

## 다양한 인자 종류

### 1. 위치 인자Positional Arguments

- 함수 호출 시 인자의 위치에 따라 전달되는 인자
- 위치 인자는 함수 호출 시 반드시 값을 전달해야 함

```python
def greet(name, age):
		print(f'안녕하세요, {name}님! {age}살이시군요.')
		
greet('Leo', 17) # 안녕하세요, Leo님! 17살이시군요.
greet(17, 'Leo') # 안녕하세요, 17님! Leo살이시군요.
greet('Leo') # TypeError: greet() missing 1 required positional argument: 'age'
```

### 2. 기본 인자 값Default Argument Values

- 함수 정의에서 매개변수에 기본 값을 할당
- 함수 호출 시 인자를 전달하지 않아도 출력되며, 기본값이 매개변수가 된다.

```python
def greet(name, age=18):
		print(f'안녕하세요, {name}님! {age}살이시군요.')
		
greet('Elias') # 안녕하세요, Elias님! 18살이시군요.
greet('Narke', 99) # 안녕하세요, Narke님! 99살이시군요.
```

### 3. 키워드 인자Keyword Arguments

- 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자
- 매개변수와 인자를 일치시키지 않고, 특정 매개변수에 값을 할당 가능
- 인자의 순서는 중요하지 않다! 인자의 이름을 명시하기만 한다면!
- 단, 호출 시 키워드 인자는 위치 인자 뒤에 위치해야 함

```python
def greet(name, age):
		print(f'안녕하세요, {name}님! {age}살이시군요.')
		
greet(name='Leo', age=17) # 안녕하세요, Leo님! 17살이시군요.
greet(age=17, name='Leo') # 안녕하세요, Leo님! 17살이시군요.
```

### 4. 임의의 인자 목록Arbitrary Argument Lists

- 정해지지 않은 개수(0개 이상)의 인자를 처리 가능
- 함수 정의 시 매개변수 앞에 ‘*’를 붙여 사용
- 여러 개의 인자를 tuple로 처리

```python
def calculate_sum(*args):
		print(args) # (1, 100, 5000, 30)
		print(type(args)) # <class 'tuple'>
		
calculate_sum(1, 100, 5000, 30)
```

### 5. 임의의 키워드 인자 목록Arbitrary Keyword Argument Lists

- 정해지지 않은 개수의 키워드 인자를 처리하는 인자
- 함수 정의 시 매개변수 앞에 ‘**’를 붙여 사용
- 여러 개의 인자를 dictionary로 묶어 처리

```python
dif print_info(**kwargs):
		print(kwargs)
		
print_info(name='Lukas', age=23) # {'name': 'Lukas', 'age': 23} 
```

- ★★ 임의의 인자 목록은 사용자 입장에서 꼭 이 기능이 필요한 게 아니라면 안 쓰는 게 더 좋다. 기본 인자 값에 가까울수록 함수가 분명해지고 오류가 덜 나기 때문이다.

### 함수 인자 권장 작성 순서

- 위치→기본→임의(가변)→임의(가변) 키워드
- 호출 시 인자를 전달하는 과정에서 혼란을 줄일 수 있도록 한다.
- 단, 절대적인 규칙은 아님. 유연한 적용 가능

```python
# 인자의 모든 종류를 적용한 예시

def func(pos1, pos2, default_arg='default', *args, **kwargs):
		print('pos1:', pos1)
		print('pos2:', pos2)
		print('default_arg:', default_arg)
		print('args:', args)
		print('kwargs:', kwargs)

func(1, 2, 3, 4, 5, 6, key1='value1', key2='value2')

"""
pos1: 1
pos2: 2
default_arg: 3
args: (4, 5, 6)
kwargs: {'key1': 'value1', 'key2': 'value2'}
"""
```