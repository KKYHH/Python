# Pandas 데이터구조 -Series 생성

| 차원 | 이름 | 설명 |
| --- | --- | --- |
| 1차원 | Series | 균일한 유형의 배열로 표시된 1차원 데이터 |
| 2차원 | DataFrame | 잠재적으로 이질적으로 유형이 지정된 열이있는
크기가 가변적인 테이블 형식의 2차원 데이터 |

Pandas 데이터 구조를 생각하는 좋은 방법은 더 낮은 차원의 데이터를 위한 유연한 컨테이너이다

- DataFrame은 Series의 컨테이너
- Series는 스칼라 컨테이너

### Pandas는 2개의 자료구조 ( Series , DataFrame )를 가지고 있습니다

> Series는 1차원 데이터 구조
> 

> DataFrame은 2차원 데이터 구조를 나타냅니다
> 

# 1 . Series

Series란?

- 1차원 데이터
- Index 와 Value 로 구성 (Python의 사전데이터와 유사)

### 1-1 Series 데이터 생성

- Python 자료형으로 생성가능 ( 리스트 , 튜플 , 사전 )
- Numpy array 자료형 생성가능

### 1-1-1 리스트로 Series 생성

```python
import pandas as pd

data = pd.Series([1,2,3,4])

print(data)

0    1
1    2
2    3
3    4
dtype: int64
```

### 1-1-2 튜플로 Series 생성

```python
import pandas as pd

data = pd.Series((1,2,3,4))

print(data)

0    1
1    2
2    3
3    4
dtype: int64
```

### 1-1-3 numpy.array로 Series 생성

```python
import pandas as pd
import numpy as np

data = pd.Series(np.array([1,2,3,4]))

print(data)

0    1
1    2
2    3
3    4
dtype: int64
```

위의 3가지 방법으로 생성한 Series를 보면 , `Value 값`(1,2,3,4)  `index 값` (0,1,2,3)으로 저장 되는 것을 확인

index를 key라고 한다면, key와 value로 이루어진 dict ( 사전 ) 타입과 비슷 하다는 점을 알 수 있습니다

### 1-1-4 사전 타입으로 Series 생성

```python
import pandas as pd

data = pd.Series({1:1 , 2:2 , 3:3 , 4:4})

print(data)

1    1
2    2
3    3
4    4
dtype: int64
```

1,2,3,4 라는 key값이 index로 저장되고 1,2,3,4 라는 데이터가 value로 저장되는 것을 확인

- method를 통해 index와 value 값을 따로 가져 올 수도 있다

index 값 가져오기

```python
import pandas as pd

data = pd.Series({1:1 , 2:2 , 3:3 , 4:4})

print(data.index)

Int64Index([1, 2, 3, 4], dtype='int64')
```

value 값 가져오기

```python
import pandas as pd

data = pd.Series({1:1 , 2:2 , 3:3 , 4:4})

print(data.values)

[1 2 3 4]
```

위 결과들을 보면 “dtype = int64” 라는 구문을 볼 수 있다

int형 외에 다른 자료형들도 Series에 저장된다

### 1-1-5 여러 자료형으로 Series 생성

```python
import pandas as pd

data = pd.Series(['info','KYH',93])

print(data)
print(data.dtypes)

0    info
1     KYH
2      93
dtype: object

object
```

문자열을 포함한 숫자가 아닌 형태의 자료형이 Series에 저장되면

Object type으로 저장되는 것을 확인 할 수 있다

### 1-2 Series의 index

- 사전형으로 Series를 생성하면 사전형의 key값이 index로 저장
- 사전형이 아닌 데이터로 Series 생성할 때 index를 명시적으로 입력 가능
- 입력값이 없다면 0부터 순서대로 번호를 부여

### 1-2-1 Series 생성시에 Index명 입력

```python
import pandas as pd

data = pd.Series(['토트넘','손흥민',30], index = ['팀명','선수명','골수'])
data2 = pd.Series(['토트넘','손흥민',30])

print(data)
print(data2)

팀명     토트넘
선수명    손흥민
골수      30
dtype: object

0    토트넘
1    손흥민
2     30
dtype: object
```

index 로 키 값을 설정한 data

입력값없이 0부터 부여된 data2

dtype : object

### 1-3 Series 의 조회

Series의 데이터를 조회하는 기법에 대해 알아본다

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data)

서울    1
대전    2
대구    3
부산    4
광주    5
전주    6
충주    7
마산    8
성남    9
dtype: int64
```

### 1-3-1 index 기준으로 조회 (색인)

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data.at['서울'])

1
```

