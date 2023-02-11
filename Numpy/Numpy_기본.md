# Numpy 기초

# Numpy란?

- 다차원 배열을 쉽게 처리하고 효율적으로 사용할수 있는 파이썬의 패키지
- 데이터 구조외에도 수치계산을 위해 효율적으로 구현된 기능제공
- 데이터 분석을 할때 pandas와 함께 자주 쓰인다
- Numerical Python 의 약자이며 Matrix와 vector 같은 Array 연산을 할 때 사용

## 왜 Numpy를 사용하나

데이터란 이미지,오디오,텍스트,숫자등으로 다양한 형태와 크기로 존재

사람은 이러한 형태를 이해하지만 컴퓨터는 0또는1만 이해가능

데이터분석을 수행하기위한 전제조건은 컴퓨터가 이해할 수 있게 데이터를 숫자형식으로 변환하는것

효율적으로 배열을 저장 및 조작하려면 Numpy 패키지를  쓴다

파이썬의 내장기능인 list[ ] 또한 Numpy배열과 동일한 기능을 제공

배열의 크기가 작다면 문제 없지만 Numpy 배열은 데이터 크기가 커질수록 저장 및 가공의 효율성 증가

이러한 점으로 파이썬의 Numpy패키지는 data 업무의 핵심도구로 인식

파이썬은 강력한 언어이지만 많은 양의 복잡한 수치 계산을 할 때는 느리다는 단점이 존재 하지만 Numpy의 경우 핵심 기능들이 C언어로 구현되어 빠르게 동작

Numpy 자체로도 많이 사용되지만 이후에 사용되는 SciPy나 Pandas의 base 객체로도 사용

Numpy에 사용되는 다양한 코드표현법을 Pytorch와 Tensorflow에 사용하는 경우가 많아 Numpy의 활용법은 반드시 알아둘 필요가 있다

## Numpy array VS Python List

> Numpy는 배열(array)을 생성하고 배열 내부의 숫자 데이터를 조작하는 빠르고 효율적인 방법을 광범위하게 제공합니다. Python 목록(list)은 단일 목록 내에 다양한 데이터 유형을 포함할 수 있지만, Numpy 배열의 모든 요소는 동질적이어야 합니다.
> 
- Numpy를 사용하는 이유
    
    > Numpy 배열은 Python 목록보다 빠르고 작습니다.배열은 메모리를 적게 사용하며, 사용이 편리합니다. Numpy는 데이터를 저장하는 데 휠씬 적은 메모리를 사용하며 데이터 유형을 지정하는 머커니즘을 제공합니다. 이를 통해 코드를 더욱 최적화할 수 있습니다.
    > 

## Numpy 특징

- 일반 List에 비해 빠르고 메모리를 효율적으로 사용
- 반복문 없이 데이터 배열에 대한 처리를 지원하여 빠르고 편리
- 선형대수와 관련된 다양한 기능 제공
- C,C++,포트란 등의 언어와 통합이 가능

## Numpy 설치 및 호출

- 설치 pip install numpy

```python
pip install numpy

import numpy as np
```

- 호출 import numpy as np
    - 일반적으로 numpy는 np라는 alias 별칭을 이용하여 호출
    - 거의 모든 예시에 np로 사용되기 때문에 np가 나오면 numpy라고 이해
    

## Numpy 프로그래밍

- 행렬 및 벡터 연산을 위해선 다차원 array를 사용해야한다 Numpy에선 이러한 다차원 array형태인 핵심적인 객체를 ndarray라고 부르며 파이썬의 기본 내장 객체인 array와는 다른 속성을 가지고 있다
    - ndarry.ndim  # 어레이의 차원
    - ndarry.shape # 어레이의 크기를 나타내는 정수 튜플 (행수,열수)
    - ndarry.size # 어레이 요소의 총 개수  (shape 요소의 곱과 같음)
    - ndarry.dtype # 어레이 요소의 데이터타입
    - ndarry.itemsize
    - ndarry.data
    

## ndarray란? (다차원배열객체)

