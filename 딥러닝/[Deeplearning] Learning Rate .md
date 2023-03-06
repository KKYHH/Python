# [Deeplearning] Learning Rate

# Learning Rate

## 학습률이란?

학습률이란, 딥러닝 모델에서 **가중치(Weight)**를 조정하기 위해 사용되는 파라미터입니다. 

학습률은 각 **반복(Iteration)**에서 가중치를 조절하는데 사용됩니다. 

즉, 학습이 진행됨에 따라 가중치를 최적화하기 위해 조정되는 값입니다.

## 학습률의 역할

학습률은 가중치 조정 시 얼마나 크게 조절할지를 결정합니다. 

학습률이 너무 작으면 가중치의 조정이 너무 느리게 이루어져 학습 시간이 오래 걸릴 수 있습니다. 

반대로 학습률이 너무 크면 가중치의 조정이 너무 크게 이루어져 발산할 가능성이 있습니다.

## 학습률의 설정 방법

학습률의 설정 방법은 다양하지만, 주로 **경험적인 방법**을 사용합니다. 

**즉, 여러 가지 학습률을 시도해 보고 가장 좋은 성능을 내는 값을 선택하는 것입니다.**

![https://gbhat.com/assets/gifs/sgd_learning_rates.gif](https://gbhat.com/assets/gifs/sgd_learning_rates.gif)

### 학습률이 너무 큰경우

<img src="https://github.com/KKYHH/Python/blob/main/image/%EB%94%A5%EB%9F%AC%EB%8B%9D/%5BDeeplearning%5D%20Learning%20Rate%20.png?raw=true">

### 학습률이 너무 작을 경우

<img src="https://github.com/KKYHH/Python/blob/main/image/%EB%94%A5%EB%9F%AC%EB%8B%9D/%5BDeeplearning%5D%20Learning%20Rate%201.png?raw=true">
