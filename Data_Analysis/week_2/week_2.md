# 데이터분석 2주차 정규과제

📌데이터분석 정규과제는 매주 정해진 분량의 『*혼자 공부하는 데이터 분석 with 파이썬*』 을 읽고 학습하는 것입니다. 이번 주는 아래의 **DataAnalysis_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=s_-VvTLb3gs&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=4
https://www.youtube.com/watch?v=Il6L8OtNFpc&list=PLVsNizTWUw7FGzSRCkQrPEEe-ljVXgS7k&index=5
-->


## DataAnalysis_2nd_TIL

### 2장 데이터 수집하기
#### 01. API 사용하기
#### 02. 웹 스크래핑 사용하기


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~81    | ✅         |
| 2주차 | p.84~151   | ✅         |
| 3주차 | p.154~219  | 🍽️         |
| 4주차 | p.222~279 | 🍽️         |
| 5주차 | p.282~325 | 🍽️         |
| 6주차 | p.328~379 | 🍽️         |
| 7주차 | p.382~430 | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->


# 1️⃣ 개념 정리 

## 01. API 사용하기

> Application Programming Interface

**두 프로그램이 서로 대화하기 위한 방법을 정의한 것**

### 📍웹 기반 API

#### ✔️웹 페이지 문서: HTML
 **HTML (Hypertext Markup Language)**
 - 웹 브라우저가 화면에 표시한 수 있는 문서의 한 종류이자 웹 페이지를 위한 표준 언어
    - 크롬 브라우저에서 [페이지 소스 보기] 메뉴 선택하면 볼 수 있음
    - CSV와 같은 단순 텍스트이지만 브라우저 프로그램이 이해할 수 있도록 체계적으로 구성됨
    - HTML 언어를 **마크업** 언어라고 부르고, div를 **태그**라고 함

 - 웹 서버와 웹 브라우저가 대화하는 방식과 유사
    - HTTP 프로토콜을 사용하지만 HTML을 주고받는 것이 아니라 CSV, JSON, XML 같은 파일 이용 (HTML의 구조가 복잡하기 때문)
    - CSV 보다는 JSON, XML 이용 多 (CSV는 각 행마다 항목의 개수가 맞지 않으면 읽을 수 X)

#### ✔️파이썬에서 JSON 다루기

**JSON (JavaScript Object Notation)**
 
 원래는 자바스크립트 언어를 위해 만들어졌지만 현재는 범용적인 포맷으로 사용
 - 딕셔너리와 리스트를 중첩해놓은 것과 유사
 - 키와 값을 콜론(:)으로 연결. 문자열은 항상 큰따옴표로 감싸야 함.
    - ex: {"name":"혼자공부하는 데이터 분석"}
 - 웹 기반 API로 데이터를 전달할 때는 파이썬 딕셔너리가 아니라 텍스트로 전달해야 함
 
 1. json.dump() 함수
    - 파이썬 객체를 JSON 문자열로 변환 <dr>
    **웹 기반 API는 전송하려는 파이썬 객체를 json.dumps() 함수를 사용하여 JSON 문자열로 변환하여 전송해야 함**
    - ensure_ascii = False
        - 딕셔너리에 한글이 포함되어 있는 경우에 False로 지정
    - d_str 문자열에 객체인지 파이썬의 type() 함수로 확인 가능
 
 2. json.loads() 함수
    - JSON 문자열을 파이썬 객체로 변환

 3. read_json() 함수
    - Json 문자열을 데이터프레임으로 변환
    - pandas에서 제공하는 함수
    - Json 객체가 데이터프레임 각 행에 매핑(mapping)
    - 데이터 프레임으로 바꾸는 다른 방법: JSON 문자열 파이썬 객체로 → DataFrame 클래스 사용 (pd.DataFrame())

#### ✔️파이썬에서 XML 다루기
**XML (eXtensible Markup Language)**
 - 웹페이지 표현 우수. But 구조적이지는 못해서 API에는 적절하지 X.
 - 엘리먼트(element)들이 계층 구조를 이루면서 정보 표현
    - 시작 태그와 종료 태그로 감싸서 표현
    - 시작 엘리먼트: 부모 엘리먼트, 부모 노드
    - 하위 엘리먼트: 자식 엘리먼트

 1. fromstring() 함수
  - XML 문자열 파이썬 객체로 변환
  - 제일 먼저 보이는 객체 이름이 x_str에서 가장 문저 등장하는 부모 엘리먼트 이름

 2. findtext() 메서드
 - 자식 엘리먼트 확인
 - XML이름.findtext()로 사용
 - list()를 통해서 이름 확인도 가능. But 자식 엘리먼트 순서가 항상 일정하지 않기 때문에 이 방법은 위험.

 3. findall() 메서드 & for 문
 - 여러 개의 자식 엘리먼트 확인
```python
for bok in books.findall('book'):
  name = bok.findtext('name')
  author = bok.findtext('author')
  year = bok.findtext('year')
  print(name)
  print(author)
  print(year)
  print()
```

 4. read_xml()
 - XML을 데이터프레임으로 변환 (by pandas)


