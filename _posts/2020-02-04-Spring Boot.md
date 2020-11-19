---
layout: post
title: 'Spring & Tomcat'
subtitle: '동작원리'
date: '2020-11-01 23:45:13 -0400'
background: /img/posts/05.jpg
published: true
---
#### spring에서 톰캣 동작 원리
<img src="https://user-images.githubusercontent.com/61040284/99372697-e6dfcf00-2903-11eb-9cb0-6851c699fa26.png">
1. web.xml 로딩
2. ContextLoaderListener 호출
3. ContextLoaderListener는 ApplicationContext를 로드하고 root-ApplicationContext가 로드된다.
4. 이때 DB관련 객체가 생성된다.(service, dao, vo)
5. 사용자 요청 (request)
6. DispatcherServlet 동작
7. servlet-context.xml 파일에 의해 읽힘.
8. FrontController 패턴을 이용해 주소 분배
9. 응답(reponse) - html파일을 응답할지 Data를 응답할지 결정해야 하는데 html 파일을 응답하게 되면 ViewResolver가 관여하게 된다.   
하지만 Data를 응답하게 되면 MessageConverter가 작동하게 되는데 메시지를 컨버팅할 때 기본전략은 json이다. 
#### 스프링부트는 내장 톰캣을 가지고 있음.
따로 설치할 필요 없이 바로 실행 가능   

http 통신 대신 소켓 통신을 하는 이유   
- 연결이 끊어지지 않는다. 하지만 그 때문에 연결이 늘어나 부하가 크다.

#### 서블릿 컨테이너
<img src="https://user-images.githubusercontent.com/61040284/99372561-b13ae600-2903-11eb-959c-5802720fda3e.png">
스프링에서는 URL을 통한 접근을 막고 URI를 통한 접근만은 허용한다.   
요청시에는 무조건 자바를 거친다. 즉 제어권을 톰캣에게 위임!   
서블릿이란 간단하게 java 코드로 웹을 할 수 있도록 하는 것.
서블릿 컨테이너는 이러한 서블릿들을 모아놓은 곳이다.

#### web.xml 은?
- ServletContext의 초기파라미터
- Session의 유효시간 설정
- Servlet/JSP에 대한 정의,매핑
    정의 : 자원들의 위치 정보
    매핑 : 식별자를 통해 요청한 자원의 위치가 어디있는지 알려주고 그쪽으로 이동할 수 있게 도와준다.
- Mime Type 매핑
    내가 들고올 데이터가 어떤 타입인지 알려주는 것.
- Welcome File List
    목적지에 대한 정보가 없는 데이터를 한 곳에 모아 Welcome File List에 모아둔다.
- Error Page 처리
- 리스너/필터 설정
- 보안   
**Servlet/JSP 매핑시에 모든 클래스에 매핑을 적용시키기에는 코드가 너무 복잡해지기 때문에 FrontController 패턴을 이용한다.**   

##### FrontController 패턴 이란
최초 앞단에서 request 요청을 받을 때, 특정 주소가 들어오면 FrontController 라는 클래스로 보내라고 web.xml에 설정한다.   
URI 혹은 자바 파일을 요청할 때 바로 자원에 접근하지 못하고 톰캣으로 가고 톰캣으로 가면 request와 response라는 객체를 자동으로 만들어낸다.   
이때 web.xml에 servlet/jsp 매핑이 너무 많이 들어있으면 복잡해지기 때문에, 특정 주소는 FrontController로 보내질 수 있게 세팅을 해준다. 그리고 FrontController에서 한번 더 해당 자원에 접근할 수 있게 ruquest가 발생하고 이에 응답하기위해 response가 발생한다.   
이때 새로운 request와 reponse가 발생하기 때문에 기존의 객체가 새롭게 갱신된다. 그래서 기존의 객체 정보를 덮어쓰는 기법이 필요한데, 이를 위해서 RequestDispatcher를 사용한다.

#### RequestDispatcher
필요한 클래스 요청이 도달했을 때, FrontController에 도착한 request와 response를 그대로 유지시켜준다.    

