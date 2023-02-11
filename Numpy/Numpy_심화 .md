# Numpy 심화

# 기본연산

### arange

- numpy 에서 원하는 숫자 범위를 모두 포함하는 배열을 만드는 함수
- arange를 사용하면 원하는 숫자 범위 간격에 따른 array 생성 가능

```python
import numpy as np

print(np.arange(30))

[ 0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
 24 25 26 27 28 29]
```

- Python list와 같은 효과, integer로 0부터 29까지 호출

```python
import numpy as np

x = np.arange(30)
print(x.reshape((5,6)))

[[ 0  1  2  3  4  5]
 [ 6  7  8  9 10 11]
 [12 13 14 15 16 17]
 [18 19 20 21 22 23]
 [24 25 26 27 28 29]]
```

- 0부터 29까지의 스칼라를 5행6열로 reshape

### zeros

- zeros는 0으로 가득 찬 array를 생성

```python
import numpy as np

print(np.zeros(shape=(10,)))

[0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
```

```python
import numpy as np

print(np.zeros(shape=(10,),dtype=np.int8))

[0 0 0 0 0 0 0 0 0 0]
```

- 데이터타입 int를 사용하여 정수로 표현

### ones

- ones는 zeros와 마찬가지로 1로 가득찬 array를 생성

```python
import numpy as np

print(np.ones(shape=(10,),dtype=np.int8))

[1 1 1 1 1 1 1 1 1 1]
```

```python
import numpy as np

a = (np.ones(shape=(10,),dtype=np.int8))

print(a.reshape((2,5)))

[[1 1 1 1 1]
 [1 1 1 1 1]]
```

- 위 값을 reshape 해서 2행5열 배열로 출력

### empty

- empty는 초기화 되지 않은 값으로 zeros나 ones와 마찬가지로 배열을 생성해준다
- !!!! 메모리가 초기화 되지 않고 할당 되기 때문에 예상치 못한 값이 들어가있어서 꼭 주의 고려해야 한다 ( 실무에서 거의 사용되지 않음)

```python
import numpy as np

a = np.empty(shape=(10,),dtype=np.int8)

print(a)

[ 0  0  0  0  0  0  0 64 -8 27]
# 할 때 마다 바뀐다
```

```python
import numpy as np

a = np.empty(shape=(10,),dtype=np.int8)

print(a.reshape((2,5)))

[[   0    0    0    0    0]
 [   0    0   16 -123  -68]]
# 마찬가지로 할 때마다 바뀐다
```

- 위 값을 2행5열 배열로 reshape

### ~ _like

- _like는 지정된 array의 shape 크기 만큼 지정된 값으로 채워 array를 반환
- ones,zeros,empty 사용 할 수 있다

ex)

```python
import numpy as np

t = np.arange(30).reshape(5,6)

print(t)

[[ 0  1  2  3  4  5]
 [ 6  7  8  9 10 11]
 [12 13 14 15 16 17]
 [18 19 20 21 22 23]
 [24 25 26 27 28 29]]
```

_like 를 적용해보자

np.ones_like(t)

```python
import numpy as np

t = np.arange(30).reshape(5,6)

print(np.ones_like(t))

[[1 1 1 1 1 1]
 [1 1 1 1 1 1]
 [1 1 1 1 1 1]
 [1 1 1 1 1 1]
 [1 1 1 1 1 1]]
```

- ones_like 를 적용한 사례 전부 1로 바꿔준다

np.zeros_like

```python
import numpy as np

t = np.arange(30).reshape(5,6)

print(np.zeros_like(t))

[[0 0 0 0 0 0]
 [0 0 0 0 0 0]
 [0 0 0 0 0 0]
 [0 0 0 0 0 0]
 [0 0 0 0 0 0]]
```

- zeors_like 를 적용한 사례 전부 0으로 바꿔준다

np.empty_like

```python
import numpy as np

t = np.arange(30).reshape(5,6)

print(np.empty_like(t))

[[-8070450532247928832 -8070450532247928832                   18
                     0                    0                    0]
 [                   0                    0                    0
                     0                    0                    0]
 [                   0                    0                    0
                     9                    0                    8]
 [                   0                    8                    0
            5427667568           5428086864           5427785664]
 [                   0                    3                    0
                    24                    0                   24]]
```