- 컴퓨터 과학에서 배열(array)란 인덱스와 그 인덱스에 대응하는 데이터들로 이루어진 자료구조를 나타낸다
- 다차원배열객체(ndarray)란 임의의 차원을 갖는 배열을 의미
- Numpy의 ndarray 클래스는 행렬과 벡터 모두를 나타낼 수 있는데 벡터는 1차원 배열을 행렬은 2차원 배열을 말합니다 3차원 이상의 배열은 텐서(tensor)라고 합니다

<img src="https://github.com/KKYHH/Python/blob/main/image/Untitled%201.png?raw=true">

1차원 배열 (벡터)

<img src="https://github.com/KKYHH/Python/blob/main/image/Untitled.png?raw=true">

2차원 배열 (행렬)

### *배열(array)과 리스트(list)의 차이점

NumPy는 배열을 작성하여 내부 수치 데이터를 조작하기 위한 매우 빠르고 효율적인 방법을 제공

[리스트(list)](https://gksid102.tistory.com/24)

위 파이선 컨테이너 관련 포스팅에서 리스트는 배열이 아니라고 표현 한다

이유는 한 리스트 내에 **다른 데이터형**을 포함할 수 있기 때문

반대로 NumPy 배열은 배열 내의 **모든 데이터의 종류가 동일** 해야 한다

즉 동일한 type의 값들을 갖는다

배열이 고르지 못할 경우 배열에 대해 실행되는 수학적 연산이 매우 비효율적이기 때문

또한 NumPy의 배열은 메모리 소비량이 적어서 사용하기 편리하고 리스트보다 더 빠르고 컴팩트하다 따라서 코드를 한층 더 최적화 할 수 있다

Python 리스트

- 여러가지 타입의 원소
- linked List 구현
- 메모리 용량이 크고 속도가 느림
- 벡터화 연산 불가

NumPy ndarray

- 동일 타입의 원소
- contiguous memory layout
- 메모리 최적화, 계산 속도 향상
- 벡터화 연산 가능

### ndarray 구현방식

- ndarray는 일반 파이썬 List의 구현방식 (Linked List)와 다르게 C의 배열(array)의 특성인 연속적인 메모리에 배치된다는 점
- 이로 인해 C의 array가 가지는 장점은 살리면서 파이썬의 직관적인 코딩도 가능하게 된다
- 인접한 메모리 배치는 다수의 선형대수 연산의 속도를 향상 시킨다
- 그래서 전문가들의 python 성능 향상을 위한 코딩 관례중 Python에서 ndarray의 벡터화 연산으로 계산할 수 있는 경우에는 파이썬 내장 반복문은 사용하지 않는다

## 벡터와 행렬

- 벡터 (vector)
    - 1차원 데이터 (1차원 배열)
    - 스칼라가 연속적으로 모여있는것
        - 스칼라(scalar): 단순하게 측정된 하나의 값
    

```python
import numpy as np

lst= [1,2,3,4,5]
vector = np.array(lst)

print(vector)

[1 2 3 4 5]
```

- 행렬 (Matrix)
    - 2차원 데이터 (2차원 배열)
    1차원 데이터가 모여 있는것

```python
import numpy as np

lst= [
    [1,2,3],
    [4,5,6]
]
matirx = np.array(lst)

print(matirx)

[[1 2 3]
 [4 5 6]]
```

점 = 스칼라

선 = 벡터

면 = 매트릭스

Tensor = 면이 모여서 3D

<img src="https://github.com/KKYHH/Python/blob/main/image/Untitled%202.png?raw=true">

---

# Numpy 기초 배열생성 해보기

```python
#numpy 불러오기
import numpy as np
```

numpy는 외부 라이브러리이기 때문에 numpy를 사용하려면 numpy를 불러야 한다

import numpy as np

- 일반적으로 numpy는 np라는 alias 별칭을 이용하여 호출
- 거의 모든 예시에 np로 사용되기 때문에 np가 나오면 numpy라고 이해

numpy를 호출 했으면 여러가지 numpy 기능을 사용 할 수 있다

numpy 패키지의 중심은 배열이므로 배열을 생성해야 한다

### 배열을 생성

```python
x = [1,4,5,6]

vector = np.array(x)
print(vector)

[1 4 5 6]
```

- x 라는 리스트를 array로 고정 시킨다

       x는 list vector는 array

```python
import numpy as np

lst = [
    [1,2,3],
    [4,5,6]
]

x = np.array(lst)

print (x)

[[1 2 3]
 [4 5 6]]
```

- python list를 array로 배열 생성된다

### .size  #  데이터의 수

```python
import numpy as np

lst = [
    [1,2,3],
		[4,5,6]
]

x = np.array(lst)

print (x.size)

6
```

- 배열 안의 데이터 수 출력 [1 2 3 4 5 6] 총 6개

### .ndim # 배열의 열수

```python
import numpy as np

lst = [
    [1,2,3],
		[4,5,6]
]

x = np.array(lst)

print (x.ndim)

2
```

- 배열의 열수를 알려준다

### .shape[0] # 배열의 열수

```python
import numpy as np

lst = [
    [1,2,3],
    [4,5,6]
]

x = np.array(lst)

print (x.shape[0])

2
```

- 배열의 열수를 알려준다

### .shape[1] # 배열의 행수

```python
import numpy as np

lst = [
    [1,2,3],
    [4,5,6]
]

x = np.array(lst)

print (x.shape[1])

3
```

- 배열의 행수를 알려준다

### .shape  # 배열의 차원

```python
import numpy as np

lst = [
    [1,2,3],
    [4,5,6]
]

x = np.array(lst)

print (x.shape)

(2,3)
```

- 배열의 차원 즉 행과 열을 알려준다

### .[0,0] # 배열의 원소 접근

```python
import numpy as np

lst = [
    [1,2,3],
    [4,5,6]
]

x = np.array(lst)

print(x[0,2])

3
```

- 배열안의 원소값을 꺼낸다
- 세기는 0 부터 열은 1 행은 2 0열의2행은 3
- ex) [0,1] = 2
    
          [0,0] = 1
    
    [1,2] = 6
    

