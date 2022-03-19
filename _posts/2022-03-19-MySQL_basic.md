---
layout: single
title: "[MySQL] 기초 문법"
subtitle: 
categories: [mysql]
tag: [database, mysql, syntax]
toc: true
toc_sticky: true
---

# [MySQL] 기초 문법  

## 기본 명령어  

### CREATE  

> 설명  

- 데이터베이스 또는 테이블을 생성  

``` sql
-- 데이터베이스 생성
CREATE DATABASE [데이터베이스 이름];

-- 테이블 생성
CREATE TABLE 테이블 이름(
    [컬럼명1] [데이터타입] [컬럼1조건],
    [컬럼명2] [데이터타입] [컬럼2조건],
    [컬럼명3] [데이터타입] [컬럼3조건]
);
```  

> 예시  

```sql
CREATE DATABASE studentdb;

CREATE TABLE studenttbl(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(5) NOT NULL,
    birth DATE,
    phone VARCHAR(15),
    gender CHAR(2),
    kor INT,
    eng INT,
    mat INT
);
```  

> 조건 목록  

- NOT NULL : 데이터 삽입 시 무조건 내용이 있어야 함.  
- AUTO_INCREMENT : 자동으로 1씩 증가시킴(중복이 되면 안되는 id 설정)  
- PRIMARY KEY : 해당 테이블에서 인자 value 가 고유값임을 선언함.  
- UNIQUE : PRIMARY KEY와 유사하지만 NULL 을 허용함.  
- FOREIGN KEY : 하나의 테이블을 다른 테이블과 연결할 때 사용함.  
- DEFAULT : 기본값.  

<br>  

### USE  

> 설명  

- 쿼리를 수행하기 위해서는 우선 데이터베이스가 지정되어야 합니다.  
- 현재 사용하는 데이터베이스를 지정하기 위한 명령  

```sql
USE [데이터베이스 이름];
```  

> 예시  

```sql
USE studentdb;
```  

### SHOW  

> 설명  

- 데이터베이스 또는 테이블을 모두 보여줍니다.  

```sql
-- MySQL 내의 모든 데이터베이스들을 보여줌.
SHOW DATABASES;

-- 선택한 데이터베이스 내의 모든 테이블들의 이름을 보여줌.
SHOW TABLES;

-- 테이블들의 상세 정보를 보여줌.
SHOW TABLE STATUS;  
```  

<br>  

### DESCRIBE, EXPLAIN  

> 설명  

- 생성된 테이블의 상세정보 확인(내용이 아니고 테이블 설정들을 확(필드, 타입, Null 가능여부 등))  

```sql
 DESCRIBE [테이블 이름];
 DESC [테이블 이름];
 EXPLAIN [테이블 이름];
```  

<br>  

### INSERT  

> 설명  

- 테이블 데이터를 삽입합니다.  
- 작성하는 순서대로 컬럼에 데이터가 삽입됩니다.  
- 컬럼의 순서가 바뀌면 값도 컬럼의 순서에 맞게 바뀌어야 합니다.  

```sql
 INSERT INTO [테이블 이름] (컬럼명1, 컬럼명2, ...) VALUES (값1, 값2, ...);
```  

> 예시  

```sql
-- id는 auto_increment 설정이 되어있어서 null로 하면 자동으로 숫자가 생성됨
INSERT studenttbl(id, name, birth, phone, gender, kor, eng, mat) 
VALUES (NULL,'김성근','1987-01-05','010-8345-5684','M',80,60,100);

-- 값을 컬럼 순서대로 입력을 하면 컬럼명은 따로 입력하지 않아도 됨
INSERT studenttbl 
VALUES (NULL,'박준우','1980-03-03','010-7894-5896','M',31,80,30);

-- 컬럼의 순서가 바뀌면 값도 컬럼의 순서에 맞게 바꾸어야 함
INSERT studenttbl(id, gender, phone, name, birth, kor, eng, mat) 
VALUES (NULL,'F','010-7458-2345','조성현','1989-02-10',25,45,50);
```  

<br>  

### SELECT  

> 설명  

- SELECT 문은 데이터베이스 내의 테이블에서 원하는 정보를 추출하는명령  
- 여러 개의 열을 추출할 경우 쉽표로 구분해서 추가할 수 있음.  
- 여러 개의 열은 작성한 순서로 정보가 추출됨  