- empty_like !주의해서 사용

# Broad casting 브로드캐스팅

Numpy 에서 브로드캐스팅이라는 단어를 매우 많이 사용한다

사전적 의미의 차이는 있지만 Python Numpy에서는 조금 다른의미로 사용된다

- Python Numpy에서 말하는 브로드캐스팅은 일정 조건을 부합하는 다른 형태의 배열끼리 연산 수행하는 것을 의미
- 같은 사이즈의 데이터일때 빈곳을 채움

<img src="https://github.com/KKYHH/Python/blob/main/numpy_image/%EC%8B%AC%ED%99%94_1.png?raw=true">

- 두 축이 똑같거나
- 둘 중 하나의 축이 1일 때

# 선형대수

### 행렬 (matrix)

```python
import numpy as np

print(np.array([1,2,3,4]))
print(np.array([[1,2,3,4],[11,22,33,44]]))

[1 2 3 4]

[[ 1  2  3  4]
 [11 22 33 44]]
```

### 단위행렬 (Unit Matrix)

```python
import numpy as np

mat_4 = np.eye(4)
print(mat_4)

[[1. 0. 0. 0.]
 [0. 1. 0. 0.]
 [0. 0. 1. 0.]
 [0. 0. 0. 1.]]
```

- 단위행렬은 대각원소가 1이고, 나머지 원소는 모두0인 n차 정방행렬( square matrix)을 의미합니다

### 영행렬 (Zero Matrix)

```python
import numpy as np

zero_4 = np.zeros((4,4))
print(zero_4)

[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
```

- n,n 을 지정 안하고 n 만 쓰면 행으로만 출력

### 대각행렬(diagonal matrix)

```python
import numpy as np

x = np.array([[1,2,3],[2,3,4],[4,5,6]])

print(x)

print(np.diag(x))

[[1 2 3]
 [2 3 4]
 [4 5 6]]

[1 3 6]
```

- 대각선으로만 1,3,6 출력

### 🛑전치행렬(Transpose Matrix)

전치행렬은 행과 열을 바꾸는 행렬

```python
import numpy as np

mat = np.array([[1,1,1],[1,1,1]])
print(mat)

print(mat.T)

[[1 1 1]
 [1 1 1]]

[[1 1]
 [1 1]
 [1 1]]
```

- 2행3열의 배열을 Transpose 해서 3행2열 배열로 변경

```python
import numpy as np

mat = np.array([[1,1,1],[1,1,1]])
print(mat)

print(mat.T)

print(np.transpose(mat+1))

[[1 1 1]
 [1 1 1]]

[[1 1]
 [1 1]
 [1 1]]

[[2 2]
 [2 2]
 [2 2]]
```

- .T를 쓰면 단순 Transpose
- np.transpose 로 쓰면 뒤에 커스터마이징 가능

### 🛑내적

원소간의 곱(*)과 내적(dot)은 다른 연산자를 통해 제공합니다

원소간 곱(*)

```python
import numpy as np

mat = np.array([[1,2],[2,3]])

print(mat)

print(mat*mat)

[[1 2]
 [2 3]]

[[1 4]
 [4 9]]
```

- *을 사용하여 원소값 그대로 곱해 출력

내적 (dot)

```python
import numpy as np

mat = np.array([[1,2],[2,3]])

print(np.dot(mat,mat))

print(mat.dot(mat))

[[ 5  8]
 [ 8 13]]

[[ 5  8]
 [ 8 13]]
```

- [1,2],[2,3] 행렬의 곱

🛑대각합(trace)

- 2차원

```python
import numpy as np

mat = np.arange(16).reshape(4,4)

print(mat)

print(np.trace(mat))

[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]
 [12 13 14 15]]

30
```

- 16개 값을 4행4열로 reshape
- trace로 대각의 합을 구함  0 + 5 + 10 + 15 = 30

🛑대각합(trace)

- 3차원

```python
import numpy as np

mat = np.arange(27).reshape(3,3,3)

print(mat)

print(np.trace(mat))

[[[ 0  1  2]
  [ 3  4  5]
  [ 6  7  8]]

 [[ 9 10 11]
  [12 13 14]
  [15 16 17]]

 [[18 19 20]
  [21 22 23]
  [24 25 26]]]

[36 39 42]
```