## 특수한 배열의 생성

### np.arange

```python
import numpy as np

x = np.arange(10)

print(x)

[0 1 2 3 4 5 6 7 8 9]
```

- 1씩 증가하는 1차원 배열  (0부터 시작)

```python
import numpy as np

x = np.arange(3,10)

print(x)

[3 4 5 6 7 8 9]
```

- 1씩 증가하는 1차원 배열 (시작이 3부터)

### -영(0) 배열-

Numpy에서는 모든 원소가 0인 벡터 또는 행렬을 만들어주는 기능이 있다

- zeros

zeros는 1차원 0 벡터를 생성할 경우 양의 정수를, 2차원 0 행렬을 생성할 경우 행,열 개수를 지정해줘야 한다

아래 코드는 길이가 4인 0 벡터를 생성

```python
import numpy as np

print(np.zeros(4))

[0. 0. 0. 0.]
```

아래 코드는 3x4 인 0 행렬을 생성

```
import numpy as np

print(np.zeros((3,4)))

[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
```

Numpy에서 주어진 배열과 똑같은 모양(Shape)의 0 벡터를 만들어주는

zeros_like 라는 것이 있다

zero_like는 똑같은 모양으로 만들 배열을 인자로 받는다

```python
import numpy as np

x = np.array([1,2,3])
print(np.zeros_like(x))

[0,0,0]

X = np.array([[1,2,3],[4,5,6]])
print(np.zeros_like(X))

[[0 0 0]
 [0 0 0]]
```

### -1(one)배열-

Numpy에서 모든 원소가 1인 배열을 만들어 준다

특정길이 또는 차원의 1 배열을 만들기 위해선 ones

특정배열과 똑같은 모양의 1배열을 만들기 위해선 ones_like

원리는 앞에서 다룬 zeors,zeors_like와 같다

```python
import numpy as np

print(np.ones(3))

[1,1,1]

print(np.ones((4,3)))

[[1. 1. 1.]
 [1. 1. 1.]
 [1. 1. 1.]
 [1. 1. 1.]]
```

