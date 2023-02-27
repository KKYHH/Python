# [Machine learning] k-fold cross validation

# k-Fold Cross Validation

k-Fold Cross Validation은 머신러닝 모델의 성능을 측정하는 방법 중 하나로, 데이터를 k개의 fold로 나누어서 k번 모델을 학습하고 검증하는 방법입니다. 각 fold는 서로 다른 데이터이며, k개의 fold에서 각각 한 번씩 검증 데이터로 사용됩니다. 나머지 (k-1)개의 fold는 학습 데이터로 사용됩니다. 이러한 과정을 k번 반복하여 모델의 성능을 평균하여 측정합니다.

이 방법은 모델의 성능을 보다 정확하게 측정할 수 있으며, 일반화 성능을 높이는 데 도움이 됩니다. 또한, 데이터의 분할에 따라 성능이 달라지는 경우가 있는데, 이러한 문제를 해결할 수 있습니다.

아래는 Python 코드를 사용하여 k-Fold Cross Validation을 수행하는 간단한 예시입니다.

```python
from sklearn.model_selection import KFold
from sklearn.linear_model import LinearRegression
import numpy as np

# 데이터 생성
X = np.array([[1, 2], [3, 4], [5, 6], [7, 8]])
y = np.array([2, 4, 6, 8])

# k-Fold Cross Validation 수행 (k=2)
kf = KFold(n_splits=2)
for train_index, test_index in kf.split(X):
    # 학습 데이터와 검증 데이터 분리
    X_train, X_test = X[train_index], X[test_index]
    y_train, y_test = y[train_index], y[test_index]

    # 모델 학습
    model = LinearRegression()
    model.fit(X_train, y_train)

    # 검증 데이터에 대한 예측
    y_pred = model.predict(X_test)

    # 검증 데이터에 대한 평균 제곱 오차 출력
    mse = np.mean((y_test - y_pred) ** 2)
    print("MSE:", mse)

```

위 코드에서는 데이터를 2개의 fold로 나누어서 Linear Regression 모델을 학습하고 검증합니다. 각 fold에서의 검증 데이터에 대한 평균 제곱 오차를 출력합니다.

- `from sklearn.model_selection import KFold`: scikit-learn 라이브러리에서 KFold 클래스를 import합니다.
- `from sklearn.linear_model import LinearRegression`: scikit-learn 라이브러리에서 LinearRegression 클래스를 import합니다.
- `import numpy as np`: numpy 라이브러리를 import하고, 이를 np로 aliasing합니다.
- `X = np.array([[1, 2], [3, 4], [5, 6], [7, 8]])`: 2차원 numpy array X를 생성합니다.
- `y = np.array([2, 4, 6, 8])`: 1차원 numpy array y를 생성합니다.
- `kf = KFold(n_splits=2)`: KFold 클래스의 객체 kf를 생성합니다. 이때 n_splits 인자를 2로 설정합니다.
- `for train_index, test_index in kf.split(X):`: kf.split 메소드를 사용하여 데이터를 (학습 데이터, 검증 데이터)로 분리하면서 반복문을 실행합니다. 이때, train_index와 test_index는 각각 (2, 3)과 (0, 1)입니다.
- `X_train, X_test = X[train_index], X[test_index]`: X에서 train_index와 test_index를 사용하여 X_train과 X_test를 생성합니다.
- `y_train, y_test = y[train_index], y[test_index]`: y에서 train_index와 test_index를 사용하여 y_train과 y_test를 생성합니다.
- `model = LinearRegression()`: LinearRegression 클래스의 객체 model을 생성합니다.
- `model.fit(X_train, y_train)`: 모델을 학습합니다.
- `y_pred = model.predict(X_test)`: 검증 데이터에 대한 예측값을 계산합니다.
- `mse = np.mean((y_test - y_pred) ** 2)`: 검증 데이터에 대한 평균 제곱 오차를 계산합니다.
- `print("MSE:", mse)`: 평균 제곱 오차를 출력합니다.

## k-Fold Cross Validation 장단점

### 장점

- 데이터를 효율적으로 사용하여 모델의 성능을 평가할 수 있습니다.
- 일반화 성능을 높이는 데 도움이 됩니다.
- 데이터의 분할에 따라 성능이 달라지는 문제를 해결할 수 있습니다.

### 단점

- 모델의 학습 시간이 증가합니다.
- k가 너무 작으면 과소적합, 너무 크면 과대적합 문제가 발생할 수 있습니다.
- 데이터의 편향이 발생할 수 있습니다.

k-Fold Cross Validation은 모델의 성능을 평가하는 데 유용한 방법입니다. 하지만, k의 값을 적절하게 설정하고, 데이터를 적절하게 분할하여 사용해야 합니다.