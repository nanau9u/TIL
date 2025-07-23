# 함수Function

- 특정 작업을 수행하기 위한 재사용 가능한 코드 묶음
- 예를 들면 ‘+’ 도 함수의 역할을 한다. ‘두 숫자를 더한다’는 정해진 작업을 수행하기 때문이다.

## 함수를 사용하는 이유

- 코드의 중복을 방지
- 재사용성, 가독성, 유지보수성 향상

```python
# 두 수의 합을 구하는 코드
num1 = 5
num2 = 3
sum_result = num1 + num2

print(sum_result)

# 두 수의 합을 구하는 함수
def get_sum(num1, num2):
		return num1 + num2
		
# 함수를 호출하여 결과 출력
num1 = 5
num2 = 3
sum_result = get_sum(num1, num2)
print(sum_resu1t)
```

## 함수 호출Function call

- 함수를 실행하기 위해 함수의 이름을 사용하여 해당 함수의 코드 블록을 실행하는 것
- 표기법: function_name(arguments)

## 함수 구조

```python
def make_sum(pram1, pram2):
			"""이것은 두 수를 받아
			두 수의 합을 반환하는 함수입니다 (함수 설명서, 선택사항)
			>>> make_sum(1, 2)
			3
			"""
			return pram1 + pram2
			
result=make_sum(100, 30)
print(result) # 130
			
#함수 구조			
def 함수이름(매개변수):
		함수내용
		return 반환할 값
		
변수이름=함수이름(매개변수) # 함수 호출
print(변수이름)		# 결과 확인
```

- 함수 인풋: parameter(매개변수(함수에 전달되는 값), INPUT: x)
- 함수 몸통: Docstring(설명서), function body
- 함수 아웃풋: Output: f(x)
- return이 모든 함수에 있는 것은 아님. 필요하지 않은 경우 함수는 반환값이 없을 수 있다!!
- return을 만나면 함수는 종료되고, 결과를 반환
- 함수 내에 return문이 없다면 None이 반환된다.
    - return을 쓰지 않아도, 파이썬이 내부적으로 return None을 붙여주기 때문

## 함수와 반환 값

### print() 함수는 반환 값이 없음

- “반환과 출력이 다른 점을 구분해야 한다.”
- 출력은 개발자 화면에 보여 주는 것 → print()
- 반환은 코드 내에서 답이 등장하는 것 (우리 눈에 보이지는 않음) → 함수 호출
- 즉, print() 자체를 출력해봐도 None이 나온다.

```python
return_value = print(1)
print(return_value) 

# 할당문은 오른쪽에서부터 계산한다.
# 1 출력 후 None 반환 => 을 또다시 출력해서

# 1
# None
# 이 나온다.
```