### 📍API로 20대가 가장 좋아하는 도서 찾기

**회사 판매 데이터에는 구매자의 나이가 없다. 도서관 정보나루 사이트에서 나이별로 대출 데이터를 찾아 분석해보자**

#### ✔️API 호출 URL 작성
 > http://data4library.kr/api/loanltemSrch?authKey=[발급받은키]&startDt=2016-01-01&endDt=2016-05-158 gender=0&from_age=6&to_age=10&region=11&addCode=0&kdc=8
 - 호출 URL: http：//data41ibrary.kr/api/loanltemSrch
 - 파라미터
    - format: 지정하지 않으면 XML 문서로 변환
    - startDt: 검색 시작 일자
    - endDt: 검색 종료 일자
    - age: 연령대
    - authKey: 인증키
 - HTTP GET 방식
    - 웹 브라우저가 웹 서버에 요청할 때 URL로 파라미터 값이나 데이터를 전달하는 방식
    - = 문자: 파라미터와 값 연결
    - & 문자: 파라미터 사이 연결
    - ? 문자: 호출 URL과 파라미터 연결
    - 쿼리 스트링: 문자 뒤에 연결된 파리미터 값

#### ✔️파이썬으로 API 호출: requests 패키지
```python
import requests
url = ~
r = requests.get(url)
```
 - for 문으로 가져온 JSON 데이터 정리
 - to_json() 메서드로 파일을 json으로 저장


### 📍 표로 정리하는 핵심 함수와 메서드

| 함수/메서드 | 기능 |
| :--- | :--- |
| `json.dumps()` | 파이썬 객체를 JSON 문자열로 변환 |
| `json.loads()` | JSON 문자열을 파이썬 객체로 변환 |
| `pandas.read_json()` | JSON 문자열을 판다스 시리즈나 데이터프레임으로 변환 |
| `xml.etree.ElementTree.fromstring()` | XML 문자열을 분석하여 xml.etree.ElementTree.Element 클래스 객체를 반환 |
| `xml.etree.ElementTree.Element.findtext()` | 지정한 태그 이름과 맞는 첫 번째 자식 엘리먼트의 텍스트를 반환 |
| `xml.etree.ElementTree.Element.findall()` | 지정한 태그 이름과 맞는 모든 자식 엘리먼트를 반환 |
| `requests.get()` | HTTP GET 방식으로 URL을 호출하고 requests.Response 객체를 반환 |
| `requests.Response.json()` | 응답받은 JSON 문자열을 파이썬 객체로 변환하여 반환 |


## 02.웹 스크래핑 사용하기

**웹 사이트에 접속해서 필요한 정보를 가져오는 방법 (직접 HTML의 내용을 읽어 정보 뽑아내기)**

### 📍검색 결과 페이지 가져오기
 - gdown 패키지 이용 (gdown.download('url', '이름', quiet=False))

#### ✔️데이터프레임 행과 열 선택: loc 메서드
 - 대괄호 사용해서 행과 열의 목록을 받음
    - ex: books_df.loc[[0,1], ['bookname','authors']]
 - 슬라이스 연산자(:) 이용 가능
    - ex: books_df.loc[0:1, ['bookname','authors']]
    - 슬라이스 "어쩌구:저쩌구:고쩌구"에서 마지막 부분은 얼마나 건너뛸 건지 설정

#### ✔️검색 결과 페이지 HTML 가져오기: requests.get() 함수
 - requests.get(url.format(isbn))


### 📍HTML에서 데이터 추출: 뷰티플수프
(최근에는 스크래피(Scrapy)도 많이 사용. But 코랩에 설치 X)

#### ✔️크롬 개발자 도구로 HTML 태그 찾기
 - 마우스 오른쪽 버튼 → [검사] 선택
 - 이때 나오는 창을 **개발자 도구**라고 함
 - 간단하게 F12키 눌러서 볼 수 있음

<br>

 - 뷰티플수프 사용
``` python
from bs4 import BeautifulSoup
soup = BeautifulSoup(r.text, 'html.parser')
```

#### ✔️태그 위치 찾기: find() 메서드
- 첫 번째 매개변수에는 찾을 태그 이름 지정
- attrs 매개변수에는 태그 속성을 딕셔너리로 지정
```python
prd_link = soup.find('a', atrs={'class':'gd_name'})
```

#### ✔️도서 상세 페이지 HTML 가져오기
- requests.get() 함수 사용

#### ✔️테이블 태그 리스트로 가져오기: find_all() 메서드
- 특정 HTML 태그를 모두 찾아서 리스트로 반환
- 이름.findall('태그이름')

#### ✔️태그 안의 텍스트 가져오기: get_text() 메서드
- 특정 태그 안에 있는 텍스트 가려오려고 사용
- if 문과 함께 사용
- split() 메서드로 리스트에서 보고 싶음 원소만 선택 가능
    - 이름.split()[인덱스]


