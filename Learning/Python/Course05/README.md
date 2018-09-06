# Python 컬렉션(셋 &amp; 튜플)
키워드 : [Python Set](https://docs.python.org/3.7/tutorial/datastructures.html#sets), [Python Tuple](https://docs.python.org/3.7/tutorial/datastructures.html#tuples-and-sequences), [Built-in Functions](https://docs.python.org/3.7/library/functions.html)

우리는 지난 강의를 통해 파이썬에서 사용되는 여러 데이터를 하나로 묶어서 사용할 수 있는 컬렉션 혹은, 컨테이너 객체라는 것에 대해서 알아보았습니다. 이번 장에서는 계속해서 파이썬에서 사용되는 컬렉션 자료형인 셋(Set)과 튜플(Tuple)에 대해서 알아보도록 하겠습니다.

## 셋(Set)
셋 컬렉션은 이름에서 느껴지듯이, 집합 연산을 가능케 하는 자료형입니다. 예를 들어, 셋 자료형 간의 합집합, 교집합, 차집합 등의 수학 집합 연산이 가능합니다. 뿐만 아니라, 더 중요한 셋 컬렉션의 특징이 존재하는데요, 셋의 요소는 중복이 없다는(Unique Elements) 점입니다. 또한, 그렇기 때문에 순서를 갖지 않습니다. (Unordered collection) 

우리가 지난 장에서 알아보았던, 딕셔너리를 선언하기 위해서 사용했던 중괄호({})를 이용해서 셋을 선언할 수 있습니다. 또한, 선언할 때 `set()` 생성자 키워드를 이용해서 순서를 갖는 문자열, 리스트, 튜플 등의 자료형을 할당하면 중복이 없는 요소를 셋 자료형으로 반환합니다.

아래 코드는 셋 자료형을 선언하는 예시입니다.
```python
num_set = {1, 1, 2, 2, 3}
print(num_set) # {1, 2, 3}
str_set1 = {'abcabc'}
print(str_set1) # {'abcabc'}
str_set2 = set('abcabc')
print(str_set2) # {a, c, b}
hangul1 = {'안녕안녕ㅎㅎ'}
print(hangul1) # {'안녕안녕ㅎㅎ'}
hangul2 = set('안녕안녕ㅎㅎ')
print(hangul2) # {'ㅎ', '녕', '안'}
```
위 코드에서 주의 깊게 봐야 할 점이 한 가지 있습니다. 바로, 문자열을 초기화하는 코드인데요, 하나의 문자열로 이루어진 자료형을 `{}`로 초기화하는 것과, `set()` 생성자를 이용해 초기화하는 두 가지 코드에 차이가 존재하는 것을 확인할 수 있습니다. 

`{}`로 초기화를 하게 되면, 기본 문자열 그 자체로 반환됩니다. 하지만, `set()` 생성자를 이용하여 문자열을 초기화하면, 해당 문자열 안에 중복된 값을 제거하여 값을 반환하게 됩니다. 또한, 순서를 갖지 않기 때문에, 셋에 할당된 값이 반환되는 순서는 코드를 실행할 때마다 달라지게 됩니다. 이러한 특징 때문에, 셋 컬렉션은 인덱싱과 슬라이싱 등이 불가합니다.

다음은, 셋 컬렉션에서 사용할 수 있는 주요 메서드에 대해서 알아보도록 하겠습니다.

아래 표는 셋 메서드의 다양한 메서드와 의미를 나타냅니다.

메서드|의미
|:-:|:-:|
set.add(x)|새로운 요소 추가
set.update({...})|새로운 요소를 여러개 추가
set.remove(x)|요소 삭제 단, 요소가 없을 경우에 에러 발생
set.pop(x)|요소를 삭제하고, 삭제한 요소를 반환 단, 요소가 없을 경우 에러 발생
set.clear(x)|요소 안의 모든 인자 삭제
set.union({...})|기존의 요소와 합집합 연산
set.intersection({...})|기존의 요소와 교집합 연산
set.diffrence({...})|기존의 요소와 차집합 연산
set.symmetric_difference({...})|기존의 요소와 대칭차집합 연산
set.discard(x)|요소가 존재한다면 삭제

대부분의 내용은 지난 장의 리스트 관련 메서드를 이야기할 때 다뤘던 내용이므로, 어렵지 않게 이해할 수 있을 거라고 생각합니다. 눈 여겨볼 점은, 셋 컬렉션은 집합 관련 연산을 할 수 있는 메서드가 존재합니다. 또한, 메서드를 이용하지 않고, 연산자를 이용하여 연산을 진행할 수도 있는데요, 아래 코드 예시는 연산자를 이용한 집합 연산 코드입니다.

```python
a = {1, 2, 3}
b = {1, 2, 4}
print(a & b) # 1, 2 교집합
print(a | b) # 1, 2, 3, 4 합집합
print(a - b) # 3 차집합
print(a ^ b) # 3, 4 대칭차집합
```
또한, 지난 장에서 알아봤듯이, 셋 컬렉션 역시 `Set Comprehension`을 지원합니다.
```python
a = {x for x in 'abcdef' if x not in 'abc'}
print(a) # {'d', 'e', 'f'}
```
파이썬 코드를 작성하다 보면, 여러 요소의 값을 중복 없이 저장해야 할 경우가 있습니다. 이러한 경우에 셋 컬렉션을 이용하면, 상대적으로 간단하게 중복을 제거할 수 있습니다.

## 튜플(Tuple)
다음은 튜플 컬렉션입니다. 튜플의 가장 큰 특징은 불변(Immutable) 타입의 컬렉션이라는 점입니다. 여기서 말하는 불변 타입은, 한 번 요소의 값이 정해지면 변경할 수 없다는 것을 의미합니다. 튜플은 기본적으로 소괄호(())를 이용해서 선언하거나, 단순히 쉼표(,)로 구분 지어 선언할 수 있습니다.

아래 코드는 튜플의 특징을 나타내는 예시입니다.
```python
# 1번 코드
rainbow = 'red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet'
# 2번 코드
rainbow[0] = 'black' # TypeError 에러 발생!
# 3번 코드
tup = (rainbow, [1, 2, 3, 4, 5])
print(tup) # (('red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet'), [1, 2, 3, 4, 5])
numbers = tup[1]
numbers[0] = 0 # 에러 없음
# 4번 코드
int1 = (1)
print(int1) # 1
# 5번 코드  
tuple1 = (1,) # 같은 표현: tuple1 = 1, 
print(tuple1) # (1,)
```
위 코드를 하나하나 살펴보도록 하겠습니다.

1. 1번 코드는, 쉼표(,)로 요소를 구분 지어 튜플을 선언하고 있는 예시입니다. 이렇게, 단순히 쉼표를 이용하여 구분 지으면 튜플 컬렉션으로 선언할 수 있습니다.

2. 2번 코드는, 이미 한 번 정해진 단일 튜플의 요소의 값을 변경하려고 시도하면, 에러가 발생하는 예시입니다.

3. 3번 코드는, 단일 튜플 컬렉션 자체로는 값을 변경할 수 없는 불변 타입이지만, 리스트와 같이 값이 변할 수 있는 타입을 요소로 가질 수 있다는 점을 나타내는 코드입니다. 튜플은 순서를 갖기 때문에, 인덱스로 값에 접근할 수 있습니다.

4. 4번 코드는, 튜플을 선언할 때 주의할 점을 나타냅니다. 소괄호로 감싼 형태로`(1)` 선언했지만, `int1` 의 값은 단순히 숫자 1을 나타냅니다.

5. 5번 코드는, 4번 코드와 이어지는 내용입니다. 요소가 하나인 튜플을 선언하기 위해선 쉼표(,)를 요소 다음에 작성해주어야 합니다.

### 패킹(Packing), 언패킹(Unpacking)
계속해서 알아봤듯이, 튜플의 경우에 여러 요소를 하나로 묶을 수 있습니다. 조금 더 구체적으로 이러한 특징을 패킹(Packing)이라고 부릅니다. 반대로 패킹된 요소를 순서대로 꺼내오는 것을 언패킹(Unpacking)이라고 부릅니다. 

아래 코드는 튜플의 패킹과 언패킹의 예시입니다.
```python
rainbow = 'red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet' # Packing
tup = (rainbow, [1, 2, 3, 4, 5]) # Packing
r, l = tup # Unpacking

print(r[0], l[0]) # red 1
```
단, 언패킹을 하기 위해선 등호의 왼쪽에 오는 할당할 변수의 수가 튜플 안의 요소의 수와 일치해야 합니다. 그렇지 않으면, `ValueError`라는 에러가 발생합니다.

### Set, Tuple 생성자
지난 장에서 리스트(`list()`)와 딕셔너리(`dict()`)의 이름으로 서로 다른 컬렉션을 형 변환할 수 있다고 말씀드렸습니다. 마찬가지로, 셋(`set()`)과 튜플(`tuple()`) 역시, 생성자를 통해 컬렉션을 변환할 수 있습니다.

```python
numbers = [1, 1, 2, 2, 3]
# 1번 코드
no_dup_numbers = list(set(numbers))  
print(no_dup_numbers) # [1, 2, 3]

tuple_numbers = tuple(numbers)
print(tuple_numbers) # (1, 1, 2, 2, 3)
```
위 코드 예시에서 주의 깊게 봐야 할 코드는, `list(set(numbers))` 부분입니다. 우선 `numbers` 리스트 안에는 `[1, 1, 2, 2, 3]` 형태로 중복된 요소가 포함되어 있습니다. 중복을 제거하기 위해서 셋 생성자를 이용해 셋 컬렉션으로 변환하면, 중복이 제거됩니다. `set(numbers) -> {1, 2, 3}` 중복이 제거된 셋 컬렉션을 다시 리스트로 변환하기 위해서 리스트 생성자를 이용하여 리스트 컬렉션으로 변환합니다. `list(set(numbers)) -> [1, 2, 3]`

## 내장 함수(sorted, lambda, map, filter)
다음 내용은, 이번 장에 주요 내용인 파이썬 내장 함수와 관련된 내용입니다. 파이썬 언어에는 `Built-in Functions`라고 불리는 이미 만들어진 다양한 함수가 존재합니다. 많은 종류의 내장 함수 중에서 다섯 가지 주요 함수에 대해서 알아보도록 하겠습니다.

우린 아직 파이썬 함수에 대한 내용을 다루지 않았지만, 자바스크립트를 공부하며, 기본적인 함수 구조에 대해서 이야기했기 때문에, 어렵지 않게 함수 구조를 이해할 수 있을 거라 생각합니다.

### sorted
우선, `sorted` 함수입니다. 함수의 기본 형식은 다음과 같습니다. 

- `sorted(iterable, key=None, reverse=False)` 

함수의 인자 중에 `key=None`, `reverse=False`로 되어 있는 부분은 작성해주지 않으면 기본 값으로 설정되는 값입니다. 가장 첫 번째 인자인 `iterable`은 반복 가능한 요소를 나타냅니다.(`e.g., list, tuple, etc.`) `key`의 경우엔 정렬을 할 기준을 명시합니다. 명시하지 않으면, 자동으로 기본 기준을 정하여 정렬합니다. `reverse`의 경우엔 오름 차순, 내림 차순을 나타냅니다. 기본 값은 `False`이며, 오름 차순을 나타냅니다. 인자의 기본 값은 파이썬 함수 부분에서 더 중점적으로 이야기하도록 하겠습니다.

```python
numbers = [1, 5, 4, 3, 2]
numbers = sorted(numbers)
print(numbers) # [1, 2, 3, 4, 5]

numbers = sorted(numbers, reverse=True)
print(numbers) # [5, 4, 3, 2, 1]
```
위 코드 예시는 랜덤하게 할당되어 있는 `numbers` 리스트의 값을 오름차순, 내림차순으로 정렬하는 예시입니다. 리스트 컬렉션의 `sort()`, `reverse()` 메서드의 경우엔 반환 값이 없고, 내부적으로 정렬만 이루어집니다. 하지만, `sorted` 메서드의 경우엔 반환값이 존재합니다.

### map
다음은, `map` 함수입니다. 함수의 기본 형식은 다음과 같습니다. 

- `map(function, iterable)` 

`map` 함수는 우리가 정의한 함수(`function`)와 반복 가능한(`iterable`) 자료형을 인자로 받습니다. `map`은 입력받은 자료형의 각 요소가 함수 f에 의해 수행된 결과를 묶어서 리턴하는 함수입니다.

```python
def double(x):
    return x * 2

numbers = [1, 2, 3, 4, 5]
numbers = list(map(double, numbers))
print(numbers) # [2, 4, 6, 8, 10]
```
함수를 먼저 정의하고, 순서가 있는 자료형에 동일한 함수 결과를 반영하여 결과를 반환받고 싶을 경우에 사용합니다. `map` 함수의 반환 결과는 `map` 객체의 주소를 반환하기 때문에, `list` 생성자를 이용해서 리스트 형태로 반환하도록 한 번 더 감싼 것입니다.

### filter
다음은, `filter` 함수입니다. 함수의 기본 형식은 다음과 같습니다. 

- `filter(function, iterable)` 

`filter` 함수는 우리가 정의한 함수(`function`)와 반복 가능한(`iterable`) 자료형을 인자로 받습니다. 위에서 살펴본 `map` 자료형과 다른 점은, 인자로 받는 함수의 반환 값이 어떤 연산 결과를 반환하는 함수가 아닌, `True, False, None`을 나타내는 형태인 논리적 반환 값이라는 점입니다. 

그렇기 때문에, 두 번째 인자로 받는 요소를 첫 번째 인자인 함수(`function`)의 인자로 넘겨주어, 함수의 연산 결과가 참(`True`)인 요소만 반환합니다.

```python
def grater_than_2(x):
    return x > 2

numbers = [1, 2, 3, 4, 5]
numbers = list(filter(grater_than_2, numbers))
print(numbers) # [3, 4, 5]
```
`filter` 함수는, 함수를 먼저 정의하고, 순서가 있는 자료형에 값을 걸러내고 반환받고 싶을 경우에 사용합니다. `filter` 함수의 반환 결과는 `filter` 객체의 주소를 반환하기 때문에, `list` 생성자를 이용해서 리스트 형태로 반환하도록 한 번 더 감싼 것입니다.

### lambda
다음은, 람다 표현식(Lambda expression)이라고 불리는 내용입니다. 파이썬 언어뿐만 아니라, 다양한 언어에서 람다 표현식을 제공하고 있습니다.(표현법은 차이가 있습니다.) 자바스크립트에서 익명 함수(Anonymous function)라고 불리는 이름 없는 함수에 대해서 이야기했습니다. 마찬가지로, 파이썬에서는 `lambda` 키워드를 이용하면, 이름이 없는 함수를 정의할 수 있습니다. 

`Lambda expression` 기본 형식은 다음과 같습니다. 

- lambda `parameters`:`expression` 

우선, lambda 키워드를 작성합니다. `parameters` 부분에 함수의 인자를 작성합니다. 표현식 부분에 해당 인자에 대한 반환 결과를 나타내기 위한 코드를 작성합니다. 

아래 코드는 위에서 살펴본, `map`, `filter` 함수 코드에 `lambda` 표현식을 적용한 코드입니다.

```python
numbers = [1, 2, 3, 4, 5]
double = list(map(lambda x:x * 2, numbers))
grater_than_2 = list(filter(lambda x:x>2, numbers))
print(double) # [2, 4, 6, 8, 10]
print(grater_than_2) # [3, 4, 5][3, 4, 5]
```
람다 표현식을 이용하면, 같은 결과를 나타내는 함수를 짧은 코드로 작성할 수 있어 효율적입니다. 또한, 함수 구문이 작성될 수 없는 부분에도 람다 표현식을 사용할 수 있기 때문에, 람다 키워드는 잘 기억해두시게 좋습니다.

파이썬에서는 굉장히 다양한 내장 함수를 제공하고 있습니다. 더 많은 파이썬 내장 함수에 대해서 궁금하시다면, [여기](https://docs.python.org/3.7/library/functions.html)를 참고해주세요! 

이번 장에서는 셋과 튜플에 대해서 알아보았습니다. 역시나.. 지난 장에 이어서 새로운 내용이 많이 나왔습니다. 자주 언급한 얘기지만, 프로그래밍을 공부할 때 어떤 언어의 문법을 익히고, 그 언어가 가지고 있는 특징을 익히는 데 생각보다 오랜 시간을 투자해야 합니다. 처음부터, 모든 문법, 개념과 같은 내용을 다 알고 넘어갈 수 있다면 좋겠지만, 어려움이 많습니다. 직접 많은 코드를 작성해보고, 모르는 내용은 찾아보며 자료 구조, 알고리즘, 성능 최적화 등과 같은 깊은 내용도 공부해보시길 바라겠습니다. 

끝으로, 긴 글 읽어주시느라 고생하셨습니다! 감사합니다. :)