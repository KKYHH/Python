# Pandas numpy로 변환

- 판다스와 넘파이는 서로 간단하게 변환이 가능
- 머신러닝 , 딥러닝에서는 numpy로 분석해야 연산의 속도가 빨라지기 때문에
- pandas로 기본 분석을 수행한 후 넘파이로 변환하여 머신러닝이나 딥러닝을 수행한다
- 반면 numpy는 데이터를 눈으로 확인하기 어려워 pandas로 변환하여 데이터를 확인한다

## pandas를 numpy로 변경하기     .to_numpy()

pandas로 데이터프레임 데이터를 불러온다

```python
import seaborn as sns
import pandas as pd

df = sns.load_dataset("iris")
print(df.head())

# head() 는 5개까지의 값을 불러온다

sepal_length  sepal_width  petal_length  petal_width species
0           5.1          3.5           1.4          0.2  setosa
1           4.9          3.0           1.4          0.2  setosa
2           4.7          3.2           1.3          0.2  setosa
3           4.6          3.1           1.5          0.2  setosa
4           5.0          3.6           1.4          0.2  setosa
```

이것을 .to_numpy()를 사용하면 간단히 numpy로 변경하여 불러올 수 있다

하지만 이 때 numpy로 변환하면 행과열 이름을 지정할 수 없다는것이 단점이다

.to_numpy로 numpy로 변환

```python
import seaborn as sns
import pandas as pd

df = sns.load_dataset("iris")

df_2 = df.to_numpy()
print(df_2)

[[5.1 3.5 1.4 0.2 'setosa']
 [4.9 3.0 1.4 0.2 'setosa']
 [4.7 3.2 1.3 0.2 'setosa']
 [4.6 3.1 1.5 0.2 'setosa']
 [5.0 3.6 1.4 0.2 'setosa']
 [5.4 3.9 1.7 0.4 'setosa']
 [4.6 3.4 1.4 0.3 'setosa']
 [5.0 3.4 1.5 0.2 'setosa']
 [4.4 2.9 1.4 0.2 'setosa']
 [4.9 3.1 1.5 0.1 'setosa']

....

```

## Numpy를 Pandas로 변경하기   pd.DataFrame

numpy로 리스트 행열을 불러온다

```python
import numpy as np

A = np.array([
    ['Minsoo','Minju','Yeomin','Hyeri','Junghun','Sunny','Bummee','Luna'],
    [33,25,19,25,32,36,23,36],
    ['M','W','W','W','M','W','M','W'],
    [91,50,69,98,72,85,43,61],
    [65,77,56,82,79,91,71,63],
    [30,95,64,88,34,69,15,25]
])

print(A)

[['Minsoo' 'Minju' 'Yeomin' 'Hyeri' 'Junghun' 'Sunny' 'Bummee' 'Luna']
 ['33' '25' '19' '25' '32' '36' '23' '36']
 ['M' 'W' 'W' 'W' 'M' 'W' 'M' 'W']
 ['91' '50' '69' '98' '72' '85' '43' '61']
 ['65' '77' '56' '82' '79' '91' '71' '63']
 ['30' '95' '64' '88' '34' '69' '15' '25']]
```

- index 없이 데이터 프레임 만들기 A

pd.DataFrame( )

```python
import numpy as np
import pandas as pd

A = np.array([
    ['Minsoo','Minju','Yeomin','Hyeri','Junghun','Sunny','Bummee','Luna'],
    [33,25,19,25,32,36,23,36],
    ['M','W','W','W','M','W','M','W'],
    [91,50,69,98,72,85,43,61],
    [65,77,56,82,79,91,71,63],
    [30,95,64,88,34,69,15,25]
])

df = pd.DataFrame(A)

print(df)

0      1       2      3        4      5       6     7
0  Minsoo  Minju  Yeomin  Hyeri  Junghun  Sunny  Bummee  Luna
1      33     25      19     25       32     36      23    36
2       M      W       W      W        M      W       M     W
3      91     50      69     98       72     85      43    61
4      65     77      56     82       79     91      71    63
5      30     95      64     88       34     69      15    25
```

pd.DataFrame( ) 는 numpy 그대로 데이터 프레임이 만들어진다

*행과 열을 뒤집고 싶을때는 아래처럼 하면 된다

- index 없이 데이터 프레임 만들기 B  (행과 열 전치하기)

```python
import numpy as np
import pandas as pd

A = np.array([
    ['Minsoo','Minju','Yeomin','Hyeri','Junghun','Sunny','Bummee','Luna'],
    [33,25,19,25,32,36,23,36],
    ['M','W','W','W','M','W','M','W'],
    [91,50,69,98,72,85,43,61],
    [65,77,56,82,79,91,71,63],
    [30,95,64,88,34,69,15,25]
])

df = pd.DataFrame(A.T)

print(df)

0   1  2   3   4   5
0   Minsoo  33  M  91  65  30
1    Minju  25  W  50  77  95
2   Yeomin  19  W  69  56  64
3    Hyeri  25  W  98  82  88
4  Junghun  32  M  72  79  34
5    Sunny  36  W  85  91  69
6   Bummee  23  M  43  71  15
7     Luna  36  W  61  63  25
```

.T 를 붙여서 행열 전치

- 특정 칼럼명을 사용하여 데이터프레임 만들기

위 A와B 코드의 경우 칼럼 이름을 지정하지 않아 0부터 5까지의 번호가 매겨진다

이때 특정 칼럼명으로 설정하고 싶다면 columns=[ ] 을 사용하여 칼럼명을 지정해줄 수 있다

```python
import numpy as np
import pandas as pd

A = np.array([
    ['Minsoo','Minju','Yeomin','Hyeri','Junghun','Sunny','Bummee','Luna'],
    [33,25,19,25,32,36,23,36],
    ['M','W','W','W','M','W','M','W'],
    [91,50,69,98,72,85,43,61],
    [65,77,56,82,79,91,71,63],
    [30,95,64,88,34,69,15,25]
])

df = pd.DataFrame(A.T , columns = ['name','age','sex','score1','score2','time'])

print(df)

name age sex score1 score2 time
0   Minsoo  33   M     91     65   30
1    Minju  25   W     50     77   95
2   Yeomin  19   W     69     56   64
3    Hyeri  25   W     98     82   88
4  Junghun  32   M     72     79   34
5    Sunny  36   W     85     91   69
6   Bummee  23   M     43     71   15
7     Luna  36   W     61     63   25
```