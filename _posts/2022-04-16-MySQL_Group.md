---
published: true
layout: single
title: "[MySQL] 그룹화해서 데이터 조회"
subtitle: 
categories: [mysql]
tag: [database, mysql, syntax, group]
toc: true
toc_sticky: true
---  

# [MySQL] 그룹화해서 데이터 조회  

## GROUP BY  

> 설명  

- 특정 컬럼을 기준으로 그룹화하여 조회할 때 사용됩니다.   

> 사용법  

```sql
-- 컬럼 그룹화
SELECT [컬럼] FROM [테이블] GROUP BY [그룹화할 컬럼];

-- 조건 처리 후 컬럼 그룹화
SELECT [컬럼] FROM [테이블] WHERE [조건식] GROUP BY [그룹화할 컬럼];

-- 컬럼 그룹화 후 조건 처리
SELECT [컬럼] FROM [테이블] GROUP BY [그룹화할 컬럼] HAVING [조건식];

-- 조건 처리 후 그룹화를 하고, 그룹화된 컬럼을 조건 처리
SELECT [컬럼] FROM [테이블] WHERE [조건식] GROUP BY [그룹화할 컬럼] HAVING [조건식];

-- ORDER BY가 존재하는 경우
SELECT [컬럼] FROM [테이블] WHERE [조건식] GROUP BY [그룹화할 컬럼] HAVING [조건식] ORDER BY [컬럼1] (, [컬럼2], [컬럼3]);
```  

<br>  

## 집계 함수  

> 설명  

- 집계 함수는 주로 GROUP BY절과 함께 쓰이며 데이터를 그룹화해주는 기능을 합니다.  

<br>  

### SUM()  

- 합계를 구합니다.  

> 사용법  

```sql
-- 회원(userID) 별 총 구매 개수를 확인
SELECT userID, SUM(amount) FROM buy_tbl GROUP BY userID;
```  

<br>

### AVG()  

- 평균을 구합니다.  

> 사용법  

```sql
-- 회원(userID) 별 한 번 구매 시 물건을 평균 몇 개 구매했는지 확인
SELECT userID, AVG(amount) AS '평균 구매 개수' FROM buy_tbl GROUP BY userID;
```  

<br>

### MAX(), MIN()  

- 최대값과 최소값을 구합니다.  

> 사용법  

```sql
-- user_tbl 에서 키가 가장 큰 회원과 가장 작은 회원의 이름을 확인
SELECT name, height FROM user_tbl
    WHERE height = (SELECT MAX(height) FROM user_tbl)
        OR height = (SELECT MIN(height) FROM user_tbl);
```  

<br>

### COUNT()  

- 해당 컬럼에서 행의 갯수(NULL 제외)를 출력합니다.  

> 사용법  

```sql
-- user_tbl에서 모든 행의 갯수를 확인
SELECT COUNT(*) FROM user_tbl;

-- buy_tbl에서 userID의 갯수를 확인(중복되는 userID는 1 개만 카운트)
SELECT COUNT(DISTINCT userID) FROM buy_tbl;

-- user_tbl에서 휴대폰이 있는 회원(mobile1 값이 있는 회원)의 수를 확인
SELECT COUNT(mobile1) FROM user_tbl;
```  

<br>  

## HAVING  

- GROUP BY로 그룹화된 데이터의 조건을 제한할 때 사용됩니다.  
- WHERE절과 사용목적은 같으나, 대상이 다릅니다. (WHERE절은 그룹화 전의 데이터에 조건처리를 하고, HAVING절은 그룹화 후의 데이터에 조건처리)  

> 사용법  

```sql
-- buy_tbl에서 물품을 구매한 회원의 총 구매액이 1000 이상인 회원목록 확인
-- userID로 그룹화하여 나온 결과에 대해 조건을 제한하는 것이기 때문에 WHERE절이 아닌 HAVING절을 사용해야 함.
SELECT userID, SUM(amount*price) AS '총 구매액'
    FROM buy_tbl
    GROUP BY userID
    HAVING SUM(amount*price) >= 1000;

-- buy_tbl에서 모니터를 구매한 회원 중 모니터의 총 구매액이 1000 이상인 회원목록 확인
-- WHERE절을 사용해서 모니터를 구매한 회원의 데이터를 가지고와서 집계함수인 SUM()을 사용하였기 때문에 SUM()의 결과는 모니터의 총 구매액이 됨
SELECT userID, amount, SUM(amount*price) AS '모니터 총 구매액'
    FROM buy_tbl
    WHERE prodName = '모니터'
    GROUP BY userID
    HAVING SUM(amount*price) >= 1000
    ORDER BY SUM(amount*price) DESC;
```  

<br>

## ROLLUP  

- 총합 또는 중간 합계가 필요하다면 GROUP BY절과 함께 WITH ROLLUP문을 사용하면 됩니다.  

> 사용법  

```sql
-- 분류(groupName)별로 소합계 및 총합계를 확인
-- 그룹을 만드는 순서에 따라 결과가 다르게 나오기 때문에 그룹 순서에 주의한다. (GROUP BY 에서 groupName 과 num 의 순서가 바뀌면 다른 결과가 나옴)
SELECT num, groupName, SUM(price*amount) AS '비용'
    FROM buy_tbl
    GROUP BY groupName, num
    WITH ROLLUP;

-- 분류(groupName)별로 소합계와 총합계만 확인(num 제외)
SELECT groupName, SUM(price*amount) AS '비용'
    FROM buy_tbl
    GROUP BY groupName
    WITH ROLLUP;
```  



<br><br><br>  

# <strong>Reference</strong>  

- [컬럼을 그룹지어 통계를 파악하자](https://jhnyang.tistory.com/304){:target="_blank"}  
- [그룹 함수 다루기](https://codingspooning.tistory.com/144){:target="_blank"}  
- [그룹화하여 데이터 조회(GROUP BY)](https://extbrain.tistory.com/56){:target="_blank"}  
- [집계함수와 group by, having절, rollup](https://sso-feeling.tistory.com/118){:target="_blank"}  