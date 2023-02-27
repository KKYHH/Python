# 알고리즘_K-Nearest Neighbors

## KNeighborsClassifier()

`KNeighborsClassifier()`는 K-최근접 이웃 알고리즘을 사용하여 분류 모델을 만들기 위한 함수입니다. K-최근접 이웃 알고리즘은 새로운 데이터 포인트를 분류하기 위해 가장 가까운 K개의 이웃 데이터 포인트를 확인하고, 이 이웃들의 레이블을 참조하여 새 데이터 포인트의 레이블을 예측합니다.

KNeighborsClassifier() 함수는 다양한 하이퍼파라미터를 가지고 있으며, 이를 조정하여 모델 성능을 향상시킬 수 있습니다. 예를 들어, K 값은 이웃의 수를 조정하는데 사용되며, 더 작은 K 값은 모델의 유연성을 높이고 더 많은 노이즈를 수용할 수 있지만, 더 큰 K 값은 보다 안정적인 모델을 만들어 줍니다.

```
from sklearn.neighbors import KNeighborsClassifier

# KNeighborsClassifier 객체 생성
knn = KNeighborsClassifier(n_neighbors=5)

# 모델 학습
knn.fit(X_train, y_train)

# 예측
y_pred = knn.predict(X_test)

```

K-최근접 이웃 알고리즘의 장점과 단점은 다음과 같습니다.

### 장점

- 간단하고 직관적인 알고리즘으로, 이해하기 쉽습니다.
- 모델의 학습 시간이 없으며, 빠르게 예측을 수행할 수 있습니다.
- 비선형적인 결정 경계를 학습할 수 있습니다.

### 단점

- 모델의 예측 성능이 상대적으로 낮을 수 있습니다.
- 이상치(outlier)에 민감하게 반응합니다.
- 모델 튜닝이 어렵습니다.
- 데이터의 차원이 높아질수록 예측 성능이 떨어질 수 있습니다.

**K-최근접 이웃 알고리즘은 적은 양의 데이터에서는 높은 예측 성능을 발휘할 수 있지만, 데이터의 차원이 높아질수록 성능이 떨어지는 단점이 있습니다.**