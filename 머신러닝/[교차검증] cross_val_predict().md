# [교차검증] cross_val_predict()

# 만든 모델을 통해 예측한 값들을 불러와 원하는평가 계산 방법을 적용할 수 있도록 사용

# cross_val_predict() 함수란?

`cross_val_predict()`는 scikit-learn 패키지에서 제공하는 교차 검증을 수행하는 함수 중 하나입니다. 이 함수는 데이터를 분할하여 모델 학습 및 예측을 수행하고, 예측 결과를 반환합니다.

## 언제 사용하나요?

`cross_val_predict()` 함수는 모델의 예측 성능을 평가하고, 과적합 문제를 방지하기 위해 사용됩니다. 이 함수는 일반적으로 모델을 학습하고 예측하기 전에 모델의 성능을 미리 예측하고자 할 때 사용됩니다.

## 어떻게 사용하나요?

`cross_val_predict()` 함수는 다음과 같은 방식으로 사용됩니다.

```python
from sklearn.model_selection import cross_val_predict
from sklearn.linear_model import LinearRegression

model = LinearRegression()
X = [[0, 0], [1, 1], [2, 2], [3, 3]]
y = [0, 1, 2, 3]

y_pred = cross_val_predict(model, X, y, cv=3)

```

위 코드에서 `model`은 학습할 모델을, `X`는 특성 행렬, `y`는 레이블 벡터입니다. `cv`는 교차 검증을 수행할 폴드 수를 나타냅니다.

`cross_val_predict()` 함수는 각 폴드에 대해 학습된 모델을 사용하여 예측을 수행하고, 예측 결과를 반환합니다. 이 예측 결과는 모델의 예측 성능을 평가하는 데 사용될 수 있습니다.

## 왜 사용하나요?

`cross_val_predict()` 함수를 사용하면 모델의 예측 성능을 미리 예측하고, 과적합 문제를 방지할 수 있습니다. 또한 이 함수를 사용하면 교차 검증을 수행할 때마다 예측 결과를 반환하여 모델의 예측 성능을 보다 정확하게 파악할 수 있습니다.