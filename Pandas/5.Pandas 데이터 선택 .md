# Pandas 데이터 선택

## 배경

판다스의 DataFrame을 사용하다 보면, **조건에 따라 행동을 선택하고 싶은 경우**가 굉장히 많다

**SQL로 따지면, Select From Where 절**을 사용하는 느낌

판다스에선 조건에 따라 행들을 선택해 바로 데이터 프레임으로 볼 수 있다

또한, **조건에 따라 선택된 행들의 값을 바로 변경** 할 수 도 있다

## 1) DataFrame 만들기

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df)

               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

먼저 DataFrame을 하나 만든다

## 2) 열 선택하기

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df['A'])

print(type(df['A']))

2023-01-01    1.764052
2023-01-02    1.867558
2023-01-03   -0.103219
2023-01-04    0.761038
2023-01-05    1.494079
2023-01-06   -2.552990
Freq: D, Name: A, dtype: float64

<class 'pandas.core.series.Series'>
```

DataFrame의 하나의 열을 선택하면, 하나의 Series를 만든다

df [ ‘A’ ] = df.A

## 3) 행 선택하기

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df[0:3])

                A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
```

df [ 0:3 ] 으로 3행 까지 출력

인덱스를 직접 사용해서도 선택 가능

- df [’20230101’ : ‘20230103’]

## 4) 레이블로 선택하기 ( .loc )

### EX) - 1

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.loc[dates[1]])

A    1.867558
B   -0.977278
C    0.950088
D   -0.151357
Name: 2023-01-02 00:00:00, dtype: float64
```

레이블을 이용해서 1행의 데이터를 *횡 방향으로 얻습니다

### EX) - 2

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.loc[:,['A','B']])

               A         B
2023-01-01  1.764052  0.400157
2023-01-02  1.867558 -0.977278
2023-01-03 -0.103219  0.410599
2023-01-04  0.761038  0.121675
2023-01-05  1.494079 -0.205158
2023-01-06 -2.552990  0.653619
```

레이블을 이용해서 여러 축을 선택

- 전체 데이터 ( : ) 중 A와B 데이터를 출력

### EX) - 3

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.loc['20230102':'20230104',['A','B']])

                A         B
2023-01-02  1.867558 -0.977278
2023-01-03 -0.103219  0.410599
2023-01-04  0.761038  0.121675
```

### EX) - 4

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.loc['20230101',['A','B']])

A    1.764052
B    0.400157
Name: 2023-01-01 00:00:00, dtype: float64
```

### EX) - 5

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.loc[dates[3],['A']])

A    0.761038
Name: 2023-01-04 00:00:00, dtype: float64
```

### EX) - 6 스칼라 값 빠르게 출력

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.at[dates[0],'A'])

1.764052345967664
```

.at 를 이용하면 스칼라 값에 빠르게 접근 가능

## 5) 위치로 선택하기 ( .iloc )

### EX) - 1

iloc[3]을 입력하여 0,1,2,3 번째 20230104 행 을 선택해서 보여준다

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.iloc[3])

A    0.761038
B    0.121675
C    0.443863
D    0.333674
Name: 2023-01-04 00:00:00, dtype: float64

#
               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

### EX) - 2

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.iloc[3:5, 0:2])

               A         B
2023-01-04  0.761038  0.121675
2023-01-05  1.494079 -0.205158

#
               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

### EX) - 3

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.iloc[[1,2,4],[0,2]])

               A         C
2023-01-02  1.867558  0.950088
2023-01-03 -0.103219  0.144044
2023-01-05  1.494079  0.313068

#
               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

1행, 2행 ,4행 의 0열 2열 을 슬라이스

### EX) - 4

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.iloc[1:3,:])

               A         C
2023-01-02  1.867558  0.950088
2023-01-03 -0.103219  0.144044
2023-01-05  1.494079  0.313068

#
               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

1행부터3행까지 ( 1 , 2 ) 전체 슬라이스 ( : )

### EX) - 5

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.iloc[:,1:3])

               B         C
2023-01-01  0.400157  0.978738
2023-01-02 -0.977278  0.950088
2023-01-03  0.410599  0.144044
2023-01-04  0.121675  0.443863
2023-01-05 -0.205158  0.313068
2023-01-06  0.653619  0.864436

#
               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

( : ) 전체 행에서 1열부터3열까지 ( 1 , 2 ) 슬라이스

### EX) - 6

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.iloc[1,1])

-0.977277879876411

#
               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

iloc [ m , n ] 으로 해당 위치의 스칼라 값을 얻을 수 있다

### EX) - 7

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df.iat[1,1])

-0.977277879876411

#
               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-03 -0.103219  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
2023-01-06 -2.552990  0.653619  0.864436 -0.742165
```

값에 대한 빠른 접근 iat [ m , n ]

## 6) 불 인덱싱

### EX) - 1

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df[df.A>0])

               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558 -0.977278  0.950088 -0.151357
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079 -0.205158  0.313068 -0.854096
```

df 로 부터 A열이 0보다 큰 데이터를 보여줍니다

### EX) - 2

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

print(df[df > 0])

               A         B         C         D