키값인 index의 서울을 조회해서 1을 출력

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data[['서울','부산']])

서울    1
부산    4
dtype: int64
```

 [] 로 감싸 두개를 출력

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data[0:2])

서울    1
대전    2
dtype: int64
```

0부터 2까지의 리스트를 출력 

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data[-3:])

충주    7
마산    8
성남    9
dtype: int64
```

끝에서 3개 까지  :

### 1-3-2 index 조건 색인

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data.index.isin(['서울','대전','대구','전주']))

[ True  True  True False False  True False False False ]
```

isin 함수 인자에 해당하는 index만 True 값을 갖고 출력

### 1-3-3 조건으로 조회

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data>3)

서울    False
대전    False
대구    False
부산     True
광주     True
전주     True
충주     True
마산     True
성남     True
dtype: bool
```

value 가 3 보다 큰 데이터만 조회해서 True로 출력

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data[data>3])

부산    4
광주    5
전주    6
충주    7
마산    8
성남    9
dtype: int64
```

True 인 데이터만 조회

## 1-4 Series의 산술 연산 및 통계

### 1-4-1 상수와의 연산

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data+10)

서울    11
대전    12
대구    13
부산    14
광주    15
전주    16
충주    17
마산    18
성남    19
dtype: int64
```

모든 데이터에 value를 +10 하기

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

print(data.add(10))

서울    11
대전    12
대구    13
부산    14
광주    15
전주    16
충주    17
마산    18
성남    19
dtype: int64
```

.add()로 value 에 추가

### 1-4-2 Series 끼리의 연산

- 두 Series의 같은 index 끼리 연산함
- 같은 index가 없을 경우 NaN으로 저장됨

위 값과 계산을 위해 새로운 data2 생성

```python
import pandas as pd

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])
print(data2)

서울    10
대전    20
대구    30
dtype: int64
```

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])

data3 = data + data2
print(data3)

광주     NaN
대구    33.0
대전    22.0
마산     NaN
부산     NaN
서울    11.0
성남     NaN
전주     NaN
충주     NaN
dtype: float64
```

위 과정을 보면 같은 index 끼리만 연산을 수행한다

동일 index가 없는 경우 NaN이 된다

NaN은 데이터가 없다는 뜻으로 타언어의 Null과 동일한 개념

### 1-5 NaN 데이터 처리

- fill_value 옵션 : NaN 데이터를 입력값으로 적용후에 함수 적용
- fillna 함수 : NaN 값을 입력값으로 변경

fill_value=

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])

print(data.add(data2,fill_value=0))

# 숫자를 바꾸면 특정값 변경

광주     5.0
대구    33.0
대전    22.0
마산     8.0
부산     4.0
서울    11.0
성남     9.0
전주     6.0
충주     7.0
dtype: float64
```

add 와 같은 산술연산함수를 적용 할 때 fill_value 옵션을 쓰면

NaN이 발생할 경우 특정 값으로 대입이 가능

fillna()

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])

data3 = data+data2

print(data3.fillna(0))
# 1로 바꾸면 1 2로 바꾸면 2로 NaN 값이 변경

광주     0.0
대구    33.0
대전    22.0
마산     0.0
부산     0.0
서울    11.0
성남     0.0
전주     0.0
충주     0.0
dtype: float64
```

Series에 NaN 값이 있을 경우 fillna를 이용해 NaN을 입력값으로 변경 가능

### 1-6 통계

- describe 함수 : 주요 통계 정보 보기
- mean 함수 : 평균 구하기
- std 함수 : 표준편차 구하기

기존의 data

```python

import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])

print(data)

서울    1
대전    2
대구    3
부산    4
광주    5
전주    6
충주    7
마산    8
성남    9
dtype: int64
```

data.describe() 통계정보 보기

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])

print(data.describe())

count    9.000000
mean     5.000000
std      2.738613
min      1.000000
25%      3.000000
50%      5.000000
75%      7.000000
max      9.000000
dtype: float64
```

data.mean() 통계의 평균 구하기

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])

print(data.mean())

5.0
```

data.std() 표준편차 구하기

```python
import pandas as pd

data = pd.Series([1,2,3,4,5,6,7,8,9], index = ['서울','대전','대구','부산','광주','전주','충주','마산','성남'])

data2 = pd.Series([10,20,30],index = ['서울','대전','대구'])

print(data.std())

2.7386127875258306
```