## RESTful
* 테크톡 영상 요약본 입니다
* [영상링크](https://www.youtube.com/watch?v=xY7cpMuWh4w)

## REST란?
* **RE**presentational (표현)
* **S**tate (상태)
* **T**ransfer (전달)
* 자원의 표현을 가지고 상태를 전달하는 것
  - 자원의 표현 = HTTP URI
  - 상태 전달 = HTTP Method
 
 ## RESTful이란?
 - REST란 아키텍쳐 스타일의 제약조건을 모두 만족하는 시스템
 - "RESTful하다"
 - RESTful의 제약 조건에 따라서 서버가 클라이언트의 요청을 처리하고 응답하는 방법을 제약 함으로써 개발자는 확장성, 단순성, 수정 가능성,
 가시성, 이식성 및 신뢰성과 같은 비 기능적인 특성들을 얻는다.

## REST 아키텍쳐의 제약조건
* **Client - Server**
  - Client가 Server에게 Request를 보내고 Server가 Client에게 Response를 보내는 구조
  - **서버**는 데이터 저장소로부터 필요한 자원을 어떻게 하면 잘 관리(조회, 추가, 삭제, 변경) 할 수 있는지에 대해서만 집중하면된다.
  - **클라이언트**에서는 사용자 인증이나 컨텍스트(ex. 세션, 로그인 정보) 등을 직접 관리하는 역할
* **Stateless**
  - 클라이언트와 서버의 통신에는 상태가 없어야한다
  - 모든 요청은 필요한 모든 정보를 담고 있어야 한다
* **Layered System**
  - 계층으로 구성이 가능해야한다
  - 클라이언트 입장에서는 서버만호출함
  - 서버는 다중 계층으로 구성될 수 있음
  - 클라이언트는 단순히 REST 서버에 요청을 보낼 뿐, 직접 찾아 서버에 요청을 한 것인지 아니면 중간 중개자에게 요청을 한 것인지 알 수 없다.
  단순히 원하는 결과를 받았는지 여부만이 중요할 뿐이다. 따라서, 서버는 다중 계층으로 구성될 수 있다. 보안, 로드 밸런싱, 암호화 계층을 추가하여 구조성의 유연성을 둘 수 있고 PROXY, 게이트 웨이와 같은
  네트워크 기반의 중간 매체를 사용할 수 있다.
  
  * **Cache**
  - 일반적인 서비스에서 60 - 80% 가량의 트랜잭션이 Select와 같은 조회성 트랜잭션
  - GET은 얼마든지 호출핻 매번 같은 결과를 만들어내므로 캐싱이 가능하다
  
* **Code-On-Demand(Option)**
  - 서버는 클라이언트가 실행시킬 수 있는 로직 (ex. Javascript와 같은 클라이언트 측 스크립트)을 전송하여 클라이언트의 기능을 일시적으로 확장하거나 사용자 정의를 할 수 있다.
* **Uniform Interface**
  - REST 인터페이스의 원칙에 대한 가이드:
  - Resource identification in requests
    1. 자원은 유일하게 식별가능해야 하낟
    2. Resource가 하나 이상의 유일한 특정 주소인 URI로 식졀되는지
    3. 아직 POST Method로만 Requet를 보내기 때문에 URI나 RequestBody로 어떤 동작을 할지 알려줘야한다
  - Resource manipulation through representations
    1. Representation의 형태는 content-type로 결정된다
    2. text/html, application/xml, appliction/json 등
  - Self-descriptive messages
    1. 메시지는 스스로를 설명해야한다
    2. 메시지는 요청 작업을 안료할 수 있도록, 응답을 이해할 수 있도록 충분한 정보들을 HTTP Method, Status Code, Header 등을 할용하여 전달 해야한다
    
  - Hypermedia as the engin of application state
    1. 하이퍼링크를 통해서 어플리케이션의 상태가 전이되어야한다
    2. HTTP Response에 다음 Action이나 관계되는 리소스에 대한 HTTP Link를 함께 리턴
    3. 요청 URI가 변경되더라도 클라이언트에서 동적으로 생성된 URI를 사용함으로써 클라이언트가 URI 수정에 따른 코드를 변경하지 않아도 된다
    

## Richardson Maturity Model (리처드슨 성숙도 모델)
*![image](https://media-exp1.licdn.com/dms/image/C5112AQEbd9Ob63-iHA/article-inline_image-shrink_1500_2232/0/1541014242876?e=1628726400&v=beta&t=tY3y2uxxp9SZPvZn0ejO1vJXly18Ib1K-DmMiqWLvSI)
* Level 0 (운격 프로시저 호출)
  - HTTP를 RPC를 기반으롷나 원격 통신을 위한 터널링 메커니즘으로 사용됨
* Level 1 (REST 리소스)
  - Resources
    - 리소스를 도입한다
    - 모든 요청을 단일 서비스 엔드포인트로 보낸느 것이 아니라 개발 리소스와 통신한다
  - Identification of Resources
    - 자원은 유일하게 실별가능해야 한다
    - Resouce가 하나 이상의 유일한 특정 주소만 URI로 식별되는지
    - 아직 POST Method로만 Request를 보내기 때문에 URI 또는 RequestBody로 어떤 동작을 할지 알려줘야 한다
* Level 2 (추가 HTTP 메소드)
  - GET, PUT, DELETE등 다른 메소드를 사용할 수 있다.
  - Level 0, 1 보다 HTTP의 사용법에 가능한 가깝게 사용한다
* Level 3 (HATEOAS)
  - HATEOAS(Hypermedia As The English Of Appication State) 도입
  - 클라이언트가 전적으로 서버와 동적인 상호작용이 가능함
  - 클라이언트가 서버로부터 어떠한 요청을 할 때, 요청에 필요한 URI를 응답에 포함시켜 변환하는 것


## 정리
1. REST는 소프트웨어 아키텍쳐의 한 형식이다
2. REST 아키텍쳐는 여러개의 제약 조건을 가지고 있다
3. RESTful은 위의 제약 조건들을 모두 만족시켜야 한다
4. HTTP Method, Status Code를 용도에 맞게 써야하고, HTTP heder과 link를 신경쓰면 RESTful한 서비스를 설계할 수 있다



