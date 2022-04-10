---
published: true
layout: single
title: "[Database] ER 다이어그램"
subtitle: 
categories: [database]
tag: [database, erd]
toc: true
toc_sticky: true
---  

# [Database] ER 다이어그램  

## ERD 란?  

- `Entity Relationship Diagram` 을 줄여 부르며, E-R 다이어그램이라고 합니다. 영어 뜻 그대로 '개체(Entity) 들의 관계(Relationship) 를 나타낸 도표(Diagram)' 입니다.  

<br>

## ERD 표기법  

> Entity  

- Entity는 정의 가능한 사물 또는 개념을 의미합니다.  
- 사람이나 객체 혹은 개념이나 이벤트 등을 Entity로 둘 수 있습니다.  
- 데이터베이스를 설계할 때, `테이블`이 Entity로 정의될 수 있습니다.  

<br>

> Entity Attribute  

- 각각의 Entity에는 속성을 포함하고 있습니다.  
- Attribute는 개체가 갖고있는 속성입니다.  
- 예를 들어 `사람`이라면, `나이`, `이름`, `생년월일` 등 속성들을 포함할 수 있습니다.  

<br>

> Entity 분류  

| 구분 | 내용 |
| -- | -- |  
| 유형 엔티티 | 물리적인 형태가 있음(예: 고객, 상품, 학생 등) |  
| 무형 엔티티 | 물리적인 형태가 없고 개념적으로만 존재함(예: 인터넷 장바구니, 부서 조직 등) |  
| 문서 엔티티 | 업무 절차상에서 사용되는 문서나 장부, 전표에 대한 엔티티(예: 거래명세서, 주문서 등) |  
| 이력 엔티티 | 업무상 반복적으로 이루어지는 행위나 사건의 내용을 일자별, 시간별로 저장하기 위한 엔티티(예: 입고 이력, 출고 이력, 구매 이력 등) |  
| 코드 엔티티 | 무형 엔티티의 일종으로 각종 코드를 관리하기 위한 엔티티(예: 국가코드, 각종 분류 코드) |  

<br>

> 표기법  

1. 하나의 A(부모)는 하나의 B(자식)로 구성되어 있음. B(자식)는 반드시 하나가 있어야 함.  

![erd1](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd1.png?raw=true)  

2. 하나의 A(부모)는 하나 이상의 B(자식)로 구성되어 있음.  

![erd2](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd2.png?raw=true)  

3. 하나의 A(부모)는 하나 이하의 B(자식)로 구성되어 있음. B(자식)는 없을수도 있고, 하나가 있을수도 있음.  

![erd3](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd3.png?raw=true)  

4. 하나의 A(부모)는 0 또는 하나 이상의 B(자식)로 구성되어 있음. B(자식)는 없을수도 있고, 여러개가 있을수도 있음.  

![erd4](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd4.png?raw=true)

5. 실선은 A(부모)의 기본키를 B(자식)이 가지고 있으며, 이를 기본키로 사용함.  

![erd5](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd5.png?raw=true)  

6. 점선은 A(부모)의 기본키를 B(자식)이 가지고 있지만, 이를 기본키로 사용하지 않음.

![erd6](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd6.png?raw=true)  

<br>  

## 두 개체의 관계  

> Cardinality  

- Cardinality는 한 개체에서 발생할 수 있는 발생 횟수를 정의하며, 다른 개체에서 발생할 수 있는 발생 횟수와 연관됩니다. 한마디로 개체들간의 수적 관계를 명시하는 표현입니다.  

<br>

> One-to-One Cardinality (1대1 관계)  

- 학생 한명이 하나의 신체 정보를 갖기 때문에 학생과 신체정보는 1:1로 매칭됩니다.  

![one_to_one_cardinality](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/one_to_one_cardinality.png?raw=true)  

> One-to-Many Cardinality (1대N 관계)  

- 한명의 학생은 여러 개의 취미를 가질 수 있기 때문에 학생과 취미는 1:N으로 매칭됩니다.  

![one_to_many_cardinality](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/one_to_many_cardinality.png?raw=true)  

> Many_to_Many Cardinality (M대N 관계)  