### - np.linspace -

linspace는 시작점과 끝점을 포함하여 정해진 개수만큼 같은 간격을 갖는 배열을 생성

```python
import numpy as np

print(np.linspace(0,1,10,))

[0.         0.11111111 0.22222222 0.33333333 0.44444444 0.55555556
 0.66666667 0.77777778 0.88888889 1.        ]
```

끝점을 포함하고 싶지 않다면 endpoint 인자를 False로 바꾼다

```python
import numpy as np

print(np.linspace(0,1,10,endpoint=False))

[0.  0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9]
```

# 배열결합

배열결합의 정의

- 결합 : 두 개 이상의 배열 내용을 단일 배열에 넣는 것 의미
- SQL : key(키) 기반해 테이블 결합.
- NumPy : axis(축) 기반해 배열 결합.

axis = 0 : 가로축 기준 결합 (명시적으로 전달 안 된 경우)

axis = 1 : 세로축 기준 결합

*아래 함수 경우 axis 명시하면 에러 발생

- ex) hstack() , vstack() , dstack () 함수

함수에 따라서 다양한 기준으로 결합.

- ex) row(행) , column(열), depth(깊이) 등

## concatenate() 함수 - row(행) 따라 결합

- 결합할 배열을 매개변수로 전달
- axis(축) 값 명시 안 한 경우, 0(=가로축) 간주

[1차원 배열 결합] axis = 0 (가로축) 기준 결합

```python
import numpy as np

arr1 = np.array([1,2,3])
arr2 = np.array([4,5,6])

arr = np.concatenate((arr1,arr2))

print(arr)

[1 2 3 4 5 6]
```

[1차원 배열 결합] axis = 1 (세로축) 기준 결합 시, 에러발생

```python
import numpy as np

arr1 = np.array([1,2,3])
arr2 = np.array([4,5,6])

arr = np.concatenate((arr1,arr2),axis=1)

print(arr)

numpy.AxisError: axis 1 is out of bounds for array of dimension 1
```

why?

[2차원 배열 결합] axis = 0 (가로축) 기준 결합

```python
import numpy as np

arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])

arr = np.concatenate((arr1,arr2),axis=0)

print(arr)

[[1 2]
 [3 4]
 [5 6]
 [7 8]]
```

[2차원 배열 결합] axis = 1(세로축) 기준 결합

```python
import numpy as np

arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])

arr = np.concatenate((arr1,arr2),axis=1)

print(arr)

[[1 2 5 6]
 [3 4 7 8]]
```

### stack() 함수 - 새로운 row(행) 따라 쌓기 결합

concatenate() 와 유사하나, 유일한 차이점은 새 축을 따라 결합

stacking 의미 : 두 번째 축을 따라 두 개의 1-D 배열을 연결해 , 하나를 다른 하나 위에 놓는걸 말한다

- 결합할 배열을 매개변수로 전달
- axis(축) 값 명시 안 한 경우, 0 (= 가로축) 간주

[1차원 배열 결합] axis=0 (가로축) 기준

```python
import numpy as np

arr1 = np.array([1,2,3])
arr2 = np.array([4,5,6])

arr = np.stack((arr1,arr2),axis=0)

print(arr)

[[1 2 3]
 [4 5 6]]
```

[1차원 배열 결합] axis=1 (세로축) 기준

```python
import numpy as np

arr1 = np.array([1,2,3])
arr2 = np.array([4,5,6])

arr = np.stack((arr1,arr2),axis=1)

print(arr)

[[1 4]
 [2 5]
 [3 6]]
```

[2차원 배열 결합] axis = 0 (가로축) 기준

```python
import numpy as np

arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])

arr = np.stack((arr1,arr2),axis=0)

print(arr)

[[[1 2]
  [3 4]]

 [[5 6]
  [7 8]]]
```

[2차원 배열 결합] axis = 1 (세로축) 기준

```python
import numpy as np

arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])

arr = np.stack((arr1,arr2),axis=1)

print(arr)

[[[1 2]
  [5 6]]

 [[3 4]
  [7 8]]]
```

