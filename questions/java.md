---
layout: page
title: 'JAVA'
published: true
background: /img/java.jpg
---
#### Java
java는 네트위크상에서 쓸 수 있도록 미국의 Sun마이크로시스템이 개발한 개체지향 프로그래밍 언어
- JVM만 설치하면 컴퓨터의 운영체제에 상관없이 작동한한**(운영체제에 독립)**
- 기본 자료형을 제외한 모든 요소들을 객체로 표현
- 객체 지향 개념의 특징인 캡슐화, 상속, 다형성이 잘 적용된 언어
- Garbage Collector를 통한 메모리 관리기능
- 멀티쓰레드(Multi-thread)를 지원한다.

#### OOP(객체지향 프로그래밍)
Object-Oriented Programming의 약어로써 객체지향 프로그래밍을 의미   
데이터를 객체로 취급하여 프로그램에 반영한 것이며, 순차적으로 프로그램이 동작하는 기존의 것들과는 다르게 객체와 객체의 상호작용을 통해 프로그램이 동작하는 것을 말한다.
- 객체지향 프로그래밍은 코드 재사용성이 높다.
- 코드의 변경이 용이
- 직관적인 코드 분석
- 개발속도 향상
- 상속을 통한 장점 극대화

#### Object
Object(객체)는 OOP에서 데이터(변수)와 그 데이터에 관련되는 동작(함수). 즉 절차, 방법, 기능을 모두 포함한 개념

#### Overloading vs Overriding
Overloading(오버로딩)
- 같은 이름의 메소드를 여러 개 정의하는 것.
- 매개변수의 타입이 다르거나 개수가 달라야 한다.
- Return type과 접근 제어자는 영향을 주지 않음
Overriding(오버라이딩)
- 상속에서 나온 개념
- 상위 클래스(부모 클래스)의 메소드를 하위 클래스(자식 클래스)에서 재정의

#### JDBC
- Java Data Base Connection의 약자로 JAVA 언어를 통해 데이터베이스에 접근할 수 있는 프로그래밍

#### Interface, Abstract
Interface
- 일종의 추상 클래스
- 오직 추상메서드와 상수만을 멤버로 갖는다.
- implements 키워드를 사용
- 상속의 관계가 없는 클래스간 서로 공동되는 로직을 구현하여 쓸 수 있도록 한다.
- Extends는 하나의 클래스만 상속 가능하나 Interface는 다중 상속이 가능하다.
Abstract
- 추상메소드를 하나 이상 가진 클래스
- 자신의 생성자로 객체 생성 불가능
- 하위 클래스를 참조하여 상위 클래스의 객체를 생성
- 하위 클래스를 제어하기 위해 사용
##### Interface vs Abstract   
공통점
- New 연산자로 인스턴스 생성 불가능
- 프로토타입만 있는 메서드를 갖는다.
- 사용하기 위해서는 하위클래스에서 확장/구현해야 한다.
차이점
- 사용하는 키워드가 다르다.
- Abstract는 일반 메서드를 사용할 수 있지만, Interface는 메서드 선언만 가능하다.

#### Call by Reference, Call by Value
Call by References
- 매개변수의 원래 주소에 값을 저장하는 방식, 클래스 객체를 인수로 전달한 경우
Call by Value
- 인수로 기본 데이터형을 사용. 주어진 값을 복사하여 처리하는 방식. 메서드 내의 처리 결과는 메서드 밖의 변수에 영향을 미치지 않늗다.

#### Static
- 클래스가 로딩될 때, 메모리 공간을 할당하는데 처음 설정된 메모리 공간이 변하지 않음을 의미
- 객체를 아무리 많이 만들어도 해당 변수는 하나만 존재(객체와 무관한 키워드)

#### Garbage Collection
- 시스템에서 더 이상 사용하지 않는 동적 할당된 메모리 블록을 찾아 자동으로 다시 사용 가능한 자원으로 회수 하는 것. 시스템에서 가비지 컬렉션을 수행하는 부분을 가비지 컬렉터라 부른다. 고로 자바에서는 메모리 문제를 신경쓰지 않아도 된다.

#### Primitive type과 Reference type
Primitive type
- 변수에 값 자체를 저장(정수형, 실수형, 문자형, 논리형) – Wrapper Class를 통해 객체로 변환 가능
Reference type
- 메모리상에 객체가 있는 위치를 저장
종류
- Class, Interface, Array 등

#### Wrapper Class
- Primitive type으로 표현할 수 있는 간단한 데이터를 객체로 만들어야 할 경우가 있는데 그러한 기능을 지원

#### Thread
Thraed(쓰레드)
- 프로세스내에서 동시에 실행되는 독립적인 실행 단위를 말함. 장점으로는 자원을 많이 사용하지 않고 구현이 쉬우며 범용성이 높다.
Process(프로세스)
- 운영체제에서 실행중인 하나의 프로그램(하나 이상의 쓰레드를 포함한다.)
Thread 장점
- 빠른 프로세스 생성
- 적은 메모리 사용
- 쉬운 정보 공유
Thread 단점
- 교착상태에 빠질 수 있다.
*교착상태 : 다중 프로그래밍 체제에서 하나 또는 그 이상의 프로세스가 수행할 수 없는 어떤 특정 시간을 기다리고 있는 상태
Thread와 Process 차이
- 여러 분야에서 ‘과정’ 또는 ‘처리’라는 뜻으로 사용되는 용어로 컴퓨터 분야에서는 ‘실행중인 프로그램’이라는 뜻으로 쓰인다.   
- 이 프로세스 내에서 실행되는 각각의 일을 스레드라고 한다. 프로세스 내에서 실행되는 세부 작업 단위로 여러 개의 스레드가 하나의 프로세스를 이루게 되는 것이다.