### 📍전체 도서의 쪽수 구하기

 1. 온라인 서점의 검색 결과 페이지 URL을 만듭니다.
 2. `requests.get()` 함수로 검색 결과 페이지의 HTML을 가져옵니다.
 3. 뷰티플수프로 HTML을 파싱합니다.
 4. 뷰티플수프의 `find()` 메서드로 `<a>` 태그를 찾아 상세 페이지 URL을 추출합니다.
 5. `requests.get()` 함수로 다시 도서 상세 페이지의 HTML을 가져옵니다.
 6. 뷰티플수프로 HTML을 파싱합니다.
 7. 뷰티플수프의 `find()` 메서드로 '품목정보' `<div>` 태그를 찾습니다.
 8. 뷰티플수프의 `find_all()` 메서드로 '쪽수'가 들어있는 `<tr>` 태그를 찾습니다.
 9. 앞에서 찾은 테이블의 행에서 `get_text()` 메서드로 `<td>` 태그에 들어 있는 '쪽수'를 가져옵니다.

#### ✔️데이터프레임 행 or 열에 함수 적용: apply() 메서드
- 데이터프레임이름.apply(적용할 함수, axis = 0 또는 1)
    - axis=0은 열에 함수 적용, axis=1은 행에 함수 적용
- 람다 함수
    - 데이터프레임이름.apply(lambda 매개변수:리턴할 값:적용할 열 또는 행)


#### ✔️데이터프레임과 시리즈 합치기: merge() 함수
- pd.merge(데이터프레임, 시리즈, left_index=True, right_index=True)
    - 인덱스 기준으로 합칠 경우 left_index=True, right_index=True 해야 함


### 📍주의할 점
 1. 웹사이트에서 스크래핑 허락했는지 확인
 2. 태그를 특정할 수 있는지 확인


### 📍merge() 함수의 매개변수
 
 1. on 매개변수: 합칠 때 기준이 되는 열 지정 (두 데이터프레임에 열이 존재해야 함)
 - pd.merge(df1, df2, on='col')

 2. how 매개변수: 합쳐질 방식 지정
 - inner: 두 데이터프레임의 값이 같은 행만 합침
 - left: 첫 번째 데이터프레임을 기준으로 두 번째 데이터프레임 합침
 - right: 두 번째 데이터프레임을 기준으로 첫 번째 데이터프레임 합침
 - outer: 두 데이터프레임의 모든 행을 유지하면서 합침
 - pd.merge(df1, df2, how='left' ~)

 3. left_on과 right_on 매개변수
 - 합칠 기준이 되는 열의 이름이 서로 다를 경우 두 매개변수에 각기 지정 가능
 - pd.merge(df1, df2, left_on='col1', right_on='col1')

 4. left_index와 right_index 매개변수
 - 합칠 기준이 열이 아니라 인덱스인 경우에 사용
 - pd.merge(df1, df2, left_on='col2', right_index=True)


### 📍표로 정리하는 핵심 함수와 메서드

| 함수/메서드 | 기능 |
| :--- | :--- |
| `loc` | 레이블(이름) 또는 불리언 배열로 데이터프레임의 행과 열을 선택합니다. 정수로 지정하면 인덱스의 레이블로 간주합니다. 불리언 배열로 지정할 경우 배열의 길이는 행 또는 열의 전체 길이와 같아야 합니다. |
| `BeautifulSoup.find()` | 현재 태그 아래의 자식 태그 중에서 지정된 이름에 맞는 첫 번째 태그를 찾습니다. 찾은 태그가 없을 경우 `None`이 반환됩니다. |
| `BeautifulSoup.find_all()` | 현재 태그 아래의 자식 태그 중에서 지정된 이름에 맞는 모든 태그를 찾습니다. 뷰티플수프 객체를 함수처럼 호출할 경우 자동으로 `find_all()` 메서드가 호출됩니다. 찾은 태그가 없을 경우 빈 리스트가 반환됩니다. |
| `BeautifulSoup.get_text()` | 태그 안의 텍스트를 반환합니다. |
| `DataFrame.apply()` | 데이터프레임의 행 또는 열에 지정한 함수를 적용합니다. |
| `pandas.merge()` | 데이터프레임이나 시리즈 객체를 합칩니다. |




# 2️⃣ 수행 인증

![result1](./image/week_2(1).png)
![result2](./image/week_2(2).png)
![result3](./image/week_2(3).png)
![result4](./image/week_2(4).png)



<br>
<br>

# 3️⃣ 확인 문제

## 문제 1.

> **🧚Q. 다음 중 BeautifulSoup 외에 웹 스크래핑에 사용할 수 있는 파이썬 패키지로 가장 적절한 것은 무엇인가요?**

```
1️⃣ NumPy  
2️⃣ Scrapy  
3️⃣ Matplotlib  
4️⃣ Scikit-learn  
```

```
2. Scrapy

Scrapy는 파이썬으로 작성된 웹 크롤링 및 스크래핑 프레임워크입니다.
BeutifulSoup가 단순히 HTML을 해석하는 도구라면, Scrapy는 웹 사이트를 돌아다니며 데이터를 수집하고 저장하는 기능을 제공합니다. 매우 효율적이지만, 코랩에는 활성화되어있지 않아 다른 툴을 사용해야 합니다.
```



### 🎉 수고하셨습니다.