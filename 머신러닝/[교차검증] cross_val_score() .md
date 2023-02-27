# [교차검증] cross_val_score()

# 평가지표로 계산된 스코어에 대한 정보들을 확인하는 방법

# cross_val_score()란 무엇인가?

`cross_val_score()`는 Scikit-learn의 교차 검증을 위한 함수 중 하나입니다. 이 함수는 주어진 데이터셋을 'k'개의 fold로 분할하고, 각 fold에서 모델을 학습시키고 검증하는 과정을 'k'번 반복하여 모델의 성능을 평가합니다.

## cross_val_score() 사용법

다음은 `cross_val_score()` 함수를 사용하는 방법입니다.

```python
from sklearn.model_selection import cross_val_score
scores = cross_val_score(estimator, X, y, cv=k)

```

여기서 `estimator`는 모델을 나타내는 객체이고, `X`와 `y`는 각각 특징과 레이블을 나타내는 데이터셋입니다. `cv`는 fold의 수를 결정하는데 사용됩니다.

## cross_val_score() 출력값

`cross_val_score()`는 모델의 성능을 나타내는 점수를 반환합니다. 이 점수는 'k'개의 fold에서 얻은 검증 점수를 평균한 값입니다. 출력값으로 여러 개의 점수가 반환되는데, 이는 'k'개의 fold에서 얻은 검증 점수를 나타내며, 모델의 성능을 측정하는 데 사용됩니다.

## cross_val_score()의 장점

`cross_val_score()`를 사용하면 모델의 성능을 더욱 정확하게 예측할 수 있습니다. 이 함수를 사용하면 overfitting을 방지하고, 모델이 일반화될 수 있도록 합니다. 이를 통해 모델의 신뢰도를 높일 수 있습니다.

## cross_val_score() 단점

`cross_val_score()` 함수의 가장 큰 단점 중 하나는 계산 비용입니다. 이 함수는 모델을 학습시키고 검증하는 과정을 'k'번 반복하기 때문에 계산 비용이 매우 높을 수 있습니다. 또한, 이 함수는 분류 모델에서는 accuracy를, 회귀 모델에서는 R-squared를 평가 지표로 사용하기 때문에, 이러한 지표가 모델의 성능을 정확하게 평가하지 못할 수 있습니다.

## 주요 매개변수

`cross_val_score()` 함수는 다양한 매개변수를 가지고 있습니다. 이 중에서 가장 중요한 매개변수는 다음과 같습니다.

- `estimator`: 모델을 나타내는 객체입니다.
- `X`: 특징을 나타내는 데이터셋입니다.
- `y`: 레이블을 나타내는 데이터셋입니다.
- `cv`: fold의 수를 결정하는데 사용됩니다.

## 예제

`cross_val_score()` 함수를 사용하여 붓꽃(iris) 데이터셋을 사용하여 분류 모델을 평가하는 예제를 살펴보겠습니다.

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import cross_val_score
from sklearn.tree import DecisionTreeClassifier

iris = load_iris()
X = iris.data
y = iris.target

clf = DecisionTreeClassifier()
scores = cross_val_score(clf, X, y, cv=5)

print('Cross-validation scores:', scores)

```

위 코드에서는 붓꽃 데이터셋을 불러오고, `DecisionTreeClassifier()` 모델을 사용하여 분류 모델을 만들고 있습니다. 그리고 `cross_val_score()` 함수를 사용하여 모델을 평가하고 있습니다. 출력값으로는 5개의 fold에서 얻은 검증 점수가 출력됩니다.

```python
Cross-validation scores: [0.96666667 1.         0.9        0.96666667 1.]
```

## 결론

`cross_val_score()` 함수는 모델의 성능을 더욱 정확하게 예측할 수 있도록 도와주는 함수입니다. 이 함수를 사용하면 overfitting을 방지하고, 모델이 일반화될 수 있도록 합니다. 이를 통해 모델의 신뢰도를 높일 수 있습니다.

## 코드 해석

이 코드는 붓꽃 데이터셋을 `Decision Tree` 분류기로 5-fold cross-validation을 수행하여 각 fold에 대한 정확도 점수를 출력하는 코드입니다.

실행 결과로는 5개의 fold에 대한 정확도 점수가 출력됩니다. 예를 들어 아래와 같은 출력이 나올 수 있습니다:

```python
lessCopy code
Cross-validation scores: [0.96666667 0.96666667 0.9        0.96666667 1.]
```

위 결과에서 보이는 것처럼, 각 fold에 대한 정확도 점수가 **0.9에서 1.0 사이의 값으로 나타납니다** 이는 각 fold에서 모델이 얼마나 잘 예측했는지를 나타내는 평균 정확도입니다.

이 점수들은 모델이 각 fold에서 학습 데이터와 테스트 데이터를 어떻게 분리했느냐에 따라 다를 수 있습니다. 5-fold cross-validation은 데이터를 5개의 fold로 나누어서, 각각의 fold를 테스트 데이터로 사용하고 나머지를 학습 데이터로 사용하는 방법입니다. 이를 통해 모델이 일반화 성능을 어느 정도 가지는지를 평가할 수 있습니다.