- 예를 들어 TV라는 제품은 LG, 삼성, 애플과 같이 여러 제조업체가 있습니다.  
- 마찬가지로 각각의 제조업체에서는 TV 뿐만 아니라 냉장고나 세탁기 등 여러 제품을 생산합니다.  
- 따라서 제품과 제조업체는 M:N으로 매칭됩니다.  

![many_to_many_cardinality_1](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/many_to_many_cardinality_1.png?raw=true)  

- 이처럼 두 엔티티가 M:N 관계에 있는 경우에는 두 엔티티가 관련이 있다는 정보를 두 개의 엔티티만으로는 표현을 할 수 없기때문에 두 엔티티의 관련성을 표현하기 위해 중간에 또 다른 엔티티가 필요합니다.  
- 각각의 엔티티는 중간에 있는 엔티티와 1:N으로 매칭됩니다.  

![many_to_many_cardinality_2](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/many_to_many_cardinality_2.png?raw=true)  

<br>  

## 예제  

> 업무파악  

1. 게시판에 `게시글`을 작성하는 `작성자`가 있으며 하나의 `게시글`은 한 명 이상의 `작성자`가 있습니다.  
2. 한 명의 `작성자`는 여러 개의 `게시글`을 작성하거나 작성하지 않을 수 있습니다.  
3. 하나의 `게시글`에는 `댓글`이 여러 개가 있거나 없을 수 있습니다.  
4. 한 명의 `작성자`는 여러 개의 `댓글`을 작성하거나 작성하지 않을 수 있습니다.  
5. 한 명의 `작성자`는 `휴면자`일 수도 있고 아닐수도 있습니다.  

<br>

> 개념적 데이터 모델링  

- 개념적 데이터 모델링은, 내가 하고자 하는 일의 데이터 간의 관계를 구상하는 단계입니다.  
- 주요 활동으로는 핵심 엔티티와 그들간의 관계를 발견하고, 그것을 표현하기 위해서 ER 다이어그램을 생성하는 것입니다.  
- 그리는 방법(각 도형의 의미)  

![erd7](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd7.png?raw=true)  

<br>

1. `작성자` 엔티티의 속성 확인  

![author_diagram](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/author_diagram.png?raw=true)   

<br>  

2. `게시글` 엔티티의 속성 확인  

![topic_diagram](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/topic_diagram.png?raw=true)  

<br>  

3. `댓글` 엔티티의 속성 확인  

![comment_diagram](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/comment_diagram.png?raw=true)   

<br>  

4. `휴면자` 엔티티의 속성 확인  

![dormant_diagram](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/dormant_diagram.png?raw=true)  

<br>  

5. 전체 엔티티의 관계 확인  

![relation_diagram](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/relation_diagram.png?raw=true)  

<br>  

> 논리적 모델링  

- 위에서 구현한 개념점 ER 다이어그램을 테이블 형태로 재구성 합니다.  
- 이 단계에서는 각 속성의 데이터타입을 명시해주고 각 데이터간의 관계를 정밀하게 맺어주며 테이블의 키를 지정해줍니다.  
- 작성자(author)와 게시글(topic)의 관계는 M:N 이기 때문에 둘 사이를 연결할 수 있는 연결테이블(mapping table)을 추가해줍니다.  

![erd_table](https://github.com/morisYu/morisyu.github.io/blob/master/assets/images/database/erd_table.png?raw=true)  




<br><br><br>

# <strong>Reference</strong>  

- [ER 다이어그램/ERD 기호 및 표기법](https://mjn5027.tistory.com/43){:target="_blank"}  
- [데이터 모델링 개념 및 ERD 다이어그램 그리는법](https://inpa.tistory.com/entry/DB-%F0%9F%93%9A-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%AA%A8%EB%8D%B8%EB%A7%81-1N-%EA%B4%80%EA%B3%84-%F0%9F%93%88-ERD-%EB%8B%A4%EC%9D%B4%EC%96%B4%EA%B7%B8%EB%9E%A8){:target="_blank"}  
- [N:M 관계의 처리](https://youtu.be/PN121bbdgSM){:target="_blank"}  