- 27개의 스칼라를 3차원 3행 3열 배열로 생성
- 0+12+24 , 1+13+25 , 2+14+26

🛑 행렬식(Matrix Determinant)

<img src="https://github.com/KKYHH/Python/blob/main/numpy_image/%EC%8B%AC%ED%99%94_2.png?raw=true">

행렬식은 역행렬 존재 유무를 확인하는 방법

- 행렬식 값 0 : 역행렬 존재하지 않음
- 행렬식 값 0이 아닌 값 : 역행렬 존재

```python
import numpy as np

a = np.array([[1,2],[3,2]])
print(np.linalg.det(a))

-4.000000000000001
#이 형태는 부동소수점으로 인한 오차
#실제로는 -4 역행렬 존재
```

🛑역행렬 (np.linalg.inv(x))

역행렬은 n차 정방행렬(nxn) 행렬일 때만 존재한다

```python
import numpy as np

a = np.array([[1,2],[3,2]])

print(np.linalg.inv(a))

[[-0.5   0.5 ]
 [ 0.75 -0.25]]
```

- 복잡한 역행렬 구하는 공식을 (np.linalg.inv(x)) 로 쉽게 해결 가능

( 1 , 0 )

( 0 , 1 )   을 구하는 값

# 난수(random number)

### np.random.rand()

- rand method 는 0 이상 1 미만의 랜덤한 실수를 생성

```python
import numpy as np

test = np.random.rand()
print(test)

0.18282993073074427
# 랜덤으로 생성
```

```python
import numpy as np

test = np.random.rand(5)
print(test)

[0.81650347 0.13657487 0.32808204 0.68567279 0.18969086]
# 랜덤으로 생성
```

- rand method에 숫자를 넣어주면 넣은 값의 길이만큼 랜덤한 숫자생성하고 1차원 array로 반환

```python
import numpy as np

test = np.random.rand(2,2)
print(test)

[[0.42237999 0.86834293]
 [0.2759937  0.73618631]]
# 랜덤으로 생성
```

- rand method로 배열을 생성하고 각 위치에 random 값을 채운다

```python
import numpy as np

test = np.random.rand(2,2,2)
print(test)

[[[0.87531755 0.18204589]
  [0.05826932 0.44606548]]

 [[0.91361715 0.12589036]
  [0.11041485 0.99601462]]]
```

- 3차원 array도 가능

### np.random.randint (min,max)

- randint method는 min 이상 , max 미만인 범위에 있는 정수중 랜덤한 숫자를 return 해준다

```python
import numpy as np

test = np.random.randint(1,10)
print(test)

6
# 1- 10 중 랜덤으로 생성
```

```python
import numpy as np

test = np.random.randint(1,10,size=5)
print(test)

[3 8 3 5 6]
# 1 - 10 중 랜덤으로 생성
```

- size 옵션을 명시해주면 size에 명시된 길이인 1차원 array를 생성
- 값은 1 이상 10 미만인 범위의 정수들로 랜덤 생성

```python
import numpy as np

test = np.random.randint(1,10,size=(3,3))
print(test)

[[5 1 5]
 [3 4 9]
 [1 6 4]]
```

- size를 tuple의 형태로 명시하면 다차원 array도 생성 가능

### np.random.randn(n)

- randn method는 표준 정규분포 확률을 따르는 난수를 return
- 표준 정규분포란 평균을 0 표준편차를 1인 정규분포를 의미

```python
import numpy as np

a = np.random.randn(5)
print(a)

[-1.67389664 -0.69842338  0.71688883 -0.73575032  1.11873252]
```

```python
import numpy as np

a = np.random.randn(3,3)
print(a)

[[ 0.04863035 -1.58720033  0.36614019]
 [-0.1429111   0.0644318   0.35124639]
 [ 0.48843389 -1.19304103  0.98674531]]
```

- 정규분포를 따르는 3행3열 랜덤 배열을 만든다

### np.random.seed()

- random 모듈을 통한 난수 생성은 사실 엄격한 의미의 난수는 아니다
- 특정 시작 숫자를 정해주면 일정한 알고리즘에 의해 마치 난수처럼 보이는 수를 쏟아내는것
- 이러한 시작 숫자를 우리는 시드(seed) 라고 한다

