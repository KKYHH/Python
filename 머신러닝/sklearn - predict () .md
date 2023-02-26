# sklearn - predict ()

# sklearn의 predict() 메서드란?

`predict()` 메서드는 `sklearn` 라이브러리의 주요 메서드 중 하나입니다. 이 메서드는 모델에 새로운 데이터를 입력하면 모델이 예측한 출력 값을 반환합니다.

예를 들어, 붓꽃 종을 분류하는 모델을 학습시킨 후, 새로운 붓꽃의 꽃잎과 꽃받침의 길이와 너비 값을 입력하면, `predict()` 메서드를 이용하여 해당 붓꽃의 종을 예측할 수 있습니다.

## 예시

다음은 `sklearn`의 `KNeighborsClassifier` 모델을 이용하여 붓꽃 데이터를 분류하는 예시 코드입니다.

```
from sklearn.datasets import load_iris
from sklearn.neighbors import KNeighborsClassifier

# 붓꽃 데이터 로드
iris = load_iris()

# 데이터와 라벨 분리
X = iris.data
y = iris.target

# 모델 생성
knn = KNeighborsClassifier(n_neighbors=3)

# 모델 학습
knn.fit(X, y)

# 새로운 샘플 데이터
new_sample = [[5.1, 3.5, 1.4, 0.2]]

# 예측
prediction = knn.predict(new_sample)
print(prediction)  # 붓꽃 종 중 하나인 0, 1, 2 중 하나의 값을 출력합니다.

```

위 코드에서 `predict()` 메서드는 `new_sample` 변수에 저장된 데이터를 이용하여 붓꽃의 종을 예측합니다. `knn.predict(new_sample)` 코드는 붓꽃 종 중 하나인 0, 1, 2 중 하나의 값을 반환합니다.

- 새로운 샘플 데이터인 **`new_sample`**의 특성 값들은 각각 꽃잎 길이, 꽃잎 너비, 꽃받침 길이, 꽃받침 너비를 나타내고, 이 값을 이용하여 **`knn.predict(new_sample)`** 메서드를 호출하면, 알고리즘이 이 샘플 데이터가 가까운 이웃 데이터들을 찾아 분류를 수행합니다.

- 여기서 k값을 3으로 설정했기 때문에, 가장 가까운 3개의 이웃 데이터를 찾아 이 중에서 다수결 투표를 통해 가장 많은 클래스를 가진 데이터의 클래스를 예측값으로 선택합니다.

- 따라서 새로운 샘플 데이터의 특성 값을 분류 알고리즘이 분석한 결과, 예측된 붓꽃 종류가 0 (Setosa)인 경우에는, 이 샘플 데이터가 다수의 이웃 데이터 중에서 Setosa에 해당하는 데이터들이 가장 많이 분포해 있기 때문입니다.