#### DispatcherServlet
스프링에서는 FrontController 패턴을 직접 짜거나, RequestDispatcher를 지접 구현할 필요가 없다.   
스프링에서는 DispatcherServlet을 제공하는데, 이는 **FrontController + RequestDispatcher** 개념이다. DispatcherServlet이 자동생성되어 질 때, 수많은 객체가 생성된다.    
보통 필터들이며, 해당 필터들은 내가 직접 등록할 수 있고, 기본적으로 필요한 필터들은 자동 등록된다.   
역할은 크게 컴포넌트 스캔, 주소 분배로 나뉜다.
주소 분배를 하기 위해서는 Object가 메모리에 로딩 되어있는 상태여야 한다.   
따라서 컴포넌트 스캔을 하는데 스프링 부트에서는 src 폴더 아래에 있는 자바파일들을 스캔하여 특정 어노테이션을 확인한다.
이렇게 컴포넌트 스캔을 통해 특정 클래스들을 메모리에 로딩하고, 주소 분배를 할 수 있다.   
이때 DispatcherServlet에 접근하기 전에  **contextLoaderListener**를 해야한다.   
DispatcherServlet에 의해 주소가 분배되면서 새로운 스레드가 계속 생성되는데, 이때 DB Connection과 같이 모든 요청이 공통적으로 사용해야하는 일, 모든 스레드가 공통적으로 사용해도 되는 것들은 contextLoaderListeners에 의해 메모리에 로딩된다.
contextLoaderListeners는 root_ApplicationContext라는 파일을 읽는다.   

#### 스프링 컨테이너
DispatcherServlet에 의해 생성되어지는 수 많은 객체들은 ApplicationContext에서 관리된다. 이것을 IoC라고 한다.   
**ApplicationContext**   
IoC란 제어의 역전을 의미한다. 개발자가 직접 new를 통해 객체를 생성하게 된다면 해당 객체를 가르키는 레퍼런스 변수를 관리하기 어렵다. 그래서 스프링이 직접 해당 객체를 관리한다. 이때 우리는 주소를 몰라도 된다. 왜냐하면 필요할 때 DI하면 되기 때문이다.   

DI를 의존성 주입이라고 한다. 필요한 곳에서 ApplicationContext에 접근하여 필요한 객체를 가져올 수 있다. ApplicationContext는 싱글톤으로 관리되기 때문에 어디에서 접근하든 동일한 객체라는 것을 보장해준다.   

ApplicationContext의 종류에는 두가지가 있는데 (root-applicationContext와 servlet-applicationContext) 이다.   

**- servlet-applicationContext**
- ViewResolver, Interceptor, MultipartResolver 객체를 생성하고 웹과 관련된 어노테이션 Controller, RestController를 스캔 한다.(DispatcherServlet에 의해 실행)   
**- root-applicationContext**
- 해당 어노테이션을 제외한 어노테이션 Service, Repository등을 메모리에 로딩하고 DB관련 객체를 생성한다.(ContextLoaderListener)   
<img src="https://user-images.githubusercontent.com/61040284/99372704-e810fc00-2903-11eb-86ab-6716fbf44fca.png">

servlet-applicationContext에서는 root-applicationContext가 로드한 객체를 참조할 수 있지만 그 반대는 불가능하다. 생성 시점이 다르기 때문이다.    
**Bean Factory**
필요한 객체를 Bean Factory에 등록할 수 도 있다. 여기에 등록하면 초기에 메모리에 로드되지 않고 필요할 때 getBean()이라는 메소드를 통하여 호출하여 메모리에 로드할 수 있다. 이것 또한 IoC이다. 그리고 필요할 때 DI하여 사용할 수 있다.    ApplicationContext와 다른 점은 Bean Factory에 로드되는 객체들은 미리 로드되지 않고 필요할 때 호출하여 로드하기 때문에 lazy-loading이 된다는 점이다.   

#### Handler Mapping
GET요청 => http://localhost:8080/post/1
해당 주소 요청이 오면 적절한 컨트롤러의 함수를 찾아서 실행한다.   
