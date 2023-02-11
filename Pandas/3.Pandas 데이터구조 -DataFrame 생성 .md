# Pandas DataFrame 생성

### DataFrame 구조

![Untitled](Pandas%20DataFrame%20%E1%84%89%E1%85%A2%E1%86%BC%E1%84%89%E1%85%A5%E1%86%BC%205db9515fc2b643eca7afe4b4ecec5c99/Untitled.png)

- DataFrame은 위 그림과 같이 Row , Column , Series 들로 구성
- 여기서 Series는 각 Column에 있는 데이터들을 의미

### DataFrame 기본형태

```python
import pandas as pd
df = pd.DataFrame( data , index , columns , dtype , copy)
```

- data - DataFrame 을 생성할 데이터
- index - 각 Row에 대해 Label 을 추가 ( 옵션 )
- columns - 각 Column 에 대해 Label 을 추가 ( 옵션 )
- dtype - 각 Column의 데이터 타입 명시 ( 옵션 )

### DataFrame 생성 예

- 1) List 를 사용한 DataFrame 생성

```python
import pandas as pd

data = [['Choi',22],['Kim',48],['Joo',32]]
df = pd.DataFrame(data,columns = ['Name','Age'])

print(df)

   Name  Age
0  Choi   22
1   Kim   48
2   Joo   32
```

- 2) dictionary를 사용한 DataFrame 생성

```python
import pandas as pd

data = {'Name' : ['Choi','Kim','Joo'], 'Age' : [22,48,32]}
df = pd.DataFrame(data)

print(df)

   Name  Age
0  Choi   22
1   Kim   48
2   Joo   32
```

- 3) index 와 columns를 사용한 DataFrame 생성

```python
import pandas as pd

data = [{'a':1 , 'b':2 , 'c':3},{'a':5 , 'b':7 , 'c':1}]
df = pd.DataFrame( data , index = ['First','Second'],columns=['a','b','c'])

print(df)

				a  b  c
First   1  2  3
Second  5  7  1
```

data의 이름,개수와 columns 이름 개수가 맞아야 한다 아닐 경우 NaN으로 표시   # index의 개수도 확인

- 4) numpy를 사용한 DataFrame 생성

```python
import pandas as pd
import numpy as np

data = np.array([[1,2,3],[4,5,6]])
df = pd.DataFrame( data ,index=['one','two'], columns=['co1','col2','col3'])

print(df)

			co1  col2  col3
one    1     2     3
two    4     5     6
```

np.array 2차원을 생성 대괄호 개수 [[]]

pd.DataFrame ( data ,  inex 와 columns 확인 )