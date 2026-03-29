# 데이터분석 4주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_4th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=HNlRYQnLkek&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=8
https://www.youtube.com/watch?v=Cbk_tQtuhbM&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=9
-->


## DataAnalysis_4th_TIL

### 4장 데이터 요약하기
#### 01. 통계로 요약하기
#### 02. 분포 요약하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | ✅         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 통계로 요약하기


### 📌 기술통계 구하기

**1. describe() 메서드**

수치형 열에 대한 요약 통계

- count: 누락된 값을 제외한 데이터의 개수
- mean: 평균
- std: 표준편차
- min: 최솟값
- 50%: 중앙값
- 25%, 75%: 순서대로 늘어 놓았을 때 25% 지점과 75% 지점에 놓인 값
- max: 최댓값


(1) percentiles 매개변수

describe()는 기본적으로 데이터의 25%, 50%, 75%에 위치한 값을 보여줌. <br>
원하는 위치의 값을 보고 싶다면 percentiles 매개변수에 위치 지정하면 됨.


(2) include 매개변수

수치형 데이터가 아닌 다른 데이터의 기술통계 볼 수 있음 <br>
- (ex) object 타입 통계

```python
데이터프레임.describe(include='object')
```


### 📌 평균 구하기

**1. range() 함수**

0부터 입력된 숫자 직전까지 반복

- (ex) range(3) >> 0, 1, 2


**2. mean() 메서드**

```python
데이터프레임['열 이름'].mean()
```


### 📌 중앙값 구하기

**1. median() 메서드**

```python
데이터프레임['열 이름'].median()
```

**2. 중복값 제거 & 중앙값 구하기**

**1. drop_duplicates() 메서드**

```python
데이터프레임['열 이름'].drop_duplicates().median()
```


### 📌 최솟값, 최댓값 구하기

**1. min(), max() 메서드**

```python
데이터프레임['열 이름'].min()
데이터프레임['열 이름'].max()
```


### 📌 분위수 구하기

**1. quantile() 메서드**

```python
데이터프레임['열 이름'].quantile(보고 싶은 분위수 숫자로)
# 여러 개의 분위수를 보고 싶다면 리스트 형태로 넣으면 됨
```

(1) interpolation 매개변수

중간 값 계산 방법 결정 >> 보간법

- 기본 값: linear로 양쪽 분위수에 비례하여 결정
- interpolation='midpoint': 분위수에 상관없이 무조건 두 수 사이의 중앙값 사용
- interpolation='nearest': 두 수 중에서 가까운 값 선택
- interpolation='lower': 두 수 중 작은 값 선택
- interpolation='higher': 두 수 중 큰 값 선택


### 📌 백분위 구하기

분위수 구하기의 반대

- (1) 불리언 배열 만들기
- (2) 불리언 배열에서 True인 개수 / 전체 데이터 개수

**1. 불리언.mean() 메서드**

백분위를 간단하게 구할 수 있음


### 📌 분산 구하기

**1. var() 메서드**

```python
데이터프레임['열 이름'].var()
```


### 📌 표준편차 구하기

**1. std() 메서드**

```python
데이터프레임['열 이름'].std()
```


### 📌 최빈값 구하기

**1. mode() 메서드**

```python
데이터프레임['열 이름'].mode()
```


### 📌 넘파이의 기술통계 함수

**1. 평균 구하기**

- mean()과 average() 함수 사용

```python
np.mean(데이터프레임['열 이름'])
np.average(데이터프레임['열 이름'])
```

(1) weight 매개변수

가중 평균 (평균을 구할 때 각 값의 중요도에 따라 가중치를 부여한 평균값) 계산


**2. 중앙값 구하기**

- median() 함수 사용

```python
np.median(데이터프레임['열 이름'])
```

**3. 최솟값, 최댓값 구하기**

- min(), max() 함수 사용

```python
np.min(데이터프레임['열 이름'])
np.max(데이터프레임['열 이름'])
```

**4. 분위수 구하기**

- quantile(), percentile() 함수 사용

```python
np.quantile(데이터프레임['열 이름'], [0.25, 0.5, 0.75])
```

method 매개변수: interpolation 매개변수와 같은 기능

**5. 분산 구하기**

