---
layout: single
title: "[MySQL] WHERE 조건 검색하기"
subtitle: 
categories: [mysql]
tag: [database, mysql, syntax]
toc: true
toc_sticky: true
---

# [MySQL] WHERE 조건 검색하기  

## 개요  

> 설명  

- WHERE 절은 SELECT, DELETE, UPDATE 등 데이터를 선택 또는 수정 시 조건을 설정할 때 사용합니다.  
- WHERE 절에 조건이 없는 FTS(Full Table Scan)는 검색된 자료가 많아 문제가 발생합니다.  

> 연산자의 우선순위  

1. 괄호()  
2. NOT 연산자  
3. 비교연산자, SQL 연산자
4. AND  
5. OR  

<br>  

## 관계연산자  

> 설명  

- 비교 연산자는 주어진 좌우 값을 비교하는 연산자입니다.  
- date 타입은 문자열을 날짜 포멧으로 변환 후 비교를 해야합니다.  

```sql
-- 국어 성적이 50 초과인 학생들의 데이터를 추출
SELECT * FROM studenttbl WHERE kor > 50;

-- 수학 성적이 70 이하인 학생들의 데이터를 추출
SELECT * FROM studenttbl WHERE mat <= 70;

-- 성별이 'M' 인 학생들의 데이터를 추출
SELECT * FROM studenttbl WHERE gender = 'M';

-- 성별이 'M' 이 아닌 학생들의 데이터를 추출
SELECT * FROM studenttbl WHERE gender != 'M';
SELECT * FROM studenttbl WHERE gender <> 'M';

-- 날짜를 비교할 때에는 DATE() 함수를 사용해서 날짜 형식을 맞춘 후 비교
SELECT * FROM studenttbl WHERE DATE(birth) >= DATE('1987-01-01');
```  

<br>  

## 논리연산자  

> 설명  

- 참과 거짓을 비교하는 연산자입니다.  
- 두 가지 이상의 조건을 설정할 때 사용합니다.  

<br>

### AND  

- 여러 조건들이 모두 참일 때 결과값이 참이 나옵니다.  

```sql
-- 국어 성적이 50보다 크고, 80보다 작거나 같은 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE kor > 50 AND kor <= 80;

-- 수학 성적이 30보다 크고, 70보다 작은 학생 중 성별이 'F'인 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE (mat > 30) AND (mat < 70) AND (gender = 'F');
```  

<br>  

### OR  

- 여러 조건들 중 하나라도 참일 때 결과값이 참이 나옵니다.  

```sql
-- 국어 성적이 50보다 크거나, 영어 성적이 60보다 큰 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE kor > 50 OR eng > 60;

-- 국어, 영어, 수학 점수 중 하나라도 30점 이상 70점 미만인 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE 
(kor >= 30 AND kor < 70) OR
(eng >= 30 AND eng < 70) OR
(mat >= 30 AND mat < 70);
```  

<br>  

## SQL 연산자  

### IN  

> 설명  

- IN 안에 있는 값에 해당하는 데이터를 추출합니다.  
- OR 연산자와 마찬가지로 여러 값들 중 하나라도 있으면 해당 데이터를 추출합니다.  

```sql
--  국어 성적이 30이거나, 80인 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE kor IN(30, 80);
```  

<br>  

### BETWEEN a AND b  

> 설명  

- a 에서 b 사이의 모든 값을 추출합니다.  
- 숫자, 날짜, 숫자로 구성된 문자열의 경우 사용할 수 있습니다.  

```sql
-- id가 2에서 4사이인 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE id BETWEEN 2 AND 4;

-- 생일이 1980-01-01 에서 1989-10-10 사이인 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE birth BETWEEN DATE('1980-01-01') AND DATE('1989-10-10');
```  

<br>  

### LIKE  

> 설명  

- 특정 문자열이 포함되어있는 데이터를 추출합니다.  
- `%` 는 해당 위치에 0개부터 여러개의 문자열이 올 수 있습니다.  
- `_` 는 해당 위치에 1개의 문자가 올 수 있습니다.  

```sql
-- 이름이 "김"으로 시작하는 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE name LIKE '김%';

-- 이름에 "성"이 들어간 학생의 데이터를 추출("성"이 제일 앞이나 뒤에도 위치 가능)
SELECT * FROM studenttbl WHERE name LIKE '%성%';

-- 이름의 중간에 "성"이 들어간 학생의 데이터를 추출(반드시 "성"의 앞뒤에 한글자씩 있어야함)
SELECT * FROM studenttbl WHERE name LIKE '_성_';
```  

<br>  

### IS NULL  

> 설명  

- 필드의 값이 NULL 인 경우의 데이터를 추출합니다.  

```sql
-- 성별 필드에 값이 없는(NULL) 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE gender IS NULL;
```  

<br>  

### NOT  

> 설명  

- 부정의 의미로 사용됩니다.  

```sql
-- 성별이 'F'가 아닌 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE NOT gender = 'F';

-- id가 3, 5, 7이 아닌 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE id NOT IN(3, 5, 7);

-- id가 2와 4 사이의 값이 아닌 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE id NOT BETWEEN 2 AND 4;

-- 이름이 '김%' 이고 '박%' 인 학생이 아닌 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE name NOT LIKE('김%') AND name NOT LIKE('박%');

-- 성별에 값이 없는 학생이 아닌(값이 있는) 학생의 데이터를 추출
SELECT * FROM studenttbl WHERE gender IS NOT NULL;
```





<br><br><br>

# <strong>Reference</strong>  

- [w3school](https://www.w3schools.com/mysql/mysql_where.asp){:target="_blank"}  
- [연산자(Operator)](https://extbrain.tistory.com/50){:target="_blank"}  
- [MySQL 함수를 활용한 날짜비교 쿼리문 작성하기](https://gakari.tistory.com/entry/MySQL-%ED%95%A8%EC%88%98%EB%A5%BC-%ED%99%9C%EC%9A%A9%ED%95%9C-%EB%82%A0%EC%A7%9C%EB%B9%84%EA%B5%90-%EC%BF%BC%EB%A6%AC%EB%AC%B8-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0){:target="_blank"}  
- [WHERE 절의 조합](https://inforyou.tistory.com/28){:target="_blank"}  
- [#16 WHERE 절](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=loleego&logNo=221613157955){:target="_blank"}  


