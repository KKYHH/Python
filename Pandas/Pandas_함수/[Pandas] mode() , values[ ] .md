# [Pandas] mode() , values[ ]

# Pandas mode()

Pandas의 **mode()** 함수는 데이터프레임에서 **최빈값(mode)을 계산하는 함수**입니다. 

최빈값이란 데이터에서 가장 자주 나타나는 값을 의미합니다.

## 사용법

```python
import pandas as pd

# 데이터프레임 생성
df = pd.DataFrame({'col1': [1, 2, 3, 3, 4, 5],
                   'col2': [1, 2, 2, 3, 3, 3]})

# 각 컬럼별 최빈값 구하기
mode_col1 = df['col1'].mode()
mode_col2 = df['col2'].mode()

print('col1의 최빈값:', mode_col1)
print('col2의 최빈값:', mode_col2)

```

위 코드에서는 Pandas를 이용하여 데이터프레임을 생성한 후, 각 컬럼별 최빈값을 구하는 방법을 보여줍니다.

## 결과

```python
col1의 최빈값: 0    3
dtype: int64
col2의 최빈값: 0    3
dtype: int64

```

위 코드를 실행하면 col1의 최빈값은 3, col2의 최빈값은 3이 출력됩니다.

### Tip

위에서 0이 같이 출력 되는 이유는 series 형태이기 때문입니다

**.mode()** 메서드는 series 에서 가장 자주 나타나는 값을 포함한 series 객체를 반환합니다

series 객체는 index 와 함께 반환되며 , 값이 여러 개일 경우 가장 앞에 있는 값을 기준으로 반환합니다

col1 과 co12 의 값은 하나인 3이기 때문에 0번 index가 같이 나오는것

```python
mode_col1 = df['col1'].mode().values[0]
print(mode_col1)
```

```python
3
```

.values 는 series의 값들을 배열 형태로 반환한다

따라서 `.mode().values[0]`를 사용하면, 시리즈에서 가장 자주 나타나는 값을 배열 형태로 반환하고, 이 배열에서 첫 번째 값(가장 자주 나타나는 값 중 가장 작은 값)을 선택하게 됩니다.

# [Pandas] values[ ]

Pandas의 데이터프레임에서 **.values**를 사용하면, 데이터프레임의 값들을 **배열(array) 형태로 변환**할 수 있습니다.

## 사용법

```python
import pandas as pd

# 데이터프레임 생성
df = pd.DataFrame({'col1': [1, 2, 3],
                   'col2': [4, 5, 6],
                   'col3': [7, 8, 9]})

# values 속성으로 데이터프레임의 값들을 배열로 확인
arr = df.values

print(arr)

```

위 코드에서는 Pandas를 이용하여 데이터프레임을 생성한 후, **.values**를 사용하여 데이터프레임의 값들을 배열로 확인하는 방법을 보여줍니다.

## 결과

```python
array([[1, 4, 7],
       [2, 5, 8],
       [3, 6, 9]], dtype=int64)

```

위 코드를 실행하면 2차원 배열 형태로 데이터프레임의 값들이 출력됩니다.

### Tip

**.values**를 사용하면, 데이터프레임의 값들을 **numpy 배열**로 변환할 수 있습니다.

그러나, 데이터프레임의 값들이 **같은 자료형을 가지고 있지 않을 경우**에는 **object type**으로 변환되어 데이터프레임보다 **메모리 사용량이 더 많아**집니다.

또한, **.values**를 사용하여 배열로 변환한 후, **인덱스와 컬럼명이 함께 삭제**되므로 주의해야 합니다.