- var() 함수 사용

```python
np.var(데이터프레임['열 이름'])
```

※ 판다스의 var() 값과 다름 <br>
이유: 판다스는 표본집단으로 계산하기 때문에 n-1 자유도를 사용하지만, 넘파이는 n 자유도를 사용함. <br>
**ddof 매개변수** 사용해서 자유도 차감값을 정할 수 있음


**6. 표준편차 구하기**

- std() 함수 사용

```python
np.std(데이터프레임['열 이름'])
```

**7. 최빈값 구하기**

- unique() 함수와 return_counts 매개변수

```python
values, counts = np.unique(데이터프레임['열 이름'], return_counts=True)
max_idx = np.argmax(counts)  # counts 배열에서 가장 큰 값의 인덱스 찾기
values[max_idx]  # 등장 횟수가 가장 많은 값의 인덱스 값 출력
```


### 📌 한바닥 정리

1) 평균
- 데이터값을 모두 더한 후 데이터 개수로 나눈 값

2) 중앙값
- 전체 데이터를 크기 순서대로 늘어 놓았을 때 중간에 위치한 값
- 데이터 개수가 짝수일 때는 중간의 두 데이터의 평균 계산

3) 분위수
- 순서대로 나열된 데이터를 일정한 간격으로 나누는 기준점
- (ex): 사분위수는 25%, 50%, 75%에 위치한 값

4) 분산
- 데이터가 평균에서 얼마나 멀리 퍼져 있는지 알려주는 값
- (데이터값 - 평균)^2 / (전체 데이터 개수)

5) 표준편자
- 분산의 제곱근
- 데이터의 분포 정도 확인
- 분산보다 해석하기 쉬움 (∵ 원본 데이터와 단위 동일)

6) 최빈값
- 데이터에서 가장 많이 등장하는 값
- 숫자와 문자 데이터에 모두 적용 가능

7) 핵심 함수와 메서드

| 함수/메서드 | 기능 |
| --- | --- |
| DataFrame.describe() | 데이터프레임의 기술통계량 출력 |
| DataFrame.mean() | 데이터 평균 계산 |
| numpy.mean() | 입력된 배열의 평균 계산 |
| Series.median() | 데이터의 중앙값 찾기 |
| numpy.median() | 입력된 배열의 중앙값 찾기 |
| Series.quantile() | 데이터의 분위수 계산 |



## 02. 분포 요약하기

### 📌 산점도 그리기

**1. 산점도란**

두 변수 or 두 가지 특성값을 직교 좌표계에 점으로 나타내는 그래프

**2. 산점도를 그려보자**

- matplotlib.pyplot

맷플롯립에서 제공하는 그래프 함수의 패키지

```python
import matplotlib.pyplot as plt
# 패키지 이름이 길어서 plt로 줄여서 씀
```

- scatter() 함수

함수 첫 번째 매개변수에 x축 좌표, 두 번째 매개변수에 y축 좌표 전달 <br>
scatter 호출한 다음에는 **show()**로 그래프 출력

```python
plt.scatter(x축 데이터, y축 데이터)
plt.show()
```

- alpha 매개변수 <br>
0-1 사이의 값으로 투명도 지정

```python
plt.scatter(x축 데이터, y축 데이터, alpha = 0-1 사이의 값)
plt.show()
```

### 📌 히스토그램 그리기

**1. 히스토그램이란**

수치형 특성의 값을 일정한 구간으로 나누어 구간 안에 포함된 데이터 개수를 막대 그래프로 그린 것. 구간 안에 속한 데이터의 개수를 도수라고 함.

**2. 히스토그램을 그려보자**

- hist() 함수
    - 1차원 데이터를 입렵받아 히스토그램 그림
    - 기본적으로 데이터를 10개의 구간으로 나눔
    - bins 매개변수: 구간의 수를 정함

```python
plt.hist(데이터, bins=구간 몇 개)
plt.show()
```

- histogram_bin_edges() 함수
    - numpy에서 제공하는 함수
    - 구간이 어떻게 나누어졌는지 수치를 확인할 수 있음

```python
import numpy as np
np.histogram_bun_edges(데이터, bins=숫자 정하기)
```

