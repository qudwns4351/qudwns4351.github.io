---
layout: post
title: '스프링부트의 트랜잭션'
subtitle: OSIV
date: '2020-10-30 23:45:13 -0400'
background: /img/posts/05.jpg
published: true
---

#### 스프링부트의 트랜잭션
- OSIV 전략
- 세션의 시작은 서블릿이 시작되는 시점 부터~ (세션은 영속성 컨텍스트를 포함)
- 트랜잭션의 시작은 서비스 레이어부터, JDBC 커넥션도 이 시점부터.
- 트랜잭션의 종료는 서비스 계층에서 종료, JDBC 커넥션도 이 시점 부터 종료.
- 세션은 컨트롤러 영역까지 끌고 가기 때문에 영속성이 보장되어 select가 가능해지고 lazy-loading이 가능해진다.
- lazy-loading 사용 이유 : 성능 이슈가 발생할 가능성을 줄여준다.   
사용법 : open-in-view=true 설정.
<img src="https://user-images.githubusercontent.com/61040284/100190366-6fc4bf00-2f31-11eb-9fa5-a70a765ed952.png">

##### 장점
-
#### 기존 방식
-세션과 트랜잭션, jdbc커넥션이 서블릿이 시작되는 시점 부터 실행.
-종료는 Controller에서 응답전에 셋 다 같이 종료.
-eager만 가능 (lazy X) : 참조 객체와 항상 함께 로드되어야 하는 조건을 가진 엔티티에 대해선 LAZY 방식보단 EAGER 방식이 더 좋다.
<img src="https://user-images.githubusercontent.com/61040284/100191928-5c672300-2f34-11eb-91fc-02f698f7189c.png">
