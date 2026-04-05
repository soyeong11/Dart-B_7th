# 데이터분석 5주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_5th_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=ho0LZ6GWhtc&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=10
https://www.youtube.com/watch?v=deYY4xHsI0o&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=11
-->


## DataAnalysis_5th_TIL

### 5장 데이터 시각화하기
#### 01. 맷플롯립 기본 요소 알아보기
#### 02. 선 그래프와 막대 그래프 그리기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | ✅         |
| 4주차 | p.222~279 | ✅         |
| 5주차 | p.282~325 | ✅         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. 맷플롯립 기본 요소 알아보기

### 1. Figure 객체

**01) Figure 란?**

- 모든 그래프의 구성 요소를 담고 있는 최상위 객체

**02) figsize 매개변수**

- 그래프 크기를 바꿀 수 있는 함수
- 기본 그래프 크기: (6, 4)




**03) dpi 매개변수**



### 2. rcParams 객체

**01) rcParams 란?**


**02) DPI 기본값 바꾸기**


**03) 산점도 마커 모양 바꾸기**




### 3. 서브플롯 출력

**01) subplots() 함수**


**02) 서브플롯 가로로 출력**




### 📌 한바닥 정리

01) figure
- 맷플롯립의 그래프 요소를 모두 담고 있는 최상위 객체
- 맷플롯립으로 그래프 그릴 때 자동 생성 >> 그려진 후 자동 삭제

02) reParams
- 맷플롯립 그래프의 기본값 관리하는 객체
- 객체에 담긴 값 출력 및 새로운 값으로 교체

03) 축
- 그래프에서 데이터 좌표 표현
- 2차원 그래프는 축 2개, 3차원 그래프는 축 3개
- Axis, Axes(Axis 두 개 이상)

04) 마커
- 그래프에 데이터 포인트를 표시하는 방법
- 기본 마커 = 'o'
- rcParams 객체나 marker 매개변수로 바꿀 수 있음

05) 서브플롯
- 피겨 안에 포함된 그래프 영역
- 보통 Axes 객체
- subplots() 활용

06) 핵심 함수 & 메서드

| 함수/메서드 | 기능 |
| --- | --- |
| matplotlib.pyplot.figure() | 피겨 객체 만들어 반환 |
| matplotlib.pyplot.subplots() | 피겨와 서브플롯 생성하여 반환 |
| Axes.set_xscale() | 서브플롯의 X축 스케일 지정 |
| Axes.set_yscale() | 서브플롯의 y축 스케일 지정 |
| Axes.set_title() | 서브플롯의 제목 설정 |
| Axes.set_xlabel() | 서브플롯의 x축 이름 지정 |
| Axes.set_ylabel() | 서브플롯의 y축 이름 지정 |



## 02. 선 그래프와 막대 그래프 그리기

### 📌 한바닥 정리

01) 선 그래프
- 각 데이터 포인트를 직선으로 연결한 그래프

02) 막대 그래프
- 데이터 포인트의 크기를 막대 높이로 나타낸 그래프
- x좌표는 범주형, y좌표는 해당 범주의 값

03) 핵심 함수와 메서드

| 함수/메서드 | 기능 |
| --- | --- |
| matplotlib.pyplot.plot() | 선 그래프 그리기 |
| matplotlib.pyplot.title() | 그래프 제목 설정 |
| matplotlib.pyplot.xlabel() | x축 이름 지정 |
| matplotlib.pyplot.ylabel() | y축 이름 지정 |
| matplotlib.pyplot.xticks() | x축 눈금 위치 & 레이블 지정 |
| matplotlib.pyplot.annotate() | 지정한 좌표에 텍스트 출력 |
| matplotlib.pyplot.bar() | 세로 막대 그래프 그리기 |
| matplotlib.pyplot.barh() | 가로 막대 그래프 그리기 |
| matplotlib.pyplot.imread() | 이미지 파일을 넘파일 배열로 읽기 |
| matplotlib.pyplot.imshow() | 이미지 출력 |
| matplotlib.pyplot.imsave() | 넘파이 배열을 이미지 파일로 저장 |
| matplotlib.pyplot.savefig() | 그래프를 이미지로 저장 |


# 2️⃣ 수행 인증

<!-- 교재에서 안내된 과정을 직접 실행해본 뒤, 진행 결과가 보이도록 4~6장의 스크린샷을 캡처하여 아래에 첨부해주세요.-->



<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 데이터를 이용하여 matplotlib으로 선그래프를 그리는 코드를 작성해주세요.**
- x = [1, 2, 3, 4, 5]
- y = [2, 4, 6, 8, 10]
> 조건은 아래와 같습니다.
```
1️⃣ 제목은 "Linear Trend"로 설정해주세요.
2️⃣ x축 이름은 "X values"로 설정해주세요.
3️⃣ y축 이름은 "Y values"로 설정해주세요.
4️⃣ 마커(marker)를 포함하여 선그래프를 그려주세요.
```

```
여기에 코드를 작성해주세요!
```



### 🎉 수고하셨습니다.