# [Numpy] np.random.choice

# np.random.choice

`np.random.choice` 함수는 numpy 라이브러리 안에 있는 함수 중 하나로, 주어진 배열에서 무작위로 샘플을 선택할 수 있도록 합니다. 이 함수를 사용하면 **데이터 분석, 머신러닝 등에서 랜덤한 샘플링이 필요한 경우 유용하게 사용할 수 있습니다.**

## 사용 방법

`np.random.choice` 함수를 사용하기 위해서는 numpy 라이브러리를 import 해야 합니다. 함수의 구조는 다음과 같습니다.

```python
numpy.random.choice(a, size=None, replace=True, p=None)

```

여기서 `a`는 원본 배열, `size`는 샘플링할 요소의 개수, `replace`는 중복을 허용할지 여부, `p`는 각 요소가 선택될 확률을 지정하는 배열입니다.

### 예시

다음은 `np.random.choice` 함수를 사용하여 주어진 배열에서 무작위로 3개의 샘플을 선택하는 예시 코드입니다.

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
sample = np.random.choice(arr, 3, replace=False)

print(sample)

```

위 코드를 실행하면 `arr` 배열에서 중복되지 않는 무작위로 선택된 3개의 수가 출력됩니다.