# [Deeplearning] Optimizer

# Optimizer

딥러닝 모델 학습 시, 모델의 성능과 학습 속도를 최적화하기 위해 **Optimizer**를 사용합니다. 

Optimizer는 Gradient Descent 방법을 기반으로 하며, 이를 발전시킨 여러 알고리즘이 존재합니다.

대표적인 Optimizer로는 아래와 같은 것들이 있습니다.

- **Stochastic Gradient Descent (SGD)**:
    
    일반적인 Optimizer로 학습 속도가 빠르지만, Local Minima에 빠지는 경우가 많습니다.
    
- **Adaptive Moment Estimation (Adam)**:
    
    Momentum과 Gradient Descent 방식을 동시에 사용하여 이를 보완했으며, 보편적으로 가장 많이 쓰이는 Optimizer입니다.
    
- **Root Mean Square Propagation (RMSprop)**: SGD의 문제점을 개선한 방식입니다.

- **Adagrad**: 학습률을 조절하는 방식으로 학습률이 작아질수록 더 작은 갱신을 하게 됩니다.

- **Adadelta**: Gradient Descent 방식을 개선하는 방식으로 이전 학습에서의 gradient값도 고려합니다.

각 Optimizer의 특징과 장단점에 대해 이해하고, 모델 학습 시에 적절한 Optimizer를 선택하는 것이 중요합니다.

SGD는 일반적인 Optimizer로 학습 속도가 빠르지만, Local Minima에 빠지는 경우가 많습니다. 

**Adam**은 Momentum과 Gradient Descent 방식을 동시에 사용하여 이를 보완했으며, RMSprop은 SGD의 문제점을 개선한 방식입니다. Adagrad와 Adadelta는 각각 학습률을 조절하거나 Gradient Descent 방식을 개선하는 방식입니다.

딥러닝 모델 학습 시에는 Optimizer를 적절하게 선택하여 학습 속도와 모델 성능을 극대화할 수 있습니다.

보편적으로 가장 많이 쓰이는 Optimizer는 Adam

![https://gbhat.com/assets/gifs/optimize_with_momentum.gif](https://gbhat.com/assets/gifs/optimize_with_momentum.gif)

![https://blog.kakaocdn.net/dn/b3frqF/btq51QxDtT7/fNqemBxDOamPkfNTkrptAK/img.gif](https://blog.kakaocdn.net/dn/b3frqF/btq51QxDtT7/fNqemBxDOamPkfNTkrptAK/img.gif)