# [알고리즘] svm

# Scikit-learn SVM

Scikit-learn은 파이썬에서 머신러닝을 수행하는 데 매우 유용한 패키지입니다. Scikit-learn의 SVM(Support Vector Machine)은 분류와 회귀 분석을 위한 머신러닝 알고리즘입니다. SVM은 특정 물체 집합을 다른 집합으로 분류하는 데 사용됩니다.

## SVM을 사용한 붓꽃 데이터 분류

분류 문제의 예로, 붓꽃 데이터를 이용한 SVM 모델 학습을 살펴보겠습니다. 붓꽃 데이터는 Scikit-learn 패키지에서 제공하는 예제 데이터셋 중 하나입니다. 붓꽃 데이터셋은 세 가지 종류의 붓꽃(Iris)의 꽃잎 길이와 너비, 꽃받침 길이와 너비를 포함합니다. 이 데이터셋에서는 꽃의 종류를 분류하는 문제를 다룹니다.

### 데이터 분류 및 모델 학습

먼저, 데이터셋을 로드하고 데이터를 학습용 데이터와 검증용 데이터로 분류합니다. 이것은 train_test_split 함수를 사용하여 쉽게 수행할 수 있습니다.

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

# 데이터 로드
iris = load_iris()

# 데이터 분류
X_train, X_test, y_train, y_test = train_test_split(iris.data, iris.target, stratify=iris.target, random_state=42)

```

그리고, SVM 모델을 학습시킵니다. 이 모델은 kernel, C, gamma 매개변수를 사용합니다. kernel 매개변수는 SVM 모델에서 사용되는 커널 함수를 정의합니다. C 매개변수는 오류에 대한 페널티를 정의하며, gamma 매개변수는 커널의 폭을 정의합니다.

```python
from sklearn.svm import SVC

# SVM 모델 학습
svm = SVC(kernel='rbf', C=1, gamma=0.1)
svm.fit(X_train, y_train)

```

### 모델 평가

마지막으로, 모델의 정확도를 평가합니다. 학습용 데이터셋과 검증용 데이터셋 모두에 대한 정확도를 출력합니다.

```python
# 모델 평가
print("학습용 데이터셋 정확도: {:.2f}".format(svm.score(X_train, y_train)))
print("검증용 데이터셋 정확도: {:.2f}".format(svm.score(X_test, y_test)))

```

### 결과

코드 실행 결과는 다음과 같습니다.

```python
학습용 데이터셋 정확도: 0.97
검증용 데이터셋 정확도: 0.97

```

위의 코드는 붓꽃 데이터셋을 train_test_split 함수를 사용하여 학습용 데이터와 검증용 데이터로 분류한 다음, SVM 모델을 학습시키고, 모델의 정확도를 평가하는 코드입니다.

SVM은 다른 머신러닝 알고리즘과 비교하여 높은 정확도를 보이는 경향이 있습니다. 따라서, 분류 문제를 해결하는 데 유용한 머신러닝 알고리즘입니다.

## SVM의 장점

- 다른 머신러닝 알고리즘과 비교하여 높은 정확도를 보인다.
- 과적합(Overfitting)을 방지할 수 있다.
- 다양한 커널(kernel) 함수를 사용하여 다양한 종류의 데이터를 분류할 수 있다.

## SVM의 단점

- 데이터의 전처리가 필요하다.
- 매개변수(kernel, C, gamma)의 선택이 중요하다.
- 대용량 데이터셋에서 성능이 저하될 수 있다.