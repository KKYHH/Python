# 데이터 시각화용 라이브러리 matplotlib

## matplotlib

- matplotlib 라이브러리는 파이썬에서 2D 형태의 그래프 , 이미지 등을 그릴때 사용하는 라이브러리다
- 실제 과학 컴퓨팅 연구분야나 인공지능 연구분야에서 많이 사용

설치

`pip install matplotlib`

기본 사용법

```python
import matplotlib.pyplot as plt

plt.plot([10,20,30,40])
plt.show
```

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled.png)

`import matplotlib.pyplot as plt`

일단 matplotlib 라이브러리 안의 pyplot 모듈을 import 해 준다

`pyplot` 을 `plt` 로 줄여부르겠다는 소리다 ( 공식 홈페이지에서도 plt로 줄여서 쓴다 )

plot 안에 리스트 하나만 넣을 경우 위 그래프와 같이 저절로 y축으로 받아서 그래프가 그려진다

### 두 개의 리스트

```python
import matplotlib.pyplot as plt
plt.plot([1,2,3,4],[12,43,25,15])
# x = [1,2,3,4]
# y = [12,43,25,15]
# plt.plot(x,y)
plt.show()
```

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%201.png)

위처럼 두 개의 리스트를 입력할 경우에는 첫 번째 리스트가 x축 값,

두 번째 리스트가 y축 값이 된다

### 제목 넣기

```python
import matplotlib.pyplot as plt
plt.title('plotting')
plt.plot([1,2,3,4],[12,43,25,15])
plt.show()
```

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%202.png)

`plt.title(’plotting’)`

- title 안에 원하는 제목을 넣으면 위와 같이 제목이 표시된다

### 한글 제목 넣기

```python
import matplotlib
matplotlib.rcParams['font.family'] = 'AppleGothic'
matplotlib.rcParams['font.size'] = 15
matplotlib.rcParams['axes.unicode_minus']=False

# 서체 선택
# 폰트 사이즈
# 한글폰트 사용시 마이너스가 깨지는 문제해결
```

### 범례 넣기

```python
import matplotlib.pyplot as plt
plt.title('legend')
plt.plot([10,20,30,40],label='asc')
plt.plot([40,30,20,10], label='desc')
plt.legend()
plt.show()
```

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%203.png)

plot() 함수 안에 리스트와 함께 label 이름을 정하고

`plt.legend()`

legend() 함수를 실행시키면 레이블 값이 범례로 나타난다

### 그래프 색상 바꾸기

```python
import matplotlib.pyplot as plt
plt.title('legend')
plt.plot([10,20,30,40], color='skyblue',label='skyblue')
plt.plot([40,30,20,10], 'pink',label='pink')
plt.legend()
plt.show()
```

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%204.png)

- plot() 함수 안에 `color=’ ‘` 를 넣고 원하는 색상을 넣는다
- 위 ‘pink’ 처럼 color=는 생략이 가능

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%205.png)

위와 같이 색상 이름을 사용해서 색상지정이 가능하다

### 그래프 선 모양 바꾸기

```python
import matplotlib.pyplot as plt
plt.title('linestyle')
plt.plot([10,20,30,40], color='r', linestyle='--', label='dashed')
plt.plot([40,30,20,10], color='g', linestyle=':', label='dotted')

plt.legend()
plt.show()
```

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%206.png)

`linestyle=’ ‘` 안에 원하는 선 모양을 넣으면 된다

선의 종류는 다음과 같다

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%207.png)

### 마커 모양 바꾸기

```python
import matplotlib.pyplot as plt
plt.title('marker')
plt.plot([10, 20, 30, 40], 'r.', label='circle')
plt.plot([40, 30, 20, 10], 'g^', label='triangle up')
plt.legend()
plt.show()
```

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%208.png)

위 예시의 경우 빨간 선은(r)은 point marker로, 녹색 선(g)은 triangle_up marker로 나타내는 그래프이다

plot() 함수 다음에 원하는 마커를 넣어주면 된다

matplotlib에서 사용할 수 있는 마커의 종류

![Untitled](%E1%84%83%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%90%E1%85%A5%20%E1%84%89%E1%85%B5%E1%84%80%E1%85%A1%E1%86%A8%E1%84%92%E1%85%AA%E1%84%8B%E1%85%AD%E1%86%BC%20%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5%20matplotlib%20c7481f1f300e4ce8bc8765e2f7be6c89/Untitled%209.png)