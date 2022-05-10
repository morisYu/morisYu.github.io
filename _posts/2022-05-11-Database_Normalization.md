---
published: true
layout: single
title: "[Database] 정규화(Normalization)"
subtitle: 
categories: [database]
tag: [database, normalization]
toc: true
toc_sticky: true
---  

# [Database] 정규화(Normalization)  

## 정규화의 목적  

- 데이터의 중복을 배제하여 삽입, 삭제, 갱신 이상의 발생을 방지합니다.  
- 중복된 데이터를 허용하지 않음으로써 무결성(Integrity)을 유지할 수 있으며, DB의 저장 용량 또한 줄일 수 있습니다.  
- 데이터 삽입 시 릴레이션을 재구성할 필요성이 감소합니다.  
- 효과적인 검색 알고리즘을 생성 가능합니다.  

### 이상(Anomaly) 현상  

- 정규화를 거치지 않은 데이터베이스에서 발생할 수 있는 현상입니다.  
- 데이터들이 불필요하게 중복되어 릴레이션 조작에 예기치 못한 문제가 발생합니다.  
- Attribute 들의 종속관계를 하나의 Relation에 표현하기 때문에 발생합니다.  

> 이상의 종류  

- 삽입 이상(Insertion Anomaly)  
    - 데이터 삽입 시 의도와 다른 값들도 삽입됨  
- 삭제 이상(Delete Anomaly)  
    - 데이터 삭제 시 의도와 다른 값들도 연쇄 삭제됨  
- 갱신 이상(Update Anomaly)  
    - 속성값 갱신 시 일부 튜플만 갱신되어 모순 발생  

<br>  

## 정규화 과정  

### 제 1 정규화  

- 테이블의 컬럼이 원자값(Atomic Value, 하나의 값)을 갖도록 테이블을 분해하는 것입니다.  

> 정규화 되기 전의 테이블  

- tag 열의 값이 두 개씩 들어있습니다.  
- tag 열의 값을 기준으로 데이터를 찾거나 정렬 등의 작업을 할 때 의도하지 않은 데이터가 나올 수 있습니다.  

![Normalization_1NF_1](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_1NF_1.png?raw=true)  


```sql
-- tag 열의 값이 두 개 있기 때문에 'free' 와 일치하는 값을 찾을 수 없음
SELECT * FROM topic WHERE tag = 'free';

-- tag 열의 값을 기준으로 정렬이 되지 않음
SELECT * FROM topic ORDER BY tag;
```  

<br>  

> 1 정규형(First Normal Form)을 만족하는 첫 번째 방법  

- tag 열의 값을 하나씩만 삽입하여 테이블을 생성하였기 때문에 1 정규형을 만족하지만, 빨간 바탕으로 표시된 것과 같이 데이터의 중복이 발생합니다.  

![Normalization_1NF_2](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_1NF_2.png?raw=true)  

<br>  

> 1 정규형(First Normal Form)을 만족하는 두 번째 방법  

- tag 열을 tag1, tag2 와 같이 나누었기 때문에 1 정규형을 만족합니다.  
- tag 가 추가되는 경우 tag3 을 추가로 만들어주어야 하기 때문에 컬럼의 구조가 변경되어야 합니다.  
- tag 의 값이 하나만 존재하는 경우 tag2 의 값은 NULL 이 되기 때문에 데이터의 낭비가 발생합니다.  

![Normalization_1NF_3](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_1NF_3.png?raw=true)  

<br>  

> 1 정규형(First Normal Form)을 만족하는 가장 좋은 방법  

- topic 과 tag 를 나누어서 테이블을 생성합니다.  
- topic 테이블과 tag 테이블은 M:N 관계이기 때문에 중간에서 연결해줄 mapping 테이블을 추가로 생성합니다.  
- topic 테이블의 title 속성과 tag 테이블의 id 속성이 서로 관계가 있기 때문에 mapping 테이블의 속성이 됩니다.  

![Normalization_1NF_4](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_1NF_4.png?raw=true)  

<br>  

> 1 정규형을 만족하는 경우 발생할 수 있는 이상(Anomaly)의 예  

