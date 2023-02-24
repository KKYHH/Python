# Python 리스트_튜플_세트_딕셔너리

## 리스트

- 리스트는 대괄호 [ ] 를 이용해 만듭니다
- 대괄호 안에 올 수 있는 항목의 데이터 타입은 다양하다
- 숫자 , 문자열 , 불 , 리스트 등등
- 튜플 , 세트 , 딕셔너리도 넣을 수 있다

리스트를 만들 때 각 항목의 데이터 타입은 같지 않아도 됩니다

데이터는 입력한 순서대로 지정되며 항목은 ( , ) 로 구분합니다

또한 대괄호 안에 아무것도 쓰지 않으면 빈 리스트가 만들어집니다

빈 리스트에는 데이터는 없지만 형태는 리스트 입니다

```python
In:

student1 = [90,95,85,80]

print(student1)
type(student1)

Out:

[90,95,85,80]
list
```

student1 에 할당된 데이터 타입은 리스트입니다

리스트 타입의 데이터가 할당된 변수 구조는 다음과 같다

student1 = [ 90,95,85,80 ]

90 = student1 [ 0 ]

95 = student1 [ 1 ]

85 = student1 [ 2 ]

80 = student1 [ 3 ]

변수 student1에서 첫 번째 , 두 번째 , 마지막 항목을 출력하려면 다음과 같이 코드를 실행

```python
In:

student1[0]
student1[1]
student1[-1]

Out:

90
95
80
```

```python
In:

student[1] = 100   # 두 번째 항목에 새로운 데이터 할당

print(student1)

Out:

[90,100,85,80]
```

위 결과를 보면 **두 번째 요소의 값이 95에서 100으로 변경**

```python
In:

myFriends = ['James' , 'Robert' , 'Lisa', 'Mary']
myFriends

Out:

['James','Robert','Lisa','Mary']
```

```python
In:

myFriends[2]

Out:

'Lisa'
```

```python
In:

myFriends[3]

Out:

'Mary'
```

```python
In:

myFriends[-1]

Out:

'Mary'
```

다음은 숫자,문자열,불,리스트를 혼합한 형태의 리스트입니다

```python
In:

mixedList = [0 , 2 , 3.14 , 'python' , 'program' , True , myFriends]

print(mixedList)

Out:

[0 , 2 , 3.14 , 'python' , 'program' , True, ['James','Robert','Lisa','Mary']]
```

## 리스트 다루기

- 리스트 더하기와 곱하기

문자열과 마찬가지로 리스트도 더하기와 곱하기를 할 수 있다

더하기는 두 리스트를 연결하고 곱하기는 리스트를 곱한 수만큼 반복한다

```python
In:

list_con1 = [1,2,3,4]
list_con2 = [5,6,7,8]
list_con = list_con1 + list_con2  # 리스트 연결

print(list_con)

Out:

[1,2,3,4,5,6,7,8]
```

리스트에서 항목 추가하기

- append() 함수를 사용하면 리스트에 새 항목을 추가할 수 있다. append() 함수는 리스트의 끝에 새 항목을 추가한다.

```
In:

a = [1,2,3]
a.append(4)
print(a)

Out:

[1,2,3,4]
```

- insert() 함수를 사용하면 리스트의 특정 위치에 새 항목을 추가할 수 있다. 첫 번째 인자로 추가할 위치의 인덱스를 지정하고, 두 번째 인자로 새 항목의 값을 지정한다.

```
In:

a = [1,2,3]
a.insert(0,0)
print(a)

Out:

[0,1,2,3]

```

리스트에서 항목 삭제하기

- del 키워드를 사용하면 리스트에서 특정 항목을 삭제할 수 있다. 삭제할 항목의 인덱스를 지정하여 del 키워드와 함께 사용한다.

```
In:

a = [1,2,3,4]
del a[1]
print(a)

Out:

[1,3,4]

```

