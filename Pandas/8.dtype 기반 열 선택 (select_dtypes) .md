# dtype 기반 열 선택 (select_dtypes)

### DataFrame.select.dtypes ( include =None , exclude =None)

### 개요

select_dtypes 함수는 열에 포함된 데이터들을 type 기준으로 인덱싱 할 수 있도록 한다

select_dtypes( include = None, exclude = None ) 형태를 가지며

include 에 넣은 값을 포함하고 exclude에 넣은 값을 제외한

columns (열)을 DataFrame 형태로 변환

### 기본 사용법

**df.dtypes**

*include 및 exclude는 비어있거나 겹치면 안되며 ( 에러 발생 ), 스칼라나 list 형태의 입력 값이 가능합니다

### 자료형

1. 숫자형(numeric)은 np.number 또는 ‘number’
2. 문자형(str)은 ‘object’
3. 날짜,시간 ( datetimes) 을 선택하려면 np.datetime64, ‘datetime’ 또는 ‘datetime64’
4. timedeltas 는 np.timedelta64 , ‘timdedelta’ or ‘timedelta64’
5. Pandas 의 categorical 타입은 ‘category’

### EX)

먼저 4X5 행렬을 만들어 본다 

```python
import pandas as pd

col1 = [1,2,3,4,5]
col2 = ['one','two','three','four','five']
col3 = [1.5,2.5,3.5,4.5,5.5]
col4 = [True,False,False,True,True]

df = pd.DataFrame({"col1":col1,"col2":col2,"col3":col3,"col4":col4})

print(df)
print(df.dtypes)

col1   col2  col3   col4
0     1    one   1.5   True
1     2    two   2.5  False
2     3  three   3.5  False
3     4   four   4.5   True
4     5   five   5.5   True

col1      int64
col2     object
col3    float64
col4       bool
dtype: object
```

`col1` 은 숫자 `col2` 는 문자 `col3` 은 float `col4` 는 bool의 dtype을 가진다

### include 사용

- include에 포함될 type을 입력함으로써, 해당 type인 열만 반환하는것이 가능하다

```python
import pandas as pd

col1 = [1,2,3,4,5]
col2 = ['one','two','three','four','five']
col3 = [1.5,2.5,3.5,4.5,5.5]
col4 = [True,False,False,True,True]

df = pd.DataFrame({"col1":col1,"col2":col2,"col3":col3,"col4":col4})

result = df.select_dtypes(include=[float,bool])
print(result)

col3   col4
0   1.5   True
1   2.5  False
2   3.5  False
3   4.5   True
4   5.5   True
```

df 안에 dtypes가 float인 `col3` 과 dtypes가 bool인 `col4` 만 출력

### exclude 사용

- exclude에 제외할 type을 입력함으로써, 해당 type인 열만 제외하여 반환하는것이 가능

```python
import pandas as pd

col1 = [1,2,3,4,5]
col2 = ['one','two','three','four','five']
col3 = [1.5,2.5,3.5,4.5,5.5]
col4 = [True,False,False,True,True]

df = pd.DataFrame({"col1":col1,"col2":col2,"col3":col3,"col4":col4})

result = df.select_dtypes(exclude=['int64'])
print(result)

col2  col3   col4
0    one   1.5   True
1    two   2.5  False
2  three   3.5  False
3   four   4.5   True
4   five   5.5   True
```

df 안에 dtypes가 ‘int64’ 인 `col1` 을 제외한 나머지 출력

### include & exclude 혼합 사용

- include 에 포함될 type을 , exclude에 제외할 type을 입력하여
혼용 인덱싱이 가능