- 삽입 이상: MySQL 의 다른 type이 추가될 때마다 description 에서 author_profile 까지의 데이터가 계속 중복됩니다.  
- 삭제 이상: ORACLE 의 online 타입을 삭제하게 되면 ORACLE의 description 에서 author_profile 까지의 데이터가 모두 사라집니다.  
- 갱신 이상: MySQL 의 description 을 수정할 경우 title이 MySQL인 모든 행을 찾아서 수정해야 합니다.  

<br>  

### 제 2 정규화  

- 제 1 정규화를 진행한 테이블에 대해 완전 함수 종속을 만족하도록 테이블을 분해하는 것입니다.  
- 완전 함수 종속이라는 것은 기본키의 부분집합이 결정자가 되어서는 안된다는 것을 의미합니다.  
- 어떤 컬럼 값은 다른 Attribute 값을 고유하게 결정지을 수 있는데 이런 Attribute를 결정자라고 합니다.  

> 1 정규화 직후의 테이블  

- topic 테이블에서 description 에서 author_profile 까지의 데이터가 중복이 됩니다.  
- description 에서 author_profile 까지의 데이터는 title 에만 의존하고 있고 type 과는 상관이 없습니다.  
- description 에서 author_profile 까지의 열은 title 열에 부분적으로 종속되어 있습니다.  
- price 는 title 과 type 에 완전 종속되어 있습니다.  

![Normalization_2NF_1](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_2NF_1.png?raw=true)  

<br>  

> 2 정규형(Second Normal Form)을 만족하는 테이블  

- title 에만 의존하는 description 에서 author_profile 까지의 데이터만 있는 테이블과 title과 type 에 의존하는 price 데이터가 있는 테이블로 분리합니다.  
- 3 정규화 설명을 위해 MariaDB 행을 추가했습니다.  

![Normalization_2NF_2](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_2NF_2_edit.png?raw=true)  

<br>  

> 2 정규형을 만족하는 경우 발생할 수 있는 이상(Anomaly)의 예  

- 삽입 이상: author_id 는 title 에 종속되고 있으며, author_name 과 author_profile 은 author_id 에 종속되기 때문에 title 에 JAVA 가 추가되고 author_id 가 1 인 경우 author_name 과 author_profile 은 중복이 발생합니다.  
- 삭제 이상: MariaDB 행을 삭제하면 author_id 가 2 인 사람의 author_name 과 author_profile 데이터까지 사라집니다.  
- 갱신 이상: author_profile 이 변경되는 경우 해당하는 모든 행을 찾아서 수정해야 합니다.    

<br>  

### 제 3 정규화  

- 제 2 정규화를 진행한 테이블에 대해 이행적 종속을 없애도록 테이블을 분해하는 것입니다.  
- 이행적 종속이라는 것은 A → B, B → C가 성립할 때 A → C 가 성립되는 것을 의미합니다.  

> 2 정규화 직후의 테이블  

- author_name 과 author_profile 은 author_id 에 종속이 되고, author_id 는 title 에 종속이 됩니다.  
- title 에 데이터가 추가될 때마다 author_name 과 author_profile 의 중복이 발생합니다.  

![Normalization_3NF_1](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_3NF_1.png?raw=true)  

<br>  

> 3 정규형(Third Normal Form)을 만족하는 테이블  

- author_name 과 author_profile 은 author_id 에만 종속되기 때문에 해당 열을 따로 분리해서 테이블을 생성합니다.  

![Normalization_3NF_2](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/Normalization_3NF_2.png?raw=true)






<br><br><br>

# <strong>Reference</strong>  

- [정규화(Normalization) 쉽게 이해하기](https://mangkyu.tistory.com/110){:target="_blank"}  
- [데이터베이스 정규화](https://itwiki.kr/w/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%EC%A0%95%EA%B7%9C%ED%99%94){:target="_blank"}  
- [정규형(1NF, 2NF, 3NF, BCNF)](https://rebro.kr/160){:target="_blank"}  
- [관계형 데이터 모델링 - 6.2. 제1 정규화](https://youtu.be/FYDHJbIwm5Y){:target="_blank"}  
- [관계형 데이터 모델링 - 6.3. 제2 정규화](https://youtu.be/7meeyknh7yE){:target="_blank"}  
- [관계형 데이터 모델링 - 6.4. 제3 정규화](https://youtu.be/aS9FoCNlt3o){:target="_blank"}  