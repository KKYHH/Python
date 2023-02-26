# sklearn - score()

# sklearn - score() 메서드

`score()` 메서드는 머신러닝 모델에서 모델의 성능을 평가하는 데 사용됩니다. 이 메서드는 모델이 예측한 결과와 실제 결과를 비교하여 정확도를 계산합니다.

예를 들어, 붓꽃 데이터를 사용하여 붓꽃의 품종을 예측하는 머신러닝 모델을 만들었다고 가정해봅시다. 우리는 이 모델의 성능을 평가하고 싶습니다. 이 때 `score()` 메서드를 사용하여 모델의 정확도를 평가할 수 있습니다.

```
from sklearn.datasets import load_iris
from sklearn.tree import DecisionTreeClassifier

iris = load_iris()
X = iris.data
y = iris.target

model = DecisionTreeClassifier()
model.fit(X, y)

accuracy = model.score(X, y)
print("모델의 정확도는:", accuracy)

```

위의 예제에서는 `DecisionTreeClassifier()`를 사용하여 붓꽃 데이터를 학습시키는 모델을 만들고, `score()` 메서드를 사용하여 모델의 정확도를 계산합니다. 결과는 모델의 정확도가 출력됩니다.

이러한 방식으로 `score()` 메서드를 사용하여 머신러닝 모델의 성능을 간단하게 평가할 수 있습니다.