- randn() 함수
    - numpy에서 제공하는 함수
    - 표준정규분포를 따르는 랜덤한 실수 생성
    - 원하는 샘플 개수를 전달하여 난수 생성 가능

```python
np.random.seed(42)
random_samples = np.rnadom.radn(1000)
```

- seed() 함수
    - 유사난수 생성 가능
    - 실습 결과를 동일하게 만들기 위해 seed() 사용
    - seed()에 동일한 값을 사용하는 한 언제나 동일한 난수 추출 가능

- 로그 스케일
    - 한 구간의 도수가 너무 커서 다른 구간에 도수가 표시되지 않는 현상 발생 >> y축을 로그 스케일로 바꿈
    - yscale()함수에 'log' 지정하면 끝
    - x축에도 적용 가능 >> xscale('log')

```python
plt.hist(데이터)
plt.yscale('log')
plt.show()
```

### 📌 상자 수염 그림 그리기

**1. 상자 수염 그림이란**

최솟값, 세 개의 사분위수, 최댓값 이렇게 다섯 개의 숫자를 사용해 데이터를 요약하는 그래프

**2. 상자 수염 그림을 그려보자**

- boxplot() 함수

```python
plt.boxplot(데이터)
plt.show()
# y값이 너무 커 결과가 잘 나오지 않는다면 여기서도 로그 스케일 사용 가능
```

- vert 매개변수
    - 상자수염 수평으로 그리기
    - 기본값이 True. False로 바꾸면 수평으로 그려짐

```python
plt.boxplot(데이터, vert=False)
plt.xscale('log')
plt.show()
```

- whis 매개변수
    - 수염 길이 조정하기
    - 기본값 1.5. 숫자를 넣으면 이것의 n배의 수염을 볼 수 있게 됨
    - 백분율로도 지정 가능
        - ex) (10, 90) >> 10%, 90% 백분위수에 해당하는 데이터까지 수염 그림

```python
plt.boxplot(데이터, whis=숫자 쓰기)
plt.show()
```


### 📌 한바닥 정리

1) matplotlib
- 파이썬의 그래프 패키지
- 산점도, 히스토그램, 상자수염, 막대 그래프, 선 그래프 등 지원
- 그래프 구성 요소 제어 옵션 제공

2) 산점도
- 데이터를 2 or 3차원 공간에 점으로 표시하는 그래프

3) 히스토그램
- 데이터를 일정 구간으로 나누어 구간에 속한 데이터의 개수(도수)를 막대로 표현한 그래프

4) 로그 스케일
- 데이터가 한쪽에 편중되어 있을 때 사용

5) 상자 수염 그림
- 사분위수, 최솟값, 최댓값을 사용한 그래프
- 제1사분위수와 제3사분위수를 이용해 상자 그림 >> 상자의 IQR 거리의 1.5배 범위 안에서 가장 멀리 떨어진 데이터까지 수직선(수염)을 그려서 분포 표현

6) 핵심 함수와 메서드

| 함수/메서드 | 기능 |
| --- | --- |
| Matplotlib.pyplot.scatter() | 2차원 평면의 산점도 |
| Matplotlib.pyplot.hist() | 히스토그램 |
| Matplotlib.pyplot.boxplot() | 상자 수염 그림 |
| Matplotlib.pyplot.xscale() | X축 스케일 지정 |
| Matplotlib.pyplot.yscale() | y축 스케일 지정 |
| nympy.random.seed() | 임의의 정수 입력 >> 난수 발생을 동일하게 재현 |
| nympy.random.randn() | 표준정규분포를 따르는 난수 생성 |


# 2️⃣ 수행 인증

![result1](./image/week_4(1).png)
![result2](./image/week_4(2).png)
![result3](./image/week_4(3).png)


<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 이번 주차에는 확인문제 대신 실습 과제를 진행합니다. 캐글에서 원하는 데이터셋을 선택하여 기술통계를 계산하고, 다양한 시각화를 수행해보세요.
작업은 코랩에서 진행한 뒤, 코랩 링크를 아래에 첨부해주세요.**

```
https://colab.research.google.com/drive/1-U1-2H_dcE5KANBW9pzNT1eDRpPqpMgT?usp=sharing
```



### 🎉 수고하셨습니다.