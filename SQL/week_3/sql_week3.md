# SQL_BASIC 3주차 정규 과제 

📌SQL_BASIC 정규과제는 매주 정해진 분량의 `초보자를 위한 BigQuery(SQL) 입문` 강의를 듣고 간단한 문제를 풀면서 학습하는 것입니다. 이번주는 아래의 **SQL_Basic_3rd_TIL**에 나열된 분량을 수강하고 `학습 목표`에 맞게 공부하시면 됩니다.

**3주차 과제는 문제 풀이를 중심으로**, 강의에서 제시된 예제 문제 중 **7 문제 이상을 선택하여 직접 풀어본 뒤**, 강의 영상의 풀이와 비교해 **틀린 부분, 맞은 부분, 새롭게 배운 개념**을 구체적으로 정리해주세요. (적어도 3문제는 정리해야 합니다.) 완성된 과제는 Gihub에 업로드하고, 링크를 스프레드시트 'SQL' 시트에 입력해 제출해주세요.

**👀(수행 인증샷은 필수입니다.)** 

## SQL_BASIC_3rd

### 섹션 3. 데이터 탐색 - 조건, 추출, 요약

### 2-6. 연습문제 1~3번

### 2-6. 연습문제 7~9번

### 2-6. 연습문제 10~12번

### 2-6. 연습문제 13~17번

### 2-7. 정리 

### 2-8. 새로운 집계함수



## 섹션 4. 쿼리 잘 작성하기, 쿼리 작성 템플릿 및 오류를 잘 디버깅하기

### 3-1. INTRO

### 3-2. SQL 쿼리 작성하는 흐름

### 3-3. 쿼리 작성 템플릿과 생산성 도구 



## 🏁 강의 수강 (Study Schedule)

| 주차  | 공부 범위              | 완료 여부 |
| ----- | ---------------------- | --------- |
| 1주차 | 섹션 **1-1** ~ **2-2** | ✅         |
| 2주차 | 섹션 **2-3** ~ **2-5** | ✅         |
| 3주차 | 섹션 **2-6** ~ **3-3** | ✅         |
| 4주차 | 섹션 **3-4** ~ **4-4** | 🍽️         |
| 5주차 | 섹션 **4-4** ~ **4-9** | 🍽️         |
| 6주차 | 섹션 **5-1** ~ **5-7** | 🍽️         |
| 7주차 | 섹션 **6-1** ~ **6-6** | 🍽️         |

<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 개념정리

## 2-6. 연습문제

~~~
✅ 학습 목표 :
* 연습문제(7문제 이상) 푼 것들 정리하기
~~~

### 1. 포켓몬 중에 type2가 없는 포켓몬의 수를 작성하는 쿼리 작성

```sql
SELECT  
  count(id) as cnt
FROM `inflearn-bigquery123.basic.pokemon` 
where
  type2 is null
  And type1 = 'Fire'

-- where 절에서 여러 조건을 연결 → and 조건문 사용
-- or 조건 >> ( ) or ( ) >> 항상 괄호 필요
```

### 2. type2가 없는 포켓몬의 type1과 type1의 포켓몬 수를 알려주는 쿼리 작성. type1의 포켓몬 수가 큰 순 으로 정렬.

```sql
select
  type1,
  count(id) as pokemon_cnt
  -- 집계 함수는 group by와 함께 다님. 기준이 없으면 count만 쓸 수 있지만, 집계하는 기준이 있다면 그 기준 컬럼을 group by에 써줘야 함.
from basic.pokemon
where
  type2 is null
group by 
  type1
order by
  pokemon_cnt DESC
```


### 3. type2 상관없이 type 1의 포켓몬 수를 알 수 있는 쿼리 작성

```sql
select
  type1,
  count (id) as cnt_type1
from basic.pokemon
group by type1
```

### 4. 전설 여부에 따른 포켓몬 수

```sql
select
  is_legendary,
  count(id) as cnt
from basic.pokemon
group by
  is_legendary
  -- group by 1 >> select의 첫 컬럼
  -- order by에도 적용됨
  ```


### 5. 동명 이인이 있는 이름

```sql
select
  name,
  count(name) as trainer_cnt
from basic.trainer
group by
  name
-- 집계 후 조건은 having
having
  trainer_cnt >= 2
```


### 6. trainer 테이블에서 "Iris" 트레이너의 정보를 알 수 있는 쿼리 작성

```sql
select
  *
from basic.trainer
where
  name = 'Iris'
```


### 7. trainer 테이블에서 'Iris', 'Whitney', 'Cynthia' 트레이너의 정보를 알 수 있는 쿼리 작성

```sql
select
  *
from basic.trainer
where
  (name = 'Iris')
  or (name = 'Whitney')
  or (name = 'Cynthia')
-- or 조건 대신에 in 사용 가능
-- name in ('Iris', 'Whitney', 'Cynthia')
```



### 8. 전체 포켓몬 수는?

```sql
select
  count(id) as pokemon_cnt
from basic.pokemon
```


### 9. 세대별로 포켓몬 수가 얼마나 되나?

```sql
select
  generation,
  count(id) as pokemon_cnt
from basic.pokemon
group by
  generation
```


### 10. type2가 존재하는 포켓몬의 수

```sql
select
  count(id) as pokemon_cnt
from basic.pokemon
where
  type2 is not null
```


### 11. type2가 있는 포켓몬 중에 가장 많은 type1?

```sql
select
  type1,
  count(id) as pokemon_cnt
from basic.pokemon
where
  type2 is not null
group by
  type1
order by
  pokemon_cnt desc
limit 1
```