2023-01-01  1.764052  0.400157  0.978738  2.240893
2023-01-02  1.867558       NaN  0.950088       NaN
2023-01-03       NaN  0.410599  0.144044  1.454274
2023-01-04  0.761038  0.121675  0.443863  0.333674
2023-01-05  1.494079       NaN  0.313068       NaN
2023-01-06       NaN  0.653619  0.864436       NaN
```

df > 0 조건이 성립하는 값을 DataFrame으로부터 선택한다

### EX) - 3

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

df2 = df.copy()
df2['E'] = ['one','one','two','wow','four','three']

print(df2[df2['E'].isin(['two','four'])])

                  A         B         C         D     E
2023-01-03 -0.103219  0.410599  0.144044  1.454274   two
2023-01-05  1.494079 -0.205158  0.313068 -0.854096  four
```

isin() 메서드를 이용해서 E열 값이 ‘two’ d와 ‘four’를 포함하는 경우를 필터링

## 7) 데이터 설정하기

### EX) - 1

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

s1 = pd.Series([1,2,3,4,5,6], index=pd.date_range('20230102',periods=6))
df['E'] = s1

print(df)

                  A         B         C         D    E
2023-01-01  1.764052  0.400157  0.978738  2.240893  NaN
2023-01-02  1.867558 -0.977278  0.950088 -0.151357  1.0
2023-01-03 -0.103219  0.410599  0.144044  1.454274  2.0
2023-01-04  0.761038  0.121675  0.443863  0.333674  3.0
2023-01-05  1.494079 -0.205158  0.313068 -0.854096  4.0
2023-01-06 -2.552990  0.653619  0.864436 -0.742165  5.0
```

새로운 열을 설정하면, 인덱스에 따라 데이터가 자동정렬

새로운 Series를 하나 만들고 DataFrame의 ‘E’ 열로 지정

### EX) - 2

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

s1 = pd.Series([1,2,3,4,5,6], index=pd.date_range('20230102',periods=6))
df['E'] = s1

df.at[dates[0],'A'] = 0
print(df)

                  A         B         C         D    E
2023-01-01  **0.000000**  0.400157  0.978738  2.240893  NaN
2023-01-02  1.867558 -0.977278  0.950088 -0.151357  1.0
2023-01-03 -0.103219  0.410599  0.144044  1.454274  2.0
2023-01-04  0.761038  0.121675  0.443863  0.333674  3.0
2023-01-05  1.494079 -0.205158  0.313068 -0.854096  4.0
2023-01-06 -2.552990  0.653619  0.864436 -0.742165  5.0
```

at과 레이블을 사용해서 값을 설정할 수 있다

### EX) - 3

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

s1 = pd.Series([1,2,3,4,5,6], index=pd.date_range('20230102',periods=6))
df['E'] = s1

df.iat[0,1] = 0
print(df)

                  A         B         C         D    E
2023-01-01  1.764052  0.000000  0.978738  2.240893  NaN
2023-01-02  1.867558 -0.977278  0.950088 -0.151357  1.0
2023-01-03 -0.103219  0.410599  0.144044  1.454274  2.0
2023-01-04  0.761038  0.121675  0.443863  0.333674  3.0
2023-01-05  1.494079 -0.205158  0.313068 -0.854096  4.0
2023-01-06 -2.552990  0.653619  0.864436 -0.742165  5.0
```

iat 과 위치 인덱스를 이용해서 값을 설정할 수 있다

### EX) - 4

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

s1 = pd.Series([1,2,3,4,5,6], index=pd.date_range('20230102',periods=6))
df['E'] = s1

df.loc[:,'D'] = np.array([5]*len(df))
print(df)

                   A         B         C  D    E
2023-01-01  1.764052  0.400157  0.978738  5  NaN
2023-01-02  1.867558 -0.977278  0.950088  5  1.0
2023-01-03 -0.103219  0.410599  0.144044  5  2.0
2023-01-04  0.761038  0.121675  0.443863  5  3.0
2023-01-05  1.494079 -0.205158  0.313068  5  4.0
2023-01-06 -2.552990  0.653619  0.864436  5  5.0
```

loc를 사용해서 Numpy 어레이를 할당함으로 값을 설정

- np.array([5]*len(df) = [ 5 5 5 5 5 5 ]

### EX) - 5

```python
import pandas as pd
import numpy as np

np.random.seed(0)

dates = pd.date_range('20230101',periods=6)
df = pd.DataFrame(np.random.randn(6,4),index=dates,columns=list('ABCD'))

s1 = pd.Series([1,2,3,4,5,6], index=pd.date_range('20230102',periods=6))
df['E'] = s1

df2 = df.copy()
df2[df2 > 0] = -df2
print(df2)

                  A         B         C         D    E
2023-01-01 -1.764052 -0.400157 -0.978738 -2.240893  NaN
2023-01-02 -1.867558 -0.977278 -0.950088 -0.151357 -1.0
2023-01-03 -0.103219 -0.410599 -0.144044 -1.454274 -2.0
2023-01-04 -0.761038 -0.121675 -0.443863 -0.333674 -3.0
2023-01-05 -1.494079 -0.205158 -0.313068 -0.854096 -4.0
2023-01-06 -2.552990 -0.653619 -0.864436 -0.742165 -5.0
```

DataFrame ( df2 ) 를 하나 만들고 0보다 큰 값들의 부호를 반대로 만든다

df2[df2 > 0] = -df2   # 뻬기가 아닌 부호 변경