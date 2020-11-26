---
layout: page
title: 'springframework'
published: true
background: /img/posts/01.jpg
---


#### Framework
- 프로그램 기본 구조(뼈대)
- 원하는 기능 구현에만 집중하여 빠르게 개발 할 수 있도록 기본적으로 필요한 기능을 갖추고 있는 것으로 위에서 설명한 라이브러리가 포함되어 있다.

#### 프레임워크가 가져야할 특징
- 개발자들이 따라야할 가이드라인을 가진다.
- 개발할 수 있는 범위가 정해져 있다.
- 개발자를 위한 다양한 도구들이 지원된다.

#### 프레임워크의 장/단점

장점 : 개발 시간을 줄일 수 있고 오류로부터 자유로울 수 있다.   
단점 : 프레임워크에 너무 의존하면 개발 능력이 떨어져서 프레임워크 없이 개발하는 것이 불가능해진다.

#### Spring Framework(스프링 프레임워크)
- 자바(JAVA) 플랫폼을 위한 오픈소스(Open Source) 애플리케이션 프레임워크(Framework)
- 자바 엔터프라이즈 개발을 편하게 해주는 오픈소스 경량급 애플리케이션 프레임워크
- 자바개발을 위한 프레임워크로 종속 객체를 생성해주고, 조립해주는 도구
- 자바로 된 프레임워크로 자바SE로 된 자바 객체(POJO)를 자바EE에 의존적이지 않게 연결해주는 역할

#### 스프링 특징 간단히
- 크기와 부하의 측면에서 경량
- 제어 역행(IoC)이라는 기술을 통해 애플리케이션의 느슨한 결합을 도모
- 관점 지향 프로그래밍(AOP)을 위한 풍부한 자원
- 애플리케이션 객체의 생명주기와 설정을 포함하고 관리한다는 점에서 일종의 컨테이너(Container)라고 할 수 있음.
- 간단한 컴포넌트로 복잡한 애플리케이션을 구성하고 설정할 수 있음.

#### 스프링 특징 자세히
**경량 컨테이너로서 자바 객체를 직접 관리**
- 각각의 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있다.

**스프링은 POJO(Plain Old Java Object) 방식의 프레임워크.**
- 일반적인 J2EE 프레임워크에 비해 구현을 위해 특정한 인터페이스를 구현하거나 상속을 받을 필요가 없어 기존에 존재하는 라이브러리 등을 지원하기에 용이하고 객체가 가볍다.

**스프링은 제어의 역행(IoC : Inversion of Control)을 지원**
- 컨트롤의 제어권이 사용자가 아니라 프레임워크에 있어서 필요에 따라 스프링에서 사용자의 코드를 호출한다.

**스프링은 의존성 주입(DI : Dependency Injection)을 지원**
- 각각의 계층이나 서비스들 간에 의존성이 존재할 경우 프레임워크가 서로 연결시켜준다.

**스프링은 관점 지향 프로그래밍(AOP : Aspect-Oriented Programming)을 지원**
- 따라서 트랜잭션이나 로깅, 보안과 같이 여러 모듈에서 공통적으로 사용하는 기능의 경우 해당 기능을 분리하여 관리할 수 있다.

**스프링은 영속성과 관련된 다양한 서비스를 지원**
- MyBatis나 Hibernate등 이미 완성도가 높은 데이터베이스 처리 라이브러리와 연결할 수 있는 인터페이스를 제공한다.

**스프링은 확장성이 높음**
- 스프링 프레임워크에 통합하기 위해 간단하게 기존 라이브러리를 감싸는 정도로 스프링에서 사용이 가능하기 때문에 수많은 라이브러리가 이미 스프링에서 지원되고 있고 스프링에서 사용되는 라이브러리를 별도로 분리하기도 용이하다.

#### Spring MVC 구조의 처리과정
1. DispatcherServlet : 어플리케이션으로 들어오는 모든 Request를 받는 관문이다. Request를 실제로 처리할 Controller에게 전달하고 그 결과값을 받아서 View에게 전달하여 적절한 응답을 생성할 수 있도록 흐름을 제어한다.

2. HandlerMapping : Request URL 각각 어떤 Controller가 실제로 처리할 것인지 찾아주는 역할

3. Controller : Request를 직접 처리한 후 그 결과를 다시 DispatcherServlet에게 돌려준다.

4. ModelAndView : Controller가 처리한 결과와 그 결과를 보여줄 View에 관한 정보를 담고있는 객체이다.

5. ViewResolver : View관련 정보를 갖고 실제 View를 찾아주는 역할을 한다.

6. View : Controller가 처리한 결과값을 보여줄 View를 생성한다.

#####기본적인 5가지 어노테이션   
 **@Controller**   
 - 특정 클래스를 Controller로 등록하는 어노테이션
 - dispacter-servlet.xml에서 <bean>태그로 정의한 것과 동일한 효과를 나타냄
 - DefaultAnnotationHandlerMapping을 통해 컨트롤러로 등록되어 사용됨

**@RequestMapping**   
 - 컨트롤러로 등록된 클래스내에 특정 메서드를 요청되는 URL과 매칭시키는 어노테이션

**@Autowired**   
 - Spring에서 자동으로 Dependency Injection을 하기 위한 어노테이션

**@Service**   
 - @Service로 정의한 클래스는 비지니스로직 처리 Service로 등록이 됨(Impl에서 사용 @Service("boardDao"))
 
**@Repository**   
 - Dao로 등록

#### FrontController 패턴
 최초 앞단에서 request 요청을 받아서 필요한 클래스에 넘겨준다. 왜? web.xml에 다 정의하기가 너무 힘듬.   
 이때 새로운 요청이 생기기 때문에 request와 response가 새롭게 new될 수 있다. 그래서 아래의 RequestDispatcher가 필요하다.   

#### RequestDispatcher
 필요한 클래스 요청이 도달했을 때 FrontController에 도착한 request와 response를 그대로 유지시켜준다.   

#### DispatcherServlet (주소분배, 컴포넌트 스캔)
 FrontController 패턴을 직접짜거나 RequestDispatcher를 직접구현할 필요가 없다. 왜냐하면 스프링에는 DispatcherServlet이 있기 때문이다. DispatcherServlet은 FrontController 패턴 + RequestDispatcher이다.   

 DispatcherServlet이 자동생성되어 질 때 수 많은 객체가 생성(IoC)된다. 보통 필터들이다. 해당 필터들은 내가 직접 등록할 수 도 있고 기본적으로 필요한 필터들은 자동 등록 되어진다.

MyBatis   
- 객체, 데이터베이스, 매퍼 자체를 독립적으로 작성하고 DTO에 해당하는 부분과 SQL실행결과를 SQL문등에 매핑해서 사용할 수 있도록 지원
- 스프링이나 JDBC를 통해 작업하던 dao에 관련된 작업은 모두 sql문이 자바 소스상에 위치했었으나 이제 sql문은 설정파일로 관리한다.
- 설정파일로 분리되면 변경되거나 했을때 설정파일만 건드리면 되므로 유지보수에 좋다. 또한, 매개변수나 리턴타입으로 매핑되는 모든 DTO에 관련된 부분도 모두 설정파일에서 작업한다



<a class="btn btn-primary float-left" href="{{"/aa" | relative_url }}">이전</a>
