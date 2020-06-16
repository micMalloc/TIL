# REST 의 개념

![img](https://gmlwjd9405.github.io/images/network/rest.png)

</br>

## REST란

- REST의 정의

  - ***"Representational State Transfer"*** 의 약자

    - 자원(Resource)을 이름(자원의 표현 : Representation)으로 구분하여 해당 자원의 상태(State) 정보를 주고 받는 (Transfer) 모든 것을 의미한다.

    - 다시말해, ***자원의 표현*** (Resource Representation) 에 의한 ***상태 정보*** 전달 (State Transfer)

      - 자원의 표현 (Resource Representation)

        - "**자원 (Resource**)" 이란, 어떤 Software가 관리하는 모든 것을 의미한다.

          → 예) 문서, 그림, 데이터, 해당 Software 그 자체 등

        - "**자원의 표현**" 이란, 그 자원을 표현하기 위한 유니크한 ID 혹은 이름

          → 예) DB의 학생 관련 정보가 자원인 경우,  'students' 라는 유니크한 ID로 해당 자원의 표현을 정한다.

      - 상태 정보 전달 (State Transfer)

        - 자원 혹은 데이터가 요청되어지는 시점에서 자원의 상태 정보를 전달한다.

          → 대게, JSON 혹은 XML을 통해 주고 받는다.

  - World Wide Web(WWW) 과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 개발 아키텍처의 한 형식

    - REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에 *웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일* 이다.
    - REST는 네트워크 상에서 Client 와 Server 사이의 통신 방식 중 하나이다.

</br>

- REST의 구체적인 개념
  - **HTTP URI (Uniform Resource Identifier)** 를 통해 자원을 표현(명시)하고, **HTTP Method - GET, POST, PUT, DELETE** 를 통해 해당 자원에 대한 **CRUD** 동작을 적용하는 것을 의미한다.
  - 웹 사이트의 모든 자원(이미지, 텍스트, DB 등)에 고유한 ID인 HTTP URI를 부여한다.
  - **CRUD 동작**
    - POST - 생성
    - GET - 조회
    - PUT - 수정
    - DELETE - 삭제
    - HEAD - 헤더 정보 조회

</br>

## REST의 장단점

- 장점
  - HTTP 프로토콜의 인프라를 그대로 사용하기 때문에 REST API 사용을 위한 별도의 인프라를 구축할 필요가 없다. - 생산성 측면
  - HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있게 해준다.
  - HTTP 표준 프로토콜을 따르는 모든 플랫폼에서 사용 가능하다.
  - Hypermedia API 의 기본을 충실히 지키면서 범용성을 보장한다.
  - REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악할 수 있다.
  - 여러가지 서비스 디자인에서 생길 수 있는 문제를 최소화한다.
  - 서버와 클라이언트의 역할을 명확하게 분리한다.
- 단점
  - 표준이 존재하지 않는다. - 의문점 : HTTP 프로토콜 표준과 다른 점이 무엇인가?
  - 사용할 수 있는 메소드가 4가지 밖에 없다.
    - HTTP Method 형태의 제한성
  - 브라우저를 통해 테스트할 일이 많은 서비스라면 쉽게 고칠 수 있는 URL보다 Header 값이 더 어렵게 될 수 있다.
  - 구형 브라우저가 아직 제대로 지원해주지 못하는 부분이 존재한다.
    - PUT, DELETE 사용불가
    - pushState 지원하지 않음

</br>

## REST가 필요한 이유

- '애플리케이션 분리 및 통합'
- '다양한 클라이언트의 등장'
- 최근의 서버 프로그램은 다양한 브라우저와 안드로이드폰, 아이폰과 같은 모바일 디바이스에서 통신을 할 수 있어야 한다.
- 이러한 멀티 플랫폼에 대한 지원을 위해 서비스 자원에 대한 아키텍처를 세우고 이용하는 방법을 모색한 결과, REST에 관심을 가지게 되었다.

</br>

## REST 구성 요소

1. 자원 Resource - URI (Uniform Resource Identifier)
   - 모든 자원에는 고유한 ID가 존재하고, 해당 자원들을 Server에 존재한다.
   - 자원을 구분하는 고유한 ID는 '/groups/:group_id'와 같이 **HTTP URI**로 표현된다.
   - Client는 URI를 이용해서 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다.
2. 행위 Verb - HTTP Method
   - HTTP 프로토콜의 Method를 사용한다.
   - HTTP 프로토콜은 GET, POST, PUT, DELETE 와 같은 행위를 제공한다.
3. 표현 Representation of Resource
   - Client 가 자원의 상태(정보)에 대한 조작을 요청하면 Server는 이에 적절한 응답(Representation)을 보낸다.
   - REST에서 하나의 자원은 JSON, XML, TEXT, RSS 등 여러 형태의 Representation으로 표현될 수 있다. → 주로 JSON 혹은 XML을 통해 데이터를 주고 받는 것이 일반적이다.

</br>