### hstack() 함수 -row(행) 따라 쌓기 결합

- axis 지정 시 에러 발생

[1차원 배열 결합]

```python
import numpy as np

arr1 = np.array([1,2,3])
arr2 = np.array([4,5,6])

arr = np.hstack((arr1,arr2))

print(arr)

[1 2 3 4 5 6]
```

[2차원 배열 결합]

```python
import numpy as np

arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])

arr = np.hstack((arr1,arr2))

print(arr)

[[1 2 5 6]
 [3 4 7 8]]
```

### vstack() 함수 - column (열) 따라 쌓기 결합

- axis 지정 시 에러 발생

[1차원 배열 결합]

```python
import numpy as np

arr1 = np.array([1,2,3])
arr2 = np.array([4,5,6])

arr = np.vstack((arr1,arr2))

print(arr)

[[1 2 3]
 [4 5 6]]
```

[2차원 배열 결합]

```python
import numpy as np

arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])

arr = np.vstack((arr1,arr2))

print(arr)

[[1 2]
 [3 4]
 [5 6]
 [7 8]]
```

### dstack() 함수 - 높이(깊이) 따라 쌓기 결합

- axis 지정 시 에러 발생

[1차원 배열 결합]

```python
import numpy as np

arr1 = np.array([1,2,3])
arr2 = np.array([4,5,6])

arr = np.dstack((arr1,arr2))

print(arr)

[[[1 4]
  [2 5]
  [3 6]]]
```

[2차원 배열 결합]

```python
import numpy as np

arr1 = np.array([[1,2],[3,4]])
arr2 = np.array([[5,6],[7,8]])

arr = np.dstack((arr1,arr2))

print(arr)

[[[1 5]
  [2 6]]

 [[3 7]
  [4 8]]]
```

# 배열의 차원 변환

### reshape 함수

- Numpy Array의 가장 큰 장점은 형태(shape)를 자유자재로 변경이 가능한것
- Numpy Array의 형태를 바꾸기 위해서는 reshape 함수를 이용
- 데이터의 변경 없이 shape만 바꾼다

1. 1차원과 2차원 변환

```python
import numpy as np

a = [1,2,3,4,5,6,7,8]
b = np.reshape(a,(2,4))
c = np.reshape(a,(4,2))

print (b)
print('\n')
print(c)

[[1 2 3 4]
 [5 6 7 8]]

[[1 2]
 [3 4]
 [5 6]
 [7 8]]

# 1차원 리스트를 2차원으로 reshape
# 차원은 대괄호의 개수로도 알 수 있다
```

> reshape 할 때는 총 개수가 맞아야 한다
> 
> 
> 즉 size가 같아야 shape 변환이 가능
> 

1. 3차원 변환

```python
import numpy as np

a = np.arange(1,9)
b = a.reshape(2,2,2)

print(b)

[[[1 2]
  [3 4]]

 [[5 6]
  [7 8]]]
```

> 이것은 높이가 2이고, 세로가 2이고, 가로가 2인 모양으로 바꾸라는 의미
> 

b[0]

```python
import numpy as np

a = np.arange(1,9)
b = a.reshape(2,2,2)

print(b[0])

[[1 2]
 [3 4]]
```

b[0][0,1]

```python
import numpy as np

a = np.arange(1,9)
b = a.reshape(2,2,2)

print(b[0][0,1])

2
```

- 3차원에서 첫 번째 행렬의 1행 2열 값 인덱싱

### reshape 에서 -1의 의미

- reshape를 활용하는 경우를 보다 보면 입력인수로 -1이 들어가는 경우가 있다
- reshape()의 ‘-1’이 의미하는 바는, 변경된 배열의 ‘-1’ 위치의 차원은 “원래 배열의 길이와 남은 차원으로 부터 추정” 이 된다는 뜻
- 자동으로 적절한 형태를 계산

EX)

```python
import numpy as np

a = np.arange(12)
a = a.reshape(3,4)

print(a)

[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
```

- 12개의 인덱스를 reshape로 3행4열 배열

