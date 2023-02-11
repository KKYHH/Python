# *마스킹을 이용한 다중조건 AND , OR , NOT

Pandas 에서 AND , OR , NOT 을 사용해

여러 조건을 가지고 행을 추출 하는 방법

|           조건 |            식 |
| --- | --- |
|          and |            & |
|           or |             | |
|          not |            ~ |

DataFrame 테스트 데이터

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample_data.csv')

print(df)

			name  age state  point
0    Alice   24    NY     64
1      Bob   42    CA     92
2  Charlie   18    CA     70
3     Dave   68    TX     70
4    Ellen   24    CA     88
5    Frank   30    NY     57
```

### 행 추출 방법

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample_data.csv')

mask = [True,False,True,False,True,False]
df_mask = df[mask]
print(df_mask)

			name  age state  point
0    Alice   24    NY     64
2  Charlie   18    CA     70
4    Ellen   24    CA     88
```

조건문이 아닌 True 와 False를 직접 지정하면

True 행만 표시  0 , 2 , 4

### 복수 조건 설정

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample_data.csv')

print(df['age'] < 35)

0     True
1    False
2     True
3    False
4     True
5     True
Name: age, dtype: bool
```

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample_data.csv')

print(~(df['state'] == 'NY'))

0    False
1     True
2     True
3     True
4     True
5    False
Name: state, dtype: bool
```

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample_data.csv')

print((df['age'] < 35 ) & ~(df['state'] == 'NY'))

0    False
1    False
2     True
3    False
4     True
5    False
dtype: bool
```

‘age’ 가 35 보다 어리면서 ‘state’가 ‘NY’가 아닌것

2 , 4

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample.csv')

df_and =df[(df['age'] < 35 ) & ~(df['state'] == 'NY')]
print(df_and)

#데이터 출력

name  age state  point
2  Charlie   18    CA     70
4    Ellen   24    CA     88
```

OR 조건도 사용 방법 동일

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample.csv')

df_and =df[(df['age'] < 35 ) & ~(df['state'] == 'NY')]
df_or = df[(df['age'] < 20) | (df['point'] > 90 )]

print(df_or)

#데이터 출력

name  age state  point
1      Bob   42    CA     92
2  Charlie   18    CA     70
```

### 연산자 우선 순위

조건이 3개 이상인 경우에는 연산자 우선순위를 주의해야한다

우선 순위가 높은 순서로는

**NOT ( ~ ) , AND ( & ) , OR ( | )** 입니다

따라서 순서에 따라 결과가 달라진다

```python
import pandas as pd
import numpy as np

df = pd.read_csv('/Users/kyhh/Desktop/pandas_sample.csv')

df_multi = df[(df['age'] < 35) | ~ (df['state'] == 'NY') & (df['point'] < 75)]

df_multi2 = df[(df['age'] < 35) & (df['point'] < 75) | ~(df['state'] == 'NY')]

print(df_multi)
print(df_multi2)

# 데이터 출력

name  age state  point
0    Alice   24    NY     64
2  Charlie   18    CA     70
3     Dave   68    TX     70
4    Ellen   24    CA     88
5    Frank   30    NY     57

      name  age state  point
0    Alice   24    NY     64
1      Bob   42    CA     92
2  Charlie   18    CA     70
3     Dave   68    TX     70
4    Ellen   24    CA     88
5    Frank   30    NY     57
```