### 12. 단일 타입 포켓몬 중 많은 type1?

```sql
select
  type1,
  count(id) as pokemon_cnt
from basic.pokemon
where
  type2 is null
group by
  type1
order by
  pokemon_cnt desc
limit 1
```


### 13. 포켓몬 이름에 '파'가 들어가는 포켓몬?

```sql
select
  kor_name
from basic.pokemon
where
  kor_name like '%파%'
  -- 컬럼 like '특정단어%'
  -- '%파': 파로 끝나는 단어, '파%': 파로 시작하는 단어, '%파%': 파가 들어가는 단어
```


### 14. 뱃지가 6개 이상인 트레이너는 몇 명?

```sql
select
  count(id) as trainer_cnt
from basic.trainer
where
  badge_count >= 6
```


### 15. 트레이너가 보유한 포켓몬(trainer_pokemon)이 제일 많은 트레이너는 누구?

```sql
select
  *
from `basic.trainer_pokemon`
where
  trainer_id = 5
```


### 16. 포켓몬을 많이 풀어준 트레이너는 누구?

```sql
select
  trainer_id,
  count(pokemon_id) as pokemon_cnt
from `basic.trainer_pokemon`
where
  status = 'Released'
group by
  trainer_id
order by
  pokemon_cnt desc
limit 1
```


### 17. 풀어준 포켓몬 비율이 20%가 넘는 포켓몬 트레이너는 누구?

```sql
-- countif(조건) 사용

select 
  trainer_id,
  countif(status = 'Released'), # 풀어준 포켓몬 수
  count(pokemon_id) as pokemon_cnt,
  countif(status = 'Released') / count(pokemon_id) as released_ratio
from basic.trainer_pokemon
group by 
  trainer_id
having
  released_ratio >= 0.2
```







## 2-8. 새로운 집계함수

~~~
✅ 학습 목표 :
* SQL 쿼리 구조를 이해할 수 있다. 
* SELECT, FROM, WHERE을 활용하는 방법을 설명할 수 있다. 
~~~

### 1. GROUP BY ALL

컬럼을 하나씩 다시 적을 필요가 없이 알아서 처리해줌.


## 3-2. 쿼리를 작성하는 흐름

~~~
✅ 학습 목표 :
* 쿼리를 작성하는 흐름을 설명할 수 있다.
~~~

### 1. SQL 쿼리 흐름표

| 순서 | 절차 | 내용 |
|:----:|------|------|
| 1 | 지표 고민 | 문제정의. 어떤 데이터가 문제를 해결하기 위해 필요한가? |
| 2 | 지표 구체화 | 추상적이지 않은 구체적인 지표 명시 (분자, 분모 표시) |
| 3 | 지표 탐색 | 유사한 문제를 해결한 케이스가 있나 확인 >(존재)> 해당 쿼리 리뷰 |
| 4 | 쿼리 작성 | 데이터가 있는 테이블 찾기 (1개면 바로 작성. 2개 이상이면 연결 방법 고민(join)) |
| 5 | 데이터 정한성 확인 | 예상한 결과와 동일한지 확인 |
| 6 | 쿼리 가독성 | 나중을 대비해 깔끔하게 쿼리 작성 |
| 7 | 쿼리 저장 | 쿼리는 재사용되므로 문서로 저장 |



## 3-3. 쿼리 작성 템플릿과 생산성 도구

~~~
✅ 학습 목표 :
* 생산성 도구를 만들 수 있다.
~~~

### 1. 템플릿 구조

```sql
-- 쿼리를 작성하는 목표, 확인할 지표:
-- 쿼리 계산 방법:
-- 데이터의 기간:
-- 사용할 테이블:
-- join KEY:
-- 데이터 특징:

SELECT

FROM
WHERE
```

### 2. 생산성 도구: Espanso

- 윈도우, mac 모두 사용 가능한 프로그램(무료)
- 특정 단어를 입력하면 원하는 문장(템플릿)으로 변경



<br>
<br>

---

# 2️⃣ 학습 인증란

![학습 인증샷](./sql_week3.png)



<br><br>



---

# 3️⃣ 확인문제

## 문제 1

> **🧚Q. Q. 포켓몬 연구에 흥미를 느낀 혜인은 각 타입(type1)별 평균 공격력(attack)을 비교해보고 싶었습니다.**
>
> 그래서 다음과 같은 필요한 정보를 미리 정리해보았습니다. 

~~~
조건 : attack이 50 이상인 포켓몬만 포함
보고 싶은 컬럼 : type1
집계 내용 : 각 type1 별 평균 공격력
정렬 기준 : 평균 공격력을 기준으로 내림차순 정렬
~~~

> **이 목표를 바탕으로 혜인은 아래와 같은 쿼리를 작성했지만, 일부 SQL 문법 요소를 빼먹었습니다. 비어 있는 부분인 ㄱ, ㄴ, ㄷ, ㄹ 에 들어갈 알맞은 SQL 구문을 채워보세요:**

~~~sql
SELECT type1, (ㄱ)
FROM pokemon
(ㄴ) attack >= 50
(ㄷ) type1
ORDER BY (ㄱ) (ㄹ);
~~~



~~~
SELECT
    type1, 
    AVG(attack)
FROM pokemon
Where attack >= 50
GROUP BY type1
ORDER BY AVG(attack) DESC;


(ㄱ): AVG(attack)
(ㄴ): Where
(ㄷ): GROUP BY
(ㄹ): DESC
~~~



### 🎉 수고하셨습니다.