이러한 원리를 통해 난수생성을 제어할 수 있다

즉 시드(seed)를 정해주는 것으로부터 예측 가능한 난수를 배열에 사용할 수 있는것입니다

```python
import numpy as np

np.random.seed(5)

a = np.random.randint(1,10,size=5)

print(a)

[4 7 7 1 9]

# random 함수이지만 seed value를 (5)로 고정시켜
# 같은 값인 [4 7 7 1 9]만 나온다
```

- seed는 간단하게 난수를 생성하는 세트의 번호다
- 동일한 seed value끼리는 동일한 세트의 난수를 갖고 있어서 어디서 실행해도 동일한 숫자를 return 한다
- * 단 seed value가 다르면 생성된 난수의 세트도 달라지므로 rand method로 인해 return된 숫자도 달라진다

# 상수

### numpy.inf

- 무한대의 IEEE 754 부동소수점 표현
- Inf,Infinity,PINF,infty 는 inf의 다른이름
- inf 사용을 권장

```python
import numpy as np

print(np.inf)
print(np.Inf)
print(np.Infinity)
print(np.PINF)
print(np.infty)

inf
inf
inf
inf
inf
```

### numpy.nan

- ‘Not a Number (Nan)’ 의 IEEE 754 부동소수점 표현
- (NaN,NAN은 nan과 같다 nan 사용 권장

```python
import numpy as np

print(np.nan)
print(np.NaN)
print(np.NAN)

nan
nan
nan
```

### numpy.NINF

- 음의 무한대의 IEEE 754 부동소수점 표현

```python
import numpy as np

print (np.NINF)

-inf
```

### numpy.NZERO

- 음의 0 (negative zero)의 IEEE 754 부동소수점 표현

```python
import numpy as np

print(np.NZERO)

-0.0
```

### numpy.PZERO

- 양의 0 (positive zero)의 IEEE 754 부동소수점 표현

```python
import numpy as np

print(np.PZERO)

0.0
```

### numpy.e

- 오일러 상수 (Euler’s constant), 자연로그의 밑, 네이피어 상수 (Napier’s constant)

```python
import numpy as np

print(np.e)

2.718281828459045
```

### numpy.euler_gamma

- 오일러-마스케로니 상수 (Euler-Mascheroni constant)

```python
import numpy as np

print(np.euler_gamma)

0.5772156649015329
```

### 🛑numpy.newaxis

- np 행렬의 차원을 확장하는 함수
- numpy array의 차원을 늘려준다
- 1D → 2D , 2D → 3D

<img src="https://github.com/KKYHH/Python/blob/main/numpy_image/%EC%8B%AC%ED%99%94_3.png?raw=true">
여러가지 상황에서 적재적소에 사용된다

- 1차원 array를 row vector나 column vector로 사용할 경우

```python
import numpy as np

a = np.arange(4)
print(a.shape)

(4,)
```

> x자리만 4 y는 공란
> 

```python
import numpy as np

a = np.arange(4)

row_vec = a[np.newaxis, :]
print(row_vec.shape)

(1, 4)
```

- 각 숫자에 []가 씌워진다

### [ np.newaxis, : ]

```python
import numpy as np

a = np.arange(4)

row_vec = a[np.newaxis, :]
print(row_vec.shape)
print(row_vec)

(1, 4)
[[0 1 2 3]]
```

- 1행4열 2차원 배열 생성 원래는 1차원 [0 1 2 3]

### [ : , np.newaxis]

```python
import numpy as np

a = np.arange(4)

col_vec = a[:, np.newaxis]
print(col_vec.shape)
print(col_vec)

(4, 1)
[[0]
 [1]
 [2]
 [3]]
```

- 4행1열 2차원 배열 생성

### 고차원으로 만들기

reshape

```python
import numpy as np

a = np.arange(5*5)

print(a)

a = np.arange(5*5).reshape(5,5)

print(a)

[ 0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
 24]

[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]
```

- 25개의 1차원 스칼라 출력
- 25개의 1차원 값을 5행5열로 reshape

```python
import numpy as np

a = np.arange(5*5).reshape(5,5)

print(a.shape)
print(a)

a2 = a[np.newaxis,...]
print(a2.shape)
print(a2)

[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]
(5, 5)

(1, 5, 5)
[[[ 0  1  2  3  4]
  [ 5  6  7  8  9]
  [10 11 12 13 14]
  [15 16 17 18 19]
  [20 21 22 23 24]]]
```

- 5행5열 배열인 a에 newaxis를 추가해 차원을 늘린다
- a [ np.newaxis , …] ( 5 , 5 ) 에서 앞에 차원이 더 생겼다 ( 1 , 5 , 5 )

```python
import numpy as np

a = np.arange(5*5).reshape(5,5)

print(a.shape)
print(a)

a2 = a[...,np.newaxis]
print(a2.shape)
print(a2)

(5, 5)

[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]

(5, 5, 1)

[[[ 0]
  [ 1]
  [ 2]
  [ 3]
  [ 4]]

 [[ 5]
  [ 6]
  [ 7]
  [ 8]
  [ 9]]

 [[10]
  [11]
  [12]
  [13]
  [14]]

 [[15]
  [16]
  [17]
  [18]
  [19]]

 [[20]
  [21]
  [22]
  [23]
  [24]]]
```

- 이번에는 ( 5 , 5 , 1 ) 뒤에 차원이 추가 되면서 5행 1열 배열을 5개의 차원으로 만든다

### np.reshape vs np.newaxis

reshape 와 newaxis의 기능은 비슷해 보일 순 있지만 다르다

reshape는 변환전 차원의 합과 변환후 차원의 합이 같아야 한다

```python
import numpy as np

a = np.arange(5*5).reshape(5,5)

print(a.shape)
print(a)

(5, 5)

[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]
```

- np.arange ( 5*5 ) = 25
- reshape (5,5 ) = 5행5열 = 25개의 스칼라

```python
import numpy as np

a = np.arange(5*5).reshape(4,5)

print(a.shape)
print(a)

ValueError: cannot reshape array of size 25 into shape (4,5)
```

- 25개의 스칼라가 4행5열로 만들어질 수가 없다

```python
import numpy as np

a = np.arange(5*4).reshape(4,5)

print(a.shape)
print(a)

(4, 5)

[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]]
```

- 20개의 스칼라가 4행5열로 만들어진다

### ‘ : ‘ 나 ‘ … ‘으로 위치를 정하지 않으면 디폴트는 열이다

```python
import numpy as np

a = np.arange(10)
a2 = a[np.newaxis]
print(a2.shape)
print(a2)

(1, 10)
[[0 1 2 3 4 5 6 7 8 9]]

# 10개의 데이터를 arange 하고
# newaxis로 1차원 행을 추가
```

```python
import numpy as np

a = np.arange(10)
a2 = a[np.newaxis,np.newaxis,np.newaxis]
print(a2.shape)
print(a2)

(1, 1, 1, 10)
[[[[0 1 2 3 4 5 6 7 8 9]]]]

# newaxis로 3차원 1개의 2차원 1행10열
```

```python
import numpy as np

a = np.arange(10)
a2 = a[np.newaxis,...,np.newaxis]
print(a2.shape)
print(a2)

(1, 10, 1)
[[[0]
  [1]
  [2]
  [3]
  [4]
  [5]
  [6]
  [7]
  [8]
  [9]]]

# newaxis로 2차원 1개의 10행1열 배열
```

```python
import numpy as np

a = np.arange(10)
a2 = a[...,np.newaxis,np.newaxis]
print(a2.shape)
print(a2)

(10, 1, 1)
[[[0]]

 [[1]]

 [[2]]

 [[3]]

 [[4]]

 [[5]]

 [[6]]

 [[7]]

 [[8]]

 [[9]]]

# newaxis로 2차원 10개의 1행1열 배열
```

### newaxis = None

newaxis는 None과 같다

newaxis말고 None을 써도 무방

```python
import numpy as np

a = np.arange(10)
a2 = a[...,None,None]
print(a2.shape)
print(a2)

(10, 1, 1)
[[[0]]

 [[1]]

 [[2]]

 [[3]]

 [[4]]

 [[5]]

 [[6]]

 [[7]]

 [[8]]

 [[9]]]

# newaxis = None
```
