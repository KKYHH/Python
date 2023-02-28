# [sklearn] OneHotEncoder

# sklearn의 OneHotEncoder

**OneHotEncoder**는 Scikit-learn 라이브러리에서 제공하는 데이터 전처리(preprocessing) 도구 중 하나로, **범주형(categorical)** **데이터를 수치형(numerical)** 데이터로 변환해주는 역할을 합니다.

예를 들어, "색깔"이라는 feature가 있고 그 값으로 "빨간색", "파란색", "노란색" 등이 있다면, 

이 feature을 그대로 머신러닝 모델에 넣을 수는 없습니다. 

따라서, 이런 경우에 OneHotEncoder를 사용하여 "빨간색"을 [1, 0, 0], "파란색"을 [0, 1, 0], "노란색"을 [0, 0, 1]와 같이 수치형으로 변환해줍니다.

## OneHotEncoder의 사용 방법

OneHotEncoder를 사용하기 위해서는 다음과 같은 과정을 거쳐야 합니다.

1. 범주형 데이터를 가진 feature을 선택합니다.
2. 해당 feature을 OneHotEncoder에 적용합니다.
3. **fit_transform()** 메서드를 사용하여 feature을 변환합니다.

아래는 예시 코드입니다.

```python
from sklearn.preprocessing import OneHotEncoder

# 범주형 데이터를 가진 feature을 선택합니다.
categorical_feature = [['빨간색'], ['파란색'], ['노란색']]

# OneHotEncoder에 적용합니다.
encoder = OneHotEncoder()
encoder.fit(categorical_feature)

# fit_transform() 메서드를 사용하여 feature을 변환합니다.
transformed_feature = encoder.transform(categorical_feature).toarray()

print(transformed_feature)

```

위 코드를 실행하면 다음과 같은 출력 결과가 나타납니다.

```python
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]

```

위와 같이 OneHotEncoder를 사용하여 범주형 데이터를 수치형 데이터로 변환할 수 있습니다.