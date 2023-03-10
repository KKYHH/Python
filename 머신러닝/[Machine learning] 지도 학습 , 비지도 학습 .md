# 머신러닝_지도 학습 , 비지도 학습

## 지도 학습

지도 학습은 입력 데이터와 정답 데이터가 모두 주어지는 학습 방법이다. 즉, 컴퓨터는 입력 데이터와 정답 데이터를 이용하여 학습하고, 새로운 입력 데이터가 주어졌을 때 정답을 예측한다. 이 때 입력 데이터와 정답 데이터는 짝을 이루어야 한다. **지도 학습은 대부분의 분류나 회귀 문제에서 사용된다.**

예를 들어, 과일 사진이 주어졌을 때 그 과일이 어떤 과일인지 예측하는 문제가 있다고 하자. 이 때, 과일 사진을 입력 데이터로, 해당 과일의 이름을 정답 데이터로 사용하여 학습한다. 그리고 새로운 과일 사진이 주어졌을 때, 컴퓨터는 그 과일이 어떤 과일인지 예측할 수 있다.

## 비지도 학습

비지도 학습은 정답 데이터 없이 입력 데이터만을 이용하여 학습하는 방법이다. 즉, 컴퓨터는 입력 데이터의 구조나 패턴을 학습하고, 이를 기반으로 새로운 데이터를 처리한다. **비지도 학습은 대부분 군집화나 차원 축소 문제에서 사용된다.**

예를 들어, 과일 사진이 주어졌을 때, 컴퓨터는 과일의 종류에 상관 없이 과일 사진들의 공통된 패턴이나 특징을 학습할 수 있다. 그리고 이를 기반으로 비슷한 패턴을 가진 과일은 같은 그룹으로 묶일 수 있다.

따라서, 지도 학습과 비지도 학습은 각각 입력 데이터와 정답 데이터의 존재 여부에 따라 구분되며, 이를 이용하여 다양한 문제들을 해결할 수 있다.

이렇게 머신러닝의 두 가지 학습 방법을 이해하면, 어떤 문제를 해결하기 위해 어떤 학습 방법을 사용해야 하는지 파악할 수 있다. 예를 들어, 스팸 메일 분류 문제는 지도 학습으로 해결할 수 있고, 비정상 거래 탐지 문제는 비지도 학습으로 해결할 수 있다.

하지만 머신러닝의 학습 방법을 선택하는 것은 그 문제의 복잡도나 데이터의 양 등에 따라 달라질 수 있으므로, 문제를 해결하기 위해 어떤 학습 방법을 사용해야 하는지는 항상 신중하게 고려해야 한다.