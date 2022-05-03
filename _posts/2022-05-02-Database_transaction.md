---
published: true
layout: single
title: "[Database] 트랜잭션(transaction)"
subtitle: 
categories: [database]
tag: [database, mysql, transaction]
toc: true
toc_sticky: true
---  

# [Database] 트랜잭션(transaction)  

## 트랜잭션 이란?  

- 데이터베이스의 상태를 변환시키는 하나의 논리적 기능을 수행하기 위한 작업의 단위 또는 한꺼번에 모두 수행되어야 할 일련의 연산들을 의미합니다.  

- 작업의 단위는 질의어 한 문장만을 의미하는 것이 아니라, 많은 질의어들을 사람이 정하는 기준에 따라 정하는 것을 의미합니다.  

- UPDATE또는 DELETE를 하는 경우 실수로 WHERE절을 쓰지 않고 실행하면 테이블에 있는 칼럼의 데이터가 모두 바뀌거나 삭제가 되는데 이런 위험성이 있는 작업의 경우 트랜잭션 안에서 실행하게 되면 최종 확인 후 Commit 또는 Rollback으로 안정적인 데이터베이스 작업이 가능합니다.  

<br>  

## 트랜잭션의 특징 

> 원자성(Atomicity)  

- 트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 합니다.  

- 트랜잭션 내의 모든 명령은 반드시 완벽히 수행되어야 하며, 모두가 완벽히 수행되지 않고 어느 하나라도 오류가 발생하면 트랜잭션 전부가 취소되어야 합니다.  

- 트랜잭션 단위로 데이터가 처리되지 않으며, 설계한 사람은 데이터 처리 시스템을 이해하기 힘들 뿐만 아니라, 오작동 시 원인을 찾기가 매우 힘들어집니다.  

> 일관성(Consistency)  

- 트랜잭션이 실행을 완료하면 언제나 일관성 있는 데이터베이스 상태로 변환합니다.  

- 트랜잭션이 진행되는 동안 데이터베이스가 변경되더라도 업데이트된 데이터베이스로 트랜잭션이 진행되는 것이 아니라, 처음에 트랜잭션을 진행하기 위해 참조한 데이터베이스로 진행됩니다.  

> 독립성(Isolation)  

- 둘 이상의 트랜잭션이 동시에 병행 실행되는 경우 어느 하나의 트랜잭션 실행 중에 다른 트랜잭션의 연산이 끼어들 수 없습니다.  

- 수행중인 트랜잭션은 완전히 완료될 때까지 다른 트랜잭션에서 수행 결과를 참조할 수 없습니다.  

> 지속성(Durability)  

- 성공적으로 완료된 트랜잭션의 결과는 시스템이 고장나더라도 영구적으로 반영되어야 합니다.  

<br>  

## 트랜잭션의 상태  

![transaction](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/transaction.png?raw=true)

1. 활성(Active)  

    - 트랜잭션이 정상적으로 실행중인 상태를 의미합니다.  

2. 작업 성공 시  

    - 부분 완료(Partially Committed): 트랜잭션이 마지막까지 실행되었지만, Commit 연산이 실행되기 직전의 상태입니다.  

    - 완료(Committed): 트랜잭션이 성공적으로 종료되어 Commit 연산을 실행한 후의 상태입니다.  

    - 부분완료 후 설계자가 결과에 대하여 반영을 승인(Commit)하면 트랜잭션이 성공적으로 종료됩니다.  

3. 작업 실패 시  

    - 실패(Failed): 트랜잭션 실행에 오류가 발생하여 중단된 상태입니다.  

    - 철회(Aborted): 트랜잭션이 비정상적으로 종료되어 Rollback 연산을 실행한 상태입니다.  

    - 실패 후 트랜잭션 내부의 작업을 다시 수행 이전의 상태로 돌리는 Rollback 연산을 수행하면 그 상태를 철회(Aborted)라고 합니다.  

> Commit  

- 모든 작업들을 정상 처리하겠다고 확정하는 명령어로서, 해당 처리 과정을 DB에 영구 저장하겠다는 의미입니다.  

- Commit을 수행하면 하나의 트랜잭션 과정이 종료가 되며, 이전 데이터가 UPDATE 됩니다.  

> Rollback  

- 작업 중 문제가 발생되어 트랜잭션의 처리 과정에서 발생한 변경사항을 취소하는 명령어입니다.  

- 트랜잭션이 시작되기 이전의 상태로 되돌아가는 것이므로, 마지막으로 Commit을 완료한 시점으로 돌아간다는 말과 같습니다.  

<br>

## 트랜잭션 사용예제(MySQL)  