- remove() 함수를 사용하면 리스트에서 특정 값을 가진 항목을 삭제할 수 있다. remove() 함수는 리스트에서 처음으로 나오는 특정 값을 삭제한다.

```
In:

a = [1,2,3,2,4]
a.remove(2)
print(a)

Out:

[1,3,2,4]

```

리스트에서 항목 정렬하기

- sort() 함수를 사용하면 리스트의 항목을 오름차순으로 정렬할 수 있다. sort() 함수는 리스트의 항목을 직접 수정한다.

```
In:

a = [3,1,4,2]
a.sort()
print(a)

Out:

[1,2,3,4]

```

- reverse() 함수를 사용하면 리스트의 항목을 역순으로 정렬할 수 있다. reverse() 함수는 리스트의 항목을 직접 수정한다.

```
In:

a = [3,1,4,2]
a.reverse()
print(a)

Out:

[2,4,1,3]

```

리스트에서 항목 개수 세기

- count() 함수를 사용하면 리스트에서 특정 값의 개수를 세어준다.

```
In:

a = [1,2,2,3,4,2]
print(a.count(2))

Out:

3

```

리스트에서 항목 위치 찾기

- index() 함수를 사용하면 리스트에서 특정 값의 위치를 찾을 수 있다. index() 함수는 리스트에서 처음으로 나오는 특정 값의 인덱스를 반환한다.

```
In:

a = [1,2,3,4,5]
print(a.index(3))

Out:

2

```

## 리스트 메서드 활용하기

파이썬에서는 데이터 타입(자료형)별로 이용할 수 있는 다양한 함수를 제공하는데

이를 **메서드라고** 한다

**메서드를** 이용하면 데이터 처리를 손쉽게 할 수 있다

자료형.메서드이름()

변수명.메서드이름()

| 메서드 | 설명 | 사용 예시 |
| --- | --- | --- |
| append() | 리스트의 맨 뒤에 새로운 항목 추가 | a = [1, 2, 3]; a.append(4)
print(a) -> [1, 2, 3, 4] |
| insert() | 리스트의 특정 위치에 새로운 항목 삽입 | a = [1, 2, 3]; a.insert(1, 4)
print(a) -> [1, 4, 2, 3] |
| extend() | 리스트에 다른 리스트를 이어붙임 | a = [1, 2, 3]; b = [4, 5] 
a.extend(b) 
print(a) -> [1, 2, 3, 4, 5] |
| remove() | 리스트에서 특정 값을 가진 항목을 삭제 | a = [1, 2, 3]; a.remove(2) 
print(a) -> [1, 3] |
| pop() | 리스트의 맨 마지막 항목을 삭제하고 반환 | a = [1, 2, 3] 
b = a.pop() 
print(a, b) -> [1, 2], 3 |
| index() | 리스트에서 특정 값의 인덱스를 반환 | a = [1, 2, 3]
print(a.index(2)) -> 1 |
| count() | 리스트에서 특정 값의 개수를 반환 | a = [1, 2, 2, 3]
print(a.count(2)) -> 2 |
| sort() | 리스트를 오름차순으로 정렬 | a = [3, 2, 1]
a.sort()
print(a) -> [1, 2, 3] |
| reverse() | 리스트를 역순으로 정렬 | a = [1, 2, 3]
a.reverse()
print(a) -> [3, 2, 1] |

표에서 설명된 리스트 메서드중 많이 사용하는 몇 개를 살펴보자

- append()
    
    append 는 리스트의 맨 끝에 새로운 항목을 추가한다
    
    ```python
    In:
    
    myFriends = ['James','Robert','Lisa','Mary']
    print(myFriends)
    
    myFriends.append('Thomas')
    print(myFreinds)
    
    Out:
    
    ['James','Robert','Lisa','Mary']
    ['James','Robert','Lisa','Mary','Thomas']
    ```
    
