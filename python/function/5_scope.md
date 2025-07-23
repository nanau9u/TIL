# 함수와 Scope

### Python의 범위(Scope)

- 함수는 코드 내부에 local scope를 생성하며, 그 외의 공간인 global scope로 구분

### 범위와 변수 관계

- **범위 scope**
    - global scope: 코드 어디서든 참조할 수 있다
    - local scope: 함수가 만든 scope (함수 내부에서만 참조 가능)
- **변수 variable**
    - global variable: global scope에 정의된 변수
    - local variable: local scope에 정의된 변수

### Scope 예시

- 이 예시에서, num은 local scope에 존재하기 때문에 global scope에서 사용할 수 없다. 이는 변수의 수명주기와 관계가 있다.

```python
def func():
		num = 20
		print('local', num) # local 20
		
func()

print('global', num) # NameError: name 'num' is not defined
```

- `func()` 를 호출했을 때 결과값이 `local 20`이 되는 이유는 `func()` 내부에 `print` 가 존재하기 때문이다.
- 즉 `func()` 자체는 아무것도 출력할 수 없지만 `func()` 내부의 `print` 가 값을 출력하는 것이다.
- `func()` 에는 `return` 이 없으므로, `print(func())` 를 하게 되면 `local 20` 과 `None` 이 동시에 출력된다.

### 변수 수명주기

- 변수의 수명주기는 변수가 선언되는 위치와 scope에 따라 결정됨
    1. built-in scope
        - 파이썬이 실행된 이후부터 영원히 유지
    2. global scope
        - 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
    3. local scope 
        - 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

### 이름 검색 규칙(Name Resolution)

- 파이썬에서 사용되는 이름(식별자)들은 특정한 이름공간(namespace)에 저장되어 있다
- 아래와 같은 순서로 이름을 찾아 나가며, LEGB Rule이라고 부른다.
- !! 함수 내에서는 바깥 Scope의 변수에 접근 가능하나 수정은 할 수 없다 !!
1. Local scope: 지역 범위 (현재 작업 중인 범위)
2. Enclosed scope: 지역 범위 한 단계 위 범위
3. Global scope: 최상단에 위치한 범위
4. Built-in scope: 모든 것을 담고 있는 범위 (정의하지 않고 사용할 수 있는 모든 것)


- 이런 이유 때문에, 내장 함수랑 같은 변수 명을 사용하면 안 된다.
    - 내장 함수를 변수명으로 사용하면 내장 함수가 실행되지 않는다.
    - 내장 함수(Built-in Scope에 있다)보다 선언된 변수(보통 Global Scope 혹은 Local Scope에 있다)를 먼저 검색하게 되기 때문이다.



## global 키워드

- 변수의 스코프를 전역 범위로 지정하기 위해 사용
- 일반적으로 함수 내에서 전역 변수를 수정하려는 경우에 사용

```python
num = 0 # 전역 변수

def increment():
		global num  # num를 전역 변수로 선언
		num += 1
		
print(num) # 0
increment()
print(num) # 1
```