#### 접근 제한자(public > protected > default > private)
Public
- 접근 제한이 없다.(같은 프로젝트 내에 어디서든 사용 가능)
Protected
- 같은 패키지 내, 다른 패키지에서 상속 받아 자손 클래스에서 접근 가능
Default
- 같은 패키지 내에서만 접근 가능
Private
- 같은 클래스 내에서만 접근 가능

#### Stack, Queue
Stack
- LIFO(Last In First Out)의 후입선출 구조
- push(); 를 이용한 데이터 입력, pop();을 이용한 데이터 출력
- 예) 시스템 스택 : 함수의 호출과 복귀 순서는 스택의 구조를 응용하여 관리.
- 역순 문자열 만들기, 수식의 괄호 검사, 수식의 후위 표기법 변환
Queue
- FIFO(First In First Out)의 선입선출 구조
- enQueue();를 이용한 데이터 입력, deQueue();를 이용한 데이터 출력
- 예) 우선순위가 같은 작업 예약(인쇄 대기열), 선입 선출이 필요한 대기열(티켓 카운터)

#### Singleton Design Pattern(싱글톤 디자인 패턴, 싱글톤 패턴)
- 클래스 인스턴스가 하나만 만들어지도록 하고, 그 인스턴스에 대한 전역 접근을 제공한다.

#### String과 StringBuffer의 차이
자바의 기본 데이터 타입인 int, float, char 등과 다르게 String은 데이터 타입이 아닌 클래스 객체입니다. 또한 String은 불변의 객체입니다. 한번 String name =”길동”; 라고 선언하게 되면 먼저 String 객체타입인 name이라는 인스턴스를 만들고 메모리에 “길동”을 올려버립니다. 그리고 name이 “길동”을 참조하는 레퍼런스가 되는 것입니다.   

중요한점은 이제 이 name에 새로운 내용을 추가하겠습니다. name += “홍”; 와 같은 소스를 적용하게 되면 name인스턴스가 가리키는 값은 “길동홍”가 됩니다. 우리는 이런식으로 흔히 코딩을 했을 텐데 아까 위에서 String이 불변 객체라고 설명을 했듯이 한번 선언된 내용에 추가적으로 바뀌지 않습니다. String은 final char배열 형태이기 때문에 내용의 추가와 삭제가 되지 않거든요. 그럼 도대체 어떻게 name변수의 값이 바뀌는 건지 답은 내부에 있습니다.    

name = name + “홍”; 구문이 실행될 때 실제로는 스트링 버퍼를 새로 생성해서 name이 가리키는 “길동”을 만들어주고 스트링 버퍼의 append 함수를 이용하여 “홍” 를 붙여줍니다. 그렇게 완성된 스트링 버퍼값을 메모리에 올리고 name은 다시 이 값을 참조하게 됩니다. 스트링 버퍼는 char타입의 배열로 되어 있어서 한글자 한글자를 append할 수 있다는 것을 아셔야합니다. 그럼 그와중에 생겨난 메모리 안의 “길동” 이라는 값과 “홍”라는 값은 가비지 컬렉터가 가지고 있다가 필요없어서 버립니다. 그 짧은 순간에 이런 일처리가 진행이 되어서 스트링 버퍼를 사용하는 것이 스트링 객체를 사용하는 것보다 빠르다는게 제 생각입니다.

#### 자바의 메모리 영역
- 메서드 영역 : static 변수, 전역변수, 코드에서 사용되는 Class 정보 등이 올라간다. 코드에서 사용되는 class들을 로더로 읽어 클래스별로 런타임 필드데이터, 메서드 데이터 등을 분류해 저장한다.
- 스택(Stack) : 지역변수, 함수(메서드) 등이 할당되는 LIFO(Last In First Out) 방식의 메모리
- 힙(Heap) : new 연산자를 통한 동적 할당된 객체들이 저장되며, Garbage 컬렉션에 의해 메모리가 관리되어 진다.

#### DAO 와 DTO
DAO
- Data Access Object의 약자로 간단히 데이터베이스의 데이터에 접근을 위한 객체이다. 데이터베이스에 접근을 하기위한 로직과 비즈니스 로직을 분리하기 위해서 사용한다. DB를 사용해 데이터를 조회하거나 조작하는 기능을 전담하도록 만든 오브젝트를 말한다.
DTO
- Data Transfer Object의 약자로 VO(Value Object)로 바꾸어 말할 수 있는데 계층간 데이터 교환을 위한 JavaBean을 말합니다. 여기서 말하는 계층이란 Controller, View, Business Layer, Persistent Layer를 말하며 각 계층간 데이터 교환을 위한 객체를 DTO 또는 VO라고 부릅니다. 그런데 VO는 동일한 개념이지만 read only 속성을 가집니다.

#### 변수 명명법
- 헝가리언 표기법 : 자료형을 식별자에 같이 포함
ex) inum; int int_num; 인터페이스명.   
- 파스칼 표기법 : 식별자가 한 단어나 혹은 여러 단어로 조합(언더바X), 각단어의 첫문자만 대문자로
ex) KorScore   
- 캐멀 표기법 : 모든 단어를 공백없이 조합(언더바X) – 첫단어의 첫문자는 소문자로
ex) korScore   
- 스네이크 표기법 : ex)eng_score





<a class="btn btn-primary float-left" href="{{"/aa" | relative_url }}">이전</a>