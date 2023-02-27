# [sklearn] accuracy_score

## sklearn의 accuracy_score 함수 이해하기

머신 러닝 모델을 다룰 때, 성능을 평가하는 것이 중요합니다. 이를 위한 일반적인 메트릭 중 하나가 정확도입니다. sklearn 라이브러리의 `accuracy_score` 함수는 정확도를 계산하는 유용한 도구입니다.

### 정확도란?

정확도는 올바른 예측 수를 전체 예측 수로 나눈 비율입니다. 이는 모델의 성능을 측정하는 간단하지만 효과적인 방법입니다.

### accuracy_score 사용 방법

`accuracy_score` 함수는 두 개의 인자를 사용합니다: `y_true`와 `y_pred`.

- `y_true`: 이는 대상 변수에 대한 실제 값의 배열입니다.
- `y_pred`: 이는 대상 변수에 대한 예측 값의 배열입니다.

```python
from sklearn.metrics import accuracy_score

y_true = [0, 1, 1, 0, 1, 1]
y_pred = [0, 1, 0, 0, 1, 1]

accuracy = accuracy_score(y_true, y_pred)
print("Accuracy: %.2f%%" % (accuracy * 100))

```

이 예제에서, 우리는 이진 분류 문제에 대한 실제 값과 예측 값 두 개의 배열을 가지고 있습니다. 그런 다음 이러한 배열을 `accuracy_score` 함수의 인수로 전달하고 'accuracy'라는 변수에 결과를 저장합니다. 이 코드의 출력은 다음과 같습니다:

```python
Accuracy: 83.33%
```

이는 우리의 모델이 6개의 인스턴스 중 5개를 정확하게 예측하여 83.33%의 정확도를 보였다는 것을 의미합니다.

### 결론

`accuracy_score` 함수는 머신 러닝 모델의 성능을 평가하는 간단하지만 강력한 도구입니다. 이 함수를 사용하여 우리는 우리의 모델의 정확도를 빠르고 쉽게 계산하고 그들을 개선하는 방법에 대한 판단을 내릴 수 있습니다.