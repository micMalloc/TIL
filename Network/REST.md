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
  - **HTTP URI (Uniform Resource Identifier)**를 통해 자원을 표현(명시)하고, **HTTP Method - GET, POST, PUT, DELETE** 를 통해 해당 자원에 대한 **CRUD** 동작을 적용하는 것을 의미한다.
  - 웹 사이트의 모든 자원(이미지, 텍스트, DB 등)에 고유한 ID인 HTTP URI를 부여한다.
  - **CRUD 동작**
    - POST - 생성
    - GET - 조회
    - PUT - 수정
    - DELETE - 삭제
    - HEAD - 헤더 정보 조회

