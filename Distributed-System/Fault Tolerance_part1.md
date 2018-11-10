##### 1106 Review

# Fault Tolerance - part 1

Failure란 사실 굉장히 빈번하게 일어난다.

그렇다면 이러한 실패가 일어나더라도 시스템이 재대로 작동할 수 있게끔 하는 것이 바로 **_Fault Tolerance_** 이다.

- ***Non - Distributed System***

  Single point of failure - 하나의 실패가 시스템 전체에 영향을 주게 된다. / 전체 시스템 다운

- ***Distributed System***

  **Partial Failure** - 몇 개의 프로세스나 서버가 다운이 되더라도 정상적으로 작동 가능 / 시스템의 규모(Redundancy) 덕분에 가능함

  <br/>

분산 시스템에 있어 중요한 핵심 목표 중 하나는 빈번히 발생되는 부분적 실패(*Partial Failure*)에 대해 수용할 수 있으면서 이와 동시에 발생된 실패를 해결(*Recovery*)할 수 있어야 한다. 이러한 분산 시스템은 ***Fault Tolerant*** 하다고 한다.

<br/><br/>

## Basic Concept

Fault Tolerance의 기본적으로 쓰이는 개념

- ***Dependability*** : Dependable system 일수록 fault tolerance 하다고 할 수 있다. / 시스템 신뢰성 혹은 안정성

  기본적으로 시스템의 **Dependabilty**는 4 가지 속정으로 정의되어질 수 있다.

  4 가지 속성은 다음과 같다.

  - **Availability** : 가용성 - 전체 시간 중 실제 동작 시간, 주로 %(퍼센트)로 표현된다.

  - **Reliability** : 신뢰성 - 시스템이 다운될 때 까지의 걸린 시간, 주로 요일 시간으로 표현된다.

    ​			실패가 발생될 때까지의 평균 시간 - **Mean Time To Failure** (MTTF)

  - **Safety** : 안정성 - 시스템 실패의 규모가 어느정도인지, 실패 규모가 작다면 안정성이 높다고 할 수 있다.

  - **Maintainability** : 유지관리성 - 얼만큼 빠르게 Failure에 대해서 복구시키는가

    ​				유지관리성이 높으면 그만큼 가용성 역시 높아진다. 복구가 빨리 될 수록 그 만큼 더 사용가능하기 때문이다.  복구하는데까지 걸리는 평균 시간 - **Mean Time To Repair**(MTTR)

    **Mean Time Between Failure(MTBF)** = MTTF + MTTR	

    **Availabilty** = MTTF / MTBF x 100 (%)

    ![MTBF](https://user-images.githubusercontent.com/22839766/48064160-67926d80-e20a-11e8-96eb-bbacdd50c622.png)

    <br/>

- ***Failure*** : 원하지 않는 결과가 리턴되거나 응답하지 않은 상태를 뜻함

  하나 이상의 서비스가 제공되지 않은 상태 (잘못된 결과값 or 응답자체 x)

  - **Error** : 실패를 야기시키는 시스템의 일부분

  - **Fault** : Error의 원인

    예) 잘못 작성된 코드 그 자체는 error / 이러한 코드를 프로그래밍한 개발자는 fault

  - **Fault Tolerance** : 시스템 상에 Failure를 야기시킬만한 여러 falut가 있음에도 정상적으로 서비스하는 것을 의미함

  **[ Types of Fault ]**

  - **Transient Fault** : 일회성 / 한 번만 발생한 경우
  - **Intermittent Fault** : 비주기적으로 발생한 경우 / 디텍션 or 트랙킹하기 어려움
  - **Permanent Fault** : 한번 발생 후 계속 발생하는 경우

  <br/>

- ***Failure Models*** 

  여러 실패 종류

  - **Crash failures** : 더 이상 동작하지 않은 상태 / 재부팅을 통해 해결가능

  - **Omission failures** : 들어온 요청을 응답하지 않고 생략되거나 뛰어넘게 되는 상태

    - Recevie omission : 요청을 받아드리지 못한 상태 / 서버의 버퍼가 가득차서 요청 받지 못한 경우
    - Send omission : 요청에 응답하였지만 받지 못한 상태 / 서버가 응답 보냈는데 os 버퍼가 가득차 받지 못한 경우

  - **Timing failures** : 응답시간 너무 늦어져서 실패로 간주된 경우

  - **Response failures** : 잘못된 결과를 응답하는 경우

    - Value failure : 요청은 재대로 왔지만, 잘못된 값을 찾은 경우
    - State transition failure : 잘못된 요청을 수신하고, 그것을 실행하다 요청이 잘못된 상태로 전환되는 경우

  - **Arbitary(Byzantine) failures** : 항상 그러는 것이 아니라 잘못된 값이 비주기적으로 애매하게 발생하는 경우

    ​							***Arbitary responses, Arbitary times***

    <br/>

- Main Approach for ***Fault Tolerance***

  ***Redundancy*** : 기본적으로 데이터 혹은 프로세스 자체를 중복시켜 해결한다.

  - **Information Redundancy** : 주고받는 정보 속에 중복된 데이터를 넣어 복구시킨다.

  - **Time Redundancy** : 동일한 내용의 정보를 다시 보낸다.

  - **Physical Redundancy** : 동일한 작업을 수행하는 **Software(Process)** 나 **Hardware**를 여러개 중복시킨다.

    <br/>

- ***Process Resilience***

  ***Resilience : 회복 탄련성***

  프로세스들을 그룹 내에서 복제시켜 프로세스의 손실 혹은 실패를 보호하고 회복한다.

  - **Group Organization**

    - **Flat Group** : Coordinator가 존재하지 않고 모두 동일한 작업을 수행하게 된다.

      동일한 작업을 모두 수행하기 때문에 하나가 망가지더라도 전체 그룹에 큰 영향 끼치지 않는다.

      하지만, 일 처리 효율성은 떨어진다.

    - **Hierarchical Group** : **Coordinator**가 존재하여 프로세스들간의 업무 배정을 진행한다.

      동일한 작업을 모두 똑같이 수행하는 것이 아니라 업무를 배정하기 때문에 효율성은 높아진다.

      그렇지만, 그에 비해 Coordinator가 다운될 시 전체 그룹이 다운될 수 있기에 위험성이 높다.

      Coordinator 실패시 Election을 통해 다시 선정한다. - Bully & Ring

