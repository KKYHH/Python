# [교차검증] cross_validate()

# 여러 개의 평가지표를 사용하고 싶을 때 사용

# cross_validate()에 대한 소개

`cross_validate()`는 Scikit-learn 라이브러리에서 제공하는 cross-validation(교차 검증) 기능의 한 가지 방법입니다. 이 함수를 사용하면 데이터셋을 여러 개의 fold(겹)로 나누어 각각의 fold를 테스트셋으로 사용하고 나머지 fold를 학습셋으로 사용하여 모델을 학습시키고 평가하는 과정을 반복할 수 있습니다.

## 함수 구문

`cross_validate(estimator, X, y=None, groups=None, scoring=None, n_jobs=None, cv=None, verbose=0, fit_params=None, pre_dispatch='2*n_jobs', return_train_score=False, return_estimator=False, error_score=nan)`

## 함수 인자

- `estimator`: scikit-learn에서 제공하는 모델 객체
- `X`: 독립 변수 데이터셋
- `y`: 종속 변수 데이터셋
- `groups`: 그룹 데이터셋
- `scoring`: 모델의 성능을 측정하는 방법
- `n_jobs`: 병렬 처리에 사용할 CPU 개수
- `cv`: 교차 검증을 위한 fold 수
- `verbose`: 출력할 로그 레벨
- `fit_params`: 모델 학습 시 사용할 매개변수
- `pre_dispatch`: 작업을 실행할 작업자 수
- `return_train_score`: 훈련 데이터에 대한 스코어를 반환할 지 여부
- `return_estimator`: 추정기 객체를 반환할 지 여부
- `error_score`: 에러가 발생한 경우 대체 값

## 함수 반환값

- `fit_time`: 각 fold에서 모델 학습에 소요된 시간
- `score_time`: 각 fold에서 모델 성능 측정에 소요된 시간
- `test_score`: 각 fold에서 모델의 성능 측정 결과
- `train_score`: 각 fold에서 모델을 학습시키고 훈련 데이터에 대한 성능 측정 결과

## 사용 예시

```python
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import cross_validate

X, y = load_iris(return_X_y=True)
logreg = LogisticRegression()
scoring = ['precision_macro', 'recall_macro']
scores = cross_validate(logreg, X, y, scoring=scoring)

```

`cross_validate()` 함수는 scikit-learn 라이브러리에서 제공하는 교차 검증 기능 중 하나입니다. 이 함수를 사용하면 데이터셋을 여러 개의 fold(겹)로 나누어 각각의 fold를 테스트셋으로 사용하고 나머지 fold를 학습셋으로 사용하여 모델을 학습시키고 평가하는 과정을 반복할 수 있습니다.

교차 검증은 모델의 성능을 평가하기 위한 방법 중 하나로, 과적합을 방지하고 일반화 성능을 높이는 데 도움이 됩니다. 이를 위해 데이터셋을 여러 개의 fold로 나누어 각각의 fold를 테스트셋으로 사용하고 나머지 fold를 학습셋으로 사용하여 모델을 학습시키고 평가하는 과정을 반복합니다. 이때, 각 fold의 테스트셋으로 사용된 데이터는 다른 fold의 학습셋으로 사용됩니다.

`cross_validate()` 함수는 다음과 같은 인자를 받습니다.

- `estimator`: scikit-learn에서 제공하는 모델 객체
- `X`: 독립 변수 데이터셋
- `y`: 종속 변수 데이터셋
- `groups`: 그룹 데이터셋
- `scoring`: 모델의 성능을 측정하는 방법
- `n_jobs`: 병렬 처리에 사용할 CPU 개수
- `cv`: 교차 검증을 위한 fold 수
- `verbose`: 출력할 로그 레벨
- `fit_params`: 모델 학습 시 사용할 매개변수
- `pre_dispatch`: 작업을 실행할 작업자 수
- `return_train_score`: 훈련 데이터에 대한 스코어를 반환할 지 여부
- `return_estimator`: 추정기 객체를 반환할 지 여부
- `error_score`: 에러가 발생한 경우 대체 값

`cross_validate()` 함수는 다음과 같은 반환값을 가집니다.

- `fit_time`: 각 fold에서 모델 학습에 소요된 시간
- `score_time`: 각 fold에서 모델 성능 측정에 소요된 시간
- `test_score`: 각 fold에서 모델의 성능 측정 결과
- `train_score`: 각 fold에서 모델을 학습시키고 훈련 데이터에 대한 성능 측정 결과

예를 들어, 아이리스 데이터셋에서 로지스틱 회귀 모델을 학습시키고 교차 검증을 수행하는 코드는 다음과 같습니다.

```python
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import cross_validate

X, y = load_iris(return_X_y=True)
logreg = LogisticRegression()
scoring = ['precision_macro', 'recall_macro']
scores = cross_validate(logreg, X, y, scoring=scoring)

```

`cross_validate()` 함수는 모델의 성능을 평가하고 반환된 결과를 scores 변수에 저장합니다.