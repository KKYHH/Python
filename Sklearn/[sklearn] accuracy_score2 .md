# [sklearn] accuracy_score

# sklearn accuracy_score

`accuracy_score` 함수는 sklearn 라이브러리에서 제공되며, 분류 모델의 예측 결과와 실제 결과를 비교하여 정확도를 계산하는 함수입니다.

이 함수는 두 개의 인자를 받습니다. **첫 번째 인자는 실제 결과값**, **두 번째 인자는 예측 결과값**입니다. 이 두 인자는 **모두 같은 길이의 배열**이어야 합니다.

`accuracy_score` 함수는 이렇게 계산된 정확도 값을 반환합니다. 정확도는 0에서 1 사이의 값으로 나타나며, 1에 가까울수록 모델이 정확하게 예측한 것입니다.

예를 들어, 다음과 같이 사용할 수 있습니다.

```python
from sklearn.metrics import accuracy_score

y_true = [0, 1, 2, 3, 4]
y_pred = [0, 2, 2, 3, 5]

accuracy = accuracy_score(y_true, y_pred)

print(accuracy)

```

이 코드는 `y_true`와 `y_pred` 두 배열을 비교하여 정확도를 계산하고, 이를 `accuracy` 변수에 할당한 뒤 출력합니다.

`accuracy_score` 함수는 이처럼 간단하게 사용할 수 있으며, 분류 모델의 성능을 평가하는 데 유용합니다.

`accuracy_score` 함수는 모델의 성능을 평가하기 위한 가장 적절한 지표가 아닐 수 있습니다. 특히 클래스의 비율이 불균형하거나, 거짓 양성과 거짓 음성의 비용이 다른 경우에는 정확도 대신 정밀도, 재현율 또는 F1 점수와 같은 지표를 사용하는 것이 더 적절할 수 있습니다. 적절한 평가 지표를 선택할 때는 문제의 특정 맥락과 모델의 목표를 고려하는 것이 중요합니다.