### reshape(-1,정수) : 행의 위치에 -1인 경우

(-1, 1)

```python
import numpy as np

a = np.arange(12)
a = a.reshape(-1,1)

print(a)

[[ 0]
 [ 1]
 [ 2]
 [ 3]
 [ 4]
 [ 5]
 [ 6]
 [ 7]
 [ 8]
 [ 9]
 [10]
 [11]]
```

(-1, 2)

```python
import numpy as np

a = np.arange(12)
a = a.reshape(-1,2)

print(a)

[[ 0  1]
 [ 2  3]
 [ 4  5]
 [ 6  7]
 [ 8  9]
 [10 11]]
```

(-1, 3)

```python
import numpy as np

a = np.arange(12)
a = a.reshape(-1,3)

print(a)

[[ 0  1  2]
 [ 3  4  5]
 [ 6  7  8]
 [ 9 10 11]]
```

즉, 행(row)의 위치에 -1을 넣고 열의 값을 지정해주면 변환될 배열의 행의 수는 알아서 지정이 된다

### reshape( 정수 , -1) : 열의 위치에 -1인 경우

( 1 , -1 )

```python
import numpy as np

a = np.arange(12)
a = a.reshape(1,-1)

print(a)

[[ 0  1  2  3  4  5  6  7  8  9 10 11]]
```

( 2 , -1 )

```python
import numpy as np

a = np.arange(12)
a = a.reshape(2,-1)

print(a)

[[ 0  1  2  3  4  5]
 [ 6  7  8  9 10 11]]
```

( 3 , -1 )

```python
import numpy as np

a = np.arange(12)
a = a.reshape(3,-1)

print(a)

[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
```

( 4 , -1 )

```python
import numpy as np

a = np.arange(12)
a = a.reshape(4,-1)

print(a)

[[ 0  1  2]
 [ 3  4  5]
 [ 6  7  8]
 [ 9 10 11]]
```

이또한 마찬가지로, 이번엔 행(row)의 수를 지정해주면 열은 자동으로 재배열을 해주는것

### reshape( - 1 ) 인 경우

```python
import numpy as np

a = np.arange(12)
a = a.reshape(-1)

print(a)

[ 0  1  2  3  4  5  6  7  8  9 10 11]
```

-1 만 들어간다면 1차원 배열을 반환한다 모양은 a.reshape(1,-1)과 같으나

이는 ( 1 , 12 )의 2차원 배열이다  #대괄호의 수로 확인 가능

# 데이터 타입

### dtype

> Numpy 배열 ndarray는 dtype으로 저장되어, np.array()로 ndarray오브젝트를 생성할 때 지정하거나 astype()메소드로 변경하는것이 가능하다
> 

> 기본적으로 하나의 ndarray오브젝트에 대해 하나의 dtype가 설정되어 있으며, 모든 요소가 같은 데이터 형이 된다
> 

Numpy 데이터타입

- i - integer (정수)
- b - boolean (참거짓)
- u - unsigned integer (부호없는 정수)
- f - float (소수)
- c - complex (복소수)
- m - timedelta (타임델타)
- M - datetime (날짜시간)
- O - object (객체)
- S - string (문자열)
- U - unicode string (유니코드 문자열)
- V - void (다른 유형에 대한 고정된 메모리 덩어리)

### 배열 데이터타입 확인

정수

```python
import numpy as np

arr = np.array([1,2,3,4])
print(arr.dtype)

int64 

# 시스템에 따라 32,64 부분 다름
```

유니코드 문자열

```python
import numpy as np

arr = np.array(['HTML','CSS','JS'])
print(arr.dtype)

<U4 

# 숫자 4부분은 문자열 요소중 가장 긴 길이 의미 ('HTML')
```

### 정의된 데이터타입으로 배열 만들기

array() 함수로 배열 생성시,

선택적 매개변수인 dtype 이용해 데이터 유형 정의 가능

```python
import numpy as np

arr = np.array([1,2,3,4],dtype="S")

print(arr)
print(arr.dtype)

[b'1' b'2' b'3' b'4']
|S1
```

