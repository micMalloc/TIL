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
