# [Deeplearning] 기울기 소실 Vanishing Gradient

# 기울기 소실 Vanishing Gradient

딥러닝에서 가장 큰 문제점 중 하나는 **기울기 소실(Vanishing Gradient)입니다.** 

이 문제는 역전파(backpropagation) 알고리즘에서 발생합니다. 

역전파 알고리즘은 출력 값과 실제 값 사이의 오차를 최소화하기 위해 가중치를 조정하는 방법입니다. 

이 때, 기울기가 전파되면서 신경망의 깊이가 깊어질수록 기울기가 소실되는 문제가 발생합니다.

<img src="https://github.com/KKYHH/Python/blob/main/image/%EB%94%A5%EB%9F%AC%EB%8B%9D/%5BDeeplearning%5D%20%EA%B8%B0%EC%9A%B8%EA%B8%B0%20%EC%86%8C%EC%8B%A4%20Vanishing%20Gradient%20.png?raw=true">

기울기 소실 문제는 심층 신경망에서 특히 더 크게 나타납니다. 

이는 역전파 알고리즘이 각 레이어(layer)에서 기울기를 계산하는데, 이 기울기가 작아질수록 학습이 어려워지기 때문입니다. 

이러한 문제는 특히 **활성화 함수로 sigmoid나 tanh 함수를 사용할 때 더욱 심각해집니다.** 

이 함수들은 입력값이 일정 범위를 넘어가면 기울기가 매우 작아지게 되는데, 이 때문에 신경망이 깊어질수록 기울기가 소실되는 문제가 발생합니다.

<img src="https://github.com/KKYHH/Python/blob/main/image/%EB%94%A5%EB%9F%AC%EB%8B%9D/%5BDeeplearning%5D%20%EA%B8%B0%EC%9A%B8%EA%B8%B0%20%EC%86%8C%EC%8B%A4%20Vanishing%20Gradient%201.png?raw=true">

이러한 기울기 소실 문제를 해결하기 위해서는 다양한 방법이 제안되고 있습니다. 

대표적인 방법으로는 **ReLU(Rectified Linear Unit) 함수를 사용하는 것입니다.**

 **ReLU 함수**는 입력값이 0보다 작으면 0을 출력하고, 0보다 크면 그대로 출력하는 함수입니다. 

이 함수는 기울기가 0이 되는 문제를 해결할 수 있습니다.

<img src="https://github.com/KKYHH/Python/blob/main/image/%EB%94%A5%EB%9F%AC%EB%8B%9D/%5BDeeplearning%5D%20%EA%B8%B0%EC%9A%B8%EA%B8%B0%20%EC%86%8C%EC%8B%A4%20Vanishing%20Gradient%202.png?raw=true">

<img src="https://github.com/KKYHH/Python/blob/main/image/%EB%94%A5%EB%9F%AC%EB%8B%9D/%5BDeeplearning%5D%20%EA%B8%B0%EC%9A%B8%EA%B8%B0%20%EC%86%8C%EC%8B%A4%20Vanishing%20Gradient%203.png?raw=true">

또한, 초기화 방법을 조정함으로써 기울기 소실 문제를 해결할 수도 있습니다. 

초기화 방법을 잘못 선택하면 기울기가 소실되는 문제가 발생할 수 있습니다. 

이를 방지하기 위해 Xavier 초기화나 He 초기화와 같은 방법을 사용할 수 있습니다.

마지막으로, skip connection을 사용하여 기울기 소실 문제를 해결할 수도 있습니다. 

skip connection은 입력값을 바로 출력값에 더해주는 방식으로, 입력값이 출력값으로 직접적으로 전달되기 때문에 기울기 소실 문제를 해결할 수 있습니다.
