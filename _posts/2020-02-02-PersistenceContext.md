---
layout: post
title: 'JPA'
subtitle: 영속성 컨텍스트
date: '2020-10-03 20:45:13 -0400'
background: /img/posts/05.jpg
published: true
---
### 영속성 컨텍스트(Persistent Context)
  영속성 컨텍스트란 엔티티를 관리하고 영속화시키는 환경을 의미합니다.
##### 좋은 이유
  - 1차 캐시 Map 객체로 저장
    - 엔티티를 식별자 값(@Id 맵핑)으로 구분한다. Key-value로 관리하는데 이때 key 값이  @Id 값이 된다.
  - 식별자 값 필요
    - 영속상태의 엔티티는 반드시 식별자 값이 있어야 한다.
  - 동일성 보장 동일한 객체 반환
    - Collection에서 객체를 빼오듯이 같은 객체를 반환하게 되면 새로운 객체가 나오는 것이 아니라 동일한 객체가 반환된다.
  - 변경 감지 자동 Update
    - 영속성 상태의 객체는 객체의 데이터가 변경이 되면, 자동 update 된다. EntityManager에서 flush가 되고, commit이 됩니다.
  - 트랜잭션으로 인한 쓰기 지연
    - 영속성 컨텍스트는 트랜잭션 범위 안에서 동작한다. 그래서 트랜잭션이 끝나야 Commit이 이루어지고 반영된다.

### Entity Manager와 Entity Manager Factory
  Entity Manager는 엔티티를 조회하거나 등록, 수정, 삭제 시키기 위해 DB에 접근할 수 있는 객체입니다.    
  EntityManagerFactory는 Entity Manager를 생성합니다. 객체 생성 비용이 상당히 크기 때문에 한번만 생성하여 애플리케이션 전체에서 사용합니다.   
### 영속성 컨텍스트 구조
  - 1차 캐시 저장소   
    엔티티를 조회하거나 저장할 경우 해당 엔티티는 1차 캐시에 저장됩니다.   
    1차 캐시에 저장되면 해당 엔티티는 영속 상태가 되며 영속성 컨텍스트가 관리하는 대상이 됩니다.
  - sql 저장소   
    insert, update, delete등.. 여러 쿼리문을 저장했다가 commit시 한번에 처리합니다. DB 접근 회수를 최소화하고 성능상 이점을 얻을 수 있습니다.