- 은행 계좌에서 'A'라는 사람이 'B'에게 돈을 이체하는 상황에서 쿼리문 중간에 실수로 'B'의 계좌에 잘못된 금액을 입금하는 경우가 생길 수 있습니다. 이럴 때 트랜잭션 내에서 계좌 이체 작업을 실행하면 중간에 오류가 발생한 경우 이체하기 전 상태로 되돌릴 수 있습니다.  

> 트랜잭션 사용 전  

- 'A'계좌에서 'B'계좌로 이체 시 중간에 오류가 발생하게되면 다시 원래상태로 돌려놓아야 하지만 복구하기가 상당히 어렵습니다.  

```sql
-- 계좌 테이블 생성
CREATE TABLE IF NOT EXISTS bank_account(
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(10) NOT NULL,
    amount INT NOT NULL
);

-- 이체내역 테이블 생성
CREATE TABLE IF NOT EXISTS bank_history(
    id INT AUTO_INCREMENT PRIMARY KEY,
    from_name VARCHAR(10) NOT NULL,
    to_name VARCHAR(10) NOT NULL,
    amount INT NOT NULL,
    transfer_date DATETIME
);

-- 계정 추가
INSERT INTO bank_account(name, amount) VALUES('A', 100000);
INSERT INTO bank_account(name, amount) VALUES('B', 50000);

/* 'A'가 'B'에게 5000원을 이체하는 과정 */
-- 1. 'A'의 계좌 잔액에서 5000원을 차감
UPDATE bank_account
    SET amount = amount - 5000
WHERE name = 'A';

-- 2. 실수로 'B'에게 50000원을 추가(오류 발생)
UPDATE bank_account
    SET amount = amount + 50000
WHERE name = 'B';

-- 중간에 'B'는 잘못된 금액이 추가되었지만 이체내역은 5000원으로 기록됨
-- 이체내역 테이블만 봤을 때는 어느 부분에 문제가 발생했는지 알기 어려움
INSERT INTO bank_history(from_name, to_name, amount, transfer_date)
VALUES('A', 'B', 5000, now());

-- 'B' 에 잘못된 금액이 UPDATE 되었지만 복구하기 어려움
SELECT * FROM bank_account;
```  

<br>  

> 트랜잭션 사용 시  

- `START TRANSACTION` 명령을 실행한 이후부터 `ROLLBACK` 또는 `COMMIT` 전까지의 명령 전체가 하나의 작업 단위가 됩니다.  

- 작업 중간에 오류가 있더라도 최종 확인 후 이전으로 되돌릴 수 있습니다.  

```sql
-- 트랜잭션 시작
START TRANSACTION;

/* 'A'가 'B'에게 5000원을 이체하는 과정 */
-- 1. 'A'의 계좌 잔액에서 5000원을 차감
UPDATE bank_account
    SET amount = amount - 5000
WHERE name = 'A';

-- 2. 실수로 'B'에게 50000원을 추가(오류 발생)
UPDATE bank_account
    SET amount = amount + 50000
WHERE name = 'B';

-- 중간에 'B'는 잘못된 금액이 추가되었지만 이체내역은 5000원으로 기록됨
INSERT INTO bank_history(from_name, to_name, amount, transfer_date)
VALUES('A', 'B', 5000, now());

-- 실행결과를 확인 후 오류를 발견하게되면 Rollback으로 다시 되돌릴 수 있음
ROLLBACK;

-- 트랜잭션 작업 이전으로 되돌아갔음을 확인
SELECT * FROM bank_account;
```  

<br>  

## 기타사항  

> 트랜잭션 예외 명령  

- CREATE, DROP, ALTER, RENAME, TRUNCATE 명령은 트랜잭션의 ROLLBACK 대상이 아닙니다.  

> 트랜잭션 전역 설정  

- MySQL에서는 auto commit이 ON으로 설정되어있어서, 하나의 명령어를 실행할 때마다 자동으로 commit을 해줍니다.  

- 이미 commit이 된 명령은 되돌릴 수 없기 때문에 auto commit 을 OFF로 설정을 하게되면 자동으로 commit이 되지 않고 직접 commit 또는 rollback을 실행해주어야 합니다.  

```sql
-- auto commit 설정 확인
SELECT @@autocommit;

-- 1로 설정하면 ON, 0으로 설정하면 OFF
SET AUTOCOMMIT = 1;
```





<br><br><br>

# <strong>Reference</strong>  

- [트랜잭션이란 무엇인가?](https://coding-factory.tistory.com/226){:target="_blank"}  
- [트랜잭션이란?](https://mommoo.tistory.com/62){:target="_blank"}  
- [트랜잭션이란? 100 정리](https://inpa.tistory.com/entry/MYSQL-%F0%9F%93%9A-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98Transaction-%EC%9D%B4%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC){:target="_blank"}  