- insert()
    
    insert 메서드는 리스트의 원하는 위치에 데이터를 삽입한다
    
    ```python
    In:
    
    myFriends = ['James','Robert','Lisa','Mary']
    print(myFriends)
    
    myFriends.insert(1,'Paul')
    print(myFriends)
    
    Out:
    
    ['James','Robert','Lisa','Mary']
    ['James','Paul','Robert','Lisa','Mary']
    ```
    
    인덱스 1번 위치에 ‘Paul’을 삽입하라는 뜻
    
- extend()
    
    ```python
    In
    
    myFriends = ['James','Robert','Lisa','Mary']
    print(myFriends)
    
    myFriends.extend(['Laura','Betty'])
    pirnt(myFreinds)
    
    Out:
    
    ['James','Robert','Lisa','Mary']
    ['James','Robert','Lisa','Mary','Laura','Betty']
    ```
    
    기존 리스트의 맨 끝에 두 개의 새로운 항목이 추가
    

## 튜플

튜플(Tuple)은 리스트와 유사하게 데이터 여러 개를 하나로 묶는데 이용

튜플의 항목은 숫자,문자열,불,리스트,튜플,세트,딕셔너리 등으로 만들 수 있다

**튜플의 속성은 리스트와 비슷하지만 튜플 데이터는 한 번 입력(생성) 하면 그 이후에는 변경할 수가 없다**

### 튜플 만들기

리스트에서는  [ ] 를 이용했고 튜플은 ( ) 사용하거나 없이 입력한다

```python
In:

tuple1 = (1,2,3,4)
pirnt(tuple1)
type(tuple1)

Out:

(1,2,3,4)
tuple
```

```python
In:

tuple2 = 5,6,7,8
print(tuple2)
type(tuple2)

Out:

(5,6,7,8)
tuple
```

인자가 하나만 있는 튜플을 생헝할 땐 항목 입력후 반드시 콤마( , ) 를 입력해야한다

```python
In:

tuple3 = (9,)
tuple4 = 10,

print(tuple3)
print(tuple4)

Out:

(9,)
(10,)
```

## 세트

리스트와 튜플과 유사한 또 다른 데이터 타입으로 세트 (set) 가 있다

세트는 수학의 집합 개념을 파이썬에 이용할 수 있게 만든 데이터 타입이다

세트가 리스트와 튜플과 다른점

- 데이터의 순서가 없고 중복해서 쓸 수 없다
- 교집합 , 합집합 , 차집합을 구하는 메서드를 사용할 수 있다

### 세트 만들기

세트를 생성할 때는 중괄호 { } 로 데이터를 감싼다

```python
In:

set1 = {1,2,3}
set1a = {1,2,3,3}

print(set1)
print(set1a)
type(set1)

Out:

{1,2,3}
{1,2,3}
set
```

중복된 데이터는 하나만 입력된다

### 세트의 교집합 , 합집합 , 차집합 구하기

집합 A 에는 {1,2,3,4,5} 집합 B 에는 {4,5,6,7,8,9,10}이 있다고 가정하에

A 와 B의 교집합 , 합집합 , 차집합을 구해보자

- 메서드
    
    교집합 - intersection()
    
    합집합 - union()
    
    차집합 - difference()
    

```python
In:

A = {1,2,3,4,5}
B = {4,5,6,7,8,9,10}

A.intersection(B) # A에 대한 B의 교집합

Out:

{4,5}
```

```python
In:

A.union(B) # A에 대한 B의 합집합

Out:

{1,2,3,4,5,6,7,8,9,10}
```

```python
In:

A.difference(B) # A에 대한 B의 차집합

Out:

{1,2,3}
```

위 메서드 이용법말고 연산자를 이용할 수도 있다

```python
In:

A&B # A에 대한 B의 합집합
A|B # A에 대한 B의 교집합
A-B # A에 대한 B의 차집합

Out:

{4,5}
{1,2,3,4,5,6,7,8,9,10}
{1,2,3}
```

### 리스트 , 튜플 , 세트 간 타입 변환