i,u,f,S,U 데이터 유형의 경우 크기도 지정 가능

```python
import numpy as np

arr = np.array([1,2,3,4],dtype='i4')

print(arr)
print(arr.dtype)

[1 2 3 4]
int32

# i8 경우 결과값은 int 64
# i 뒤에는 아무 숫자나 넣으면 에러 발생
```

### 데이터타입 변환 불가한 요소 존재시 에러 발생

지정 타입으로 변환 불가한 요소 존재시, ValueError 발생

```python
import numpy as np

arr = np.array(['a','2','3'],dtype='i')

ValueError: invalid literal for int() with base 10: 'a'
```

### 기존 배열 데이터타입 변환

astype() 함수 : 배열 복사본 만들고 데이터유형을 매개변수로 지정

- 데이터유형 지정은 ‘f’ , ‘i’ 등 형식, float , int 등 형식 둘 다 가능
- 기존 배열을 유지한 채 데이터유형 변경하는 가장 좋은 방법

i 매개변수 사용해 데이터유형을 (실수 → 정수)로 변경

```python
import numpy as np

arr = np.array([1.1,2.1,3.1])
newarr = arr.astype('i')

print(arr)
print(newarr)
print(newarr.dtype)

[1.1 2.1 3.1]
[1 2 3]
int32
```

int 매개변수로 데이터유형을 (실수 → 정수)로 변경

```python
import numpy as np

arr = np.array([1.1,2.1,3.1])
newarr = arr.astype('int')

print(arr)
print(newarr)
print(newarr.dtype)

[1.1 2.1 3.1]
[1 2 3]
int64
```

bool 매개변수로 데이터 유형을 ( 정수 → 참거짓) 변경

```python
import numpy as np

arr = np.array([1,0,3])
newarr = arr.astype(bool)

print(arr)
print(newarr)
print(newarr.dtype)

[1 0 3]
[ True False  True]
bool
```

# 슬라이싱 / 인덱싱

1.

```python
import numpy as np

a = np.array([1,2,3,4,5])

print(a)
print(a[3:])
print(a[1:-1])
print(a[0:3:2])

[1 2 3 4 5]
[4 5]
[2 3 4]
[1 3]
```

배열 [a:b:c]를 이용하여 배열의 일부를 잘라서 표시할 수 있다

- a는 시작값
- b는 도착값
- c는 간격을 의미

index는 0~len-1 까지 존재하며, 아무것도 입력하지 않고 :로 사용할 경우, 모든 행 또는 열을 의미한다

:n 으로 사용할 경우 0~n 까지의 길이를 의미하며 n: 으로 사용할 경우, n ~ len -1 까지의 길이를 의미한다

-1 을 입력할 경우, 마지막 index -1 (len -2) 를 의미한다

2.

```python
import numpy as np

a = np.array([[1,2,3],
              [4,5,6],
              [7,8,9]])

print(a)
print(a[: ,1:])
print(a[0:1,0:2])

[[1 2 3]
 [4 5 6]
 [7 8 9]]

[[2 3]
 [5 6]
 [8 9]]

[[1 2]]
```

배열 [a:b,c:d]를 이용하여 배열의 일부를 잘라서 표시할 수 있다

동일하게 배열 [a:b:e,c:d:f] 를 이용하여 e와 f를 간격으로 사용할 수 있습니다

a ~ b 는 표시할 행의 위치를 의미하며, c ~ d 는 표시할 열의 위치를 의미합니다

3.

```python
import numpy as np

a = np.array([[1,2,3,4,5],
              [6,7,8,9,10],
              [11,12,13,14,15]])

print(a)

print(a[::2,::2])

[[ 1  2  3  4  5]
 [ 6  7  8  9 10]
 [11 12 13 14 15]]

[[ 1  3  5]
 [11 13 15]]
```

배열의 슬라이싱에서 간격만 입력하여 배열을 출력 할 수 있다

[::2,::2] 일 경우, 행을 2칸씩 띄우며, 열도 2칸씩 띄워 출력

# 배열 조건 연산

### where 함수