```sql
SELECT [열 이름1], [열 이름2], ... FROM [테이블 이름];

-- 열 이름을 "*" 로 대체하면 모든 열을 다 볼 수 있음
SELECT * FROM [테이블 이름];

-- 다른 데이터베이스에 있는 테이블 확인 시 데이터베이스명도 같이 입력
SELECT * FROM [데이터베이스명].[테이블명];
```  

> 예시  

```sql
-- id, name, birth 순서로 결과가 나옴
SELECT id, name, birth FROM studenttbl;  

-- 테이블의 모든 데이터가 결과로 나옴
SELECT * FROM studenttbl;

-- 다른 데이터베이스에 있는 테이블의 데이터 확인
SELECT * FROM studentdb.studenttbl;
```

<br>  

### WHERE  

> 설명  

- SELECT 문으로 정보를 추출할 때 조건을 설정할 수 있음.    

```sql
SELECT * FROM [테이블 이름] WHERE [조건식];
```  

> 예시  

```sql
-- 성별이 'M' 인 학생의 데이터가 결과로 나옴
SELECT * FROM studenttbl WHERE gender = 'M';
```  

<br>  

### ALTER  

> 설명  

- 테이블을 추가, 수정  

```sql
-- 테이블 이름 변경
ALTER TABLE [기존테이블 이름] RENAME [변경테이블 이름];

-- 컬럼 추가
ALTER TABLE [테이블 이름] ADD COLUMN [컬러명] [데이터타입] [컬럼조건];

-- 컬럼 타입 변경
ALTER TABLE [테이블 이름] MODIFY COLUMN [컬럼명] [데이터타입];

-- 컬럼명 변경
ALTER TABLE [테이블 이름] CHANGE COLUMN [변경 전 컬럼명] [변경 후 컬럼명] [데이터타입];

-- 컬럼 삭제
ALTER TABLE [테이블 이름] DROP COLUMN [컬럼명];

-- Primary Key 설정
ALTER TABLE [테이블 이름] ADD PRIMARY KEY (Key [설정 컬럼명1], Key [설정 컬럼명2]);

-- Primary Key 삭제
ALTER TABLE [테이블 이름] DROP PRIMARY KEY;
```  

<br>  

### UPDATE  

> 설명  

- 기존 데이터에 내용을 추가, 수정  
- 조건을 설정하지 않으면 테이블 내 컬럼의 모든 레코드가 수정될 수 있으니 주의할 것
- 처음 데이터를 수정하면 1175 Error 가 발생할 수 있는데, 안전모드가 설정되어있으면 key 열을 조건으로 설정을 해야하기 때문에 SQL Editor에서 Safe Updates를 체크해제 하거나 설정을 바꾸는 쿼리를 실행해주어야 합니다.  

```sql
UPDATE [테이블 이름] SET [컬럼 이름] = [값] WHERE [조건];
```  

> 예시  

```sql
-- 테이블에서 name 이 '김성근' 인 학생의 kor, eng 점수를 수정
UPDATE studenttbl SET kor = 80, eng = 60 WHERE name='김성근';

-- Safe Updates 해제 쿼리
SET sql_safe_updates = 0;
```  

<br>  

### DELETE, DROP  

> 설명  

- 테이블이나 데이터베이스를 삭제합니다.  
- 항상 데이터를 삭제하기 전 백업을 하는 것이 좋습니다.  

```sql
-- 조건에 일치하는 행의 데이터를 삭제
DELETE FROM [테이블 이름] WHERE [조건];

-- 테이블 또는 데이터베이스 전체를 삭제
DROP TABLE [테이블 이름];
DROP DATABASE [데이터베이스 이름];
```  

> 예시  

```sql
-- id가 2인 학생의 데이터 삭제
DELETE FROM studenttbl WHERE id=2;

-- 테이블 내용 전체 삭제(틀은 남아있고 레코드만 삭제)
DELETE FROM studenttbl;

-- 테이블 삭제
DROP TABLE studenttbl;

-- 데이터베이스 삭제
DROP DATABASE studentdb;
```





<br><br><br>

# <strong>Reference</strong>  

- [w3school](https://www.w3schools.com/mysql/mysql_select.asp){:target="_blank"}  
- [MySQL 기초](https://brunch.co.kr/@topherlee/67){:target="_blank"}  
- [MySQL 기본 명령어](http://leechoong.com/posts/2018/mysql_basic/){:target="_blank"}  
- [MySQL 사용법 및 관리, 명령어](https://shyunku.tistory.com/43){:target="_blank"}  
- [ALTER TABLE 문법 총 정리](https://java119.tistory.com/83){:target="_blank"}  