list () , tuple () , set () 를 이용해 서로 변환할 수 있다

```python
In:

a = [1,2,3,4,5]
b = tuple(a)

print(b)

Out:

(1,2,3,4,5)
```

리스트인 a 가 튜플로 바뀌었다

```python
In:

c = set(a)

print(c)

Out:

{1,2,3,4,5}
```

리스트인 a가 세트로 바뀌었다

튜플과 세트로 변환된 b 와 c 를 다시 리스트로 변경해보자

```python
In:

list(b)
list(c)

Out:

[1,2,3,4,5]
[1,2,3,4,5]
```

## 딕셔너리

딕셔너리란 우리말로 사전입니다

사전의 구성을 보면 표제어가 있고 그에 대한 설명이 있습니다

따라서 표제어만 찾으면 그에 대한 설명을 전부 확인할 수 있습니다

파이썬의 딕셔너리도 유사하게 구성돼 있습니다 사전의 표제어와 설명은

파이썬의 ( key ) 와 값 ( value ) 이라고 합니다

이처럼 딕셔너리는 키와 값이 항상 쌍으로 구성 됩니다

리스트나 튜플은 인덱스를 이용해 항목을 다뤘지만

**딕셔너리는 키를 이용해 값을 다룹니다**

### 딕셔너리 만들기 { }

**딕셔너리를 만들 땐 데이터 전체를 { } 로 감싼다**

**그리고 키와 값의 구분으로 콜론 ( : ) 을 넣어준다**

dict_name = { key1 : value1 , key2 : value2 , key3 : value3 }

```python
In:

country_capital = { '영국':'런던' , '프랑스':'파리' , '스위스':'베른' , '호주':'멜버른'
'덴마크':'코펜하겐' }

print(country_capital)

Out:

{'영국':'런던' , '프랑스':'파리' , '스위스':'베른' , '호주':'멜버른'
'덴마크':'코펜하겐'}

```

```python
In:

country_capital{'영국'}

Out:

'런던'
```

앞에서도 얘기했듯 딕셔너리의 키는 숫자와 문자열이 될 수 있고

**값은 어떤 데이터 형태도 올 수 있다**

```python
In:

dict_data1 = {1:'버스',3:'비행기',4:'택시',5:'자전거'}
dict_data1

Out:

{1:'버스',3:'비행기',4:'택시',5:'자전거'}
```

```python
In:

dict_data1[3]

Out:

'비행기'
```

dict_data1 의 키 3에 해당하는 값인 ‘비행기’ 출력

### 딕셔너리 다루기

- 딕셔너리에 데이터 추가하고 변경하기

```python
In:

country_capital['독일']='베를린'
country_capital

Out:

{'덴마크':'코펜하겐','독일':'베를린','스위스':'베른','영국':'런던','프랑스':'파리','호주':'멜버른'}
```

```python
In:

country_capital['호주']='캔버라'
country_capital

Out:

{'덴마크':'코펜하겐','독일':'베를린','스위스':'베른','영국':'런던','프랑스':'파리','호주':'캔버라'}
```

### 딕셔너리 데이터 삭제하기

- del 딕셔너리 [key]

```python
In:

del country_capital['덴마크']
country_capital

Out:

{'독일':'베를린','스위스':'베른','영국':'런던','프랑스':'파리','호주':'캔버라'}
```

| 메서드 | 설명 | 예시 |
| --- | --- | --- |
| keys() | 딕셔너리의 모든 키를 리스트로 반환 | dict_data.keys() |
| values() | 딕셔너리의 모든 값을 리스트로 반환 | dict_data.values() |
| items() | 딕셔너리의 모든 키와 값을 (키, 값) 형태의 튜플로 반환 | dict_data.items() |
| update() | 딕셔너리의 데이터를 업데이트 | dict_data.update({'독일':'베를린'}) |
| clear() | 딕셔너리의 모든 항목 삭제 | dict_data.clear() |