- 단순 조건문으로 해결하기 어려울 때 np.where 을 사용하여 복잡한 작업을 할 수 있다
- where 함수는 조건에 맞을 경우와 틀릴경우 두가지 값을 구성된 배열로 리턴

```python
import numpy as np

arr = np.array([1,2,3,4,5])
print(np.where(arr > 3,1,0))

[0 0 0 1 1]
```

- arr 중 3보다 크면 1 작으면 0 을 리턴한다

```python
import numpy as np

arr = np.array([10,5,3,9,1])
x = np.arange(5)

print(np.where( x % 2==0 , arr ,0))

[10  0  3  0  1]
```

- [0,1,2,3,4] 순차 배열인 x 배열의 조건을 사용하여 arr의 짝수번째 값만 0으로 바꾼 arr을 리턴

```python
import numpy as np

x,y = np.ogrid[:3,:4]
print(x,y,sep='\n')

[[0]
 [1]
 [2]]
[[0 1 2 3]]
```

- 3x4 의 격자의 축을 각각 x,y 배열로 리턴

```python
import numpy as np

x,y = np.ogrid[:3,:4]

print(x,y,sep='\n')

print(np.where(x==y,1,0))

[[0]
 [1]
 [2]]
[[0 1 2 3]]

[[1 0 0 0]
 [0 1 0 0]
 [0 0 1 0]]
```

- 위 배열을 활용해 대각선 값만 access 할 수 있는 예제

```python
import numpy as np

x,y = np.ogrid[:10,:10]

print(np.where(x==y,y,0))

[[0 0 0 0 0 0 0 0 0 0]
 [0 1 0 0 0 0 0 0 0 0]
 [0 0 2 0 0 0 0 0 0 0]
 [0 0 0 3 0 0 0 0 0 0]
 [0 0 0 0 4 0 0 0 0 0]
 [0 0 0 0 0 5 0 0 0 0]
 [0 0 0 0 0 0 6 0 0 0]
 [0 0 0 0 0 0 0 7 0 0]
 [0 0 0 0 0 0 0 0 8 0]
 [0 0 0 0 0 0 0 0 0 9]]
```

- 응용하면 10x10의 대각선에 순차 값을 넣을 수도 있다

# 

# Broad casting 브로드캐스팅

- 하나의 배열이나 요소가 어떤 특정 배열에 영향을 미칠 때 배열간의 형상을 맞추는것을 브로드캐스팅이라고 한다
- 배열의 모양이 다르더라도 어떠한 조건이 만족했을 때 작은 배열을 자동으로 큰배열 크기에 맞춘다.

```python
import numpy as np

arr1 = np.array([1.0, 2.0, 3.0])
arr2 = np.array([2.0, 2.0, 2.0])
print(arr1 * arr2)

[2. 4. 6.]
```

```python
import numpy as np

arr1 = np.array([1.0, 2.0, 3.0])
print(arr1 * 2) # arr1 * arr2와 결과가 같다.

[2. 4. 6.]
```

<img src="https://github.com/KKYHH/Python/blob/main/image/Untitled%203.png?raw=true">

<img src="https://github.com/KKYHH/Python/blob/main/image/Untitled%204.png?raw=true">

<img src="https://github.com/KKYHH/Python/blob/main/image/Untitled%206.png?raw=true">

<img src="https://github.com/KKYHH/Python/blob/main/image/Untitled%205.png?raw=true">


# Mask 마스킹

Bool 배열을 마스크로 사용하여 데이터의 특정 부분을 선택할 수 있다

```python
import numpy as np

lst = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
arr = np.array(lst)
print(arr.shape)

(3, 3)
```

- lst 안에 행렬을 만들고 arr 변수로 array 시킨다
- 형태는 (3,3)

```python
import numpy as np

lst = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
arr = np.array(lst)

mask = [True,False,True]
print(arr[:,mask])

[[1 3]
 [4 6]
 [7 9]]
```

- mask = [True,False,True]
- [ : , mask]
- 전체 행의 1열 3열을 True로 출력하고 2열은 False 출력
- 2열 2,5,8 제외 나머지 행열 출력
