# [Pandas] .value_counts()

# `.value_counts()` 메서드

Pandas에서 제공하는 `.value_counts()` 메서드는 데이터프레임의 열(column)에서 고유값(unique value)의 출현 빈도수를 계산하여 반환해주는 메서드입니다. 이를 통해 해당 열에 어떤 유형의 데이터가 있는지, 각 유형이 얼마나 많은지에 대한 정보를 제공할 수 있습니다.

`.value_counts()` 메서드는 주로 카테고리형 데이터(categorical data)에 대한 분석에 많이 사용됩니다. 또한, 막대 그래프(bar plot)나 파이 차트(pie chart)와 같은 시각화 작업을 수행하기 전에 해당 열의 데이터 분포를 빠르게 파악할 수 있는 유용한 도구입니다.

다음은 `.value_counts()` 메서드를 사용하여 'fruit' 열에서 각 과일이 출현한 빈도수를 계산하는 예시 코드입니다.

```python
import pandas as pd

df = pd.DataFrame({'fruit': ['apple', 'banana', 'apple', 'orange', 'banana', 'banana']})

fruit_counts = df['fruit'].value_counts()

print(fruit_counts)

```

위 코드를 실행하면 다음과 같은 결과가 출력됩니다.

```python
banana    3
apple     2
orange    1
Name: fruit, dtype: int64

```

즉, 'banana'가 3번, 'apple'이 2번, 'orange'가 1번 출현했다는 것을 알 수 있습니다.

`.value_counts()` 메서드는 매우 유용한 기능이지만, **데이터프레임의 크기가 매우 큰 경우에는 계산에 시간이 오래 걸릴 수 있습니다.** 따라서, 이를 사용하기 전에 데이터프레임의 크기와 열의 수를 고려하여 사용하는 것이 좋습니다.