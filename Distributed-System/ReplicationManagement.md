##### 1031 Review Distributed-System

# Replication Management

실제 Replication이 누구에 의해서, 언제, 어떻게 할 것인지에 대한 논의

<br/><br/>

### **Replication Mangement** 의 핵심 두가지

* **_Content Placement_**

  Finding the best servers for placing content

  내용물을 위치시킬 최적의 서버 찾기

* **_Update Propagation_**

  Propagating the updated content to the relevant replica servers

  최신화된 데이터를 인접한 Replica 서버에 전송

  <br/><br/>

### Replication의 유형

누구에 의해서, 언제, 어떻게 되는지에 따라 그 유형이 나뉘어짐

* **_Static Replication_**
  - **Permanent Replica** : Intial Set of Replica / Mirroring Sites 초기 복제 데이터 셋
* **_Dynamic Replication_**
  - **Server-initiated Replica**
    - Server-initiated replica는 전체 시스템의 성능을 높이기 위해 생성된다.
    - Server-initiated replica는 주로 clients가 집중된 곳에 위치된다.
    - 어느 위치에 복제시킬지 결정하기 위해 Server-Initiated Replica 알고리즘이 적용된다.
    - 예) Content Distributed Network(**CDN**), Reverse Proxy Server
  - **Client-initiated Replica** - *Client Cache*
    - Client-initiated replica는 client들의 access time을 줄이기 위해 생성된다.
    - 예) Web proxy server(Forward proxy server), Web browser cache

<br/>

### Dynamic Replication : Server-Initiated replicas

**접근 횟수**에 따라 적재적소하게 복제되고 삭제되며 운영된다.

* ***Objecives*** : Enhance to improve the performance of the Distributed System
  * Reduce the load on a server (Load Balancing)
  * Files can be replicated to Serves placed near clients (사용자가 집중된 곳에 위치)

* ***Server-initiated Replica Algorithm*** : keep track of access count per files < ***cnt(Q)(S, F)*** >

  Q : 현재 해당 파일 가진 서버 / S : Replica Server (파일 요청 서버) / F : 해당 요청 파일

  * Below Threshold 접근 횟수가 작다면 : ***dep(S, F)*** 해당 파일 서버로부터 삭제시킨다.
  * Exceeds Threshold 접근 횟수가 많다면 : ***rep(S, F)*** 접근 횟수가 많은 서버에 파일을 복제시킨다.

<br/>

### Client-initiated replicas - Client cache

복제 및 일관성 유지는 오로지 Client에 의해 운영된다.

### ***Content Distribution*** 

***Propagation*** of (updated) content to ***relevant*** replica server

(수정된) 내용물을 ***연관된 복제 서버***로 전달하는 것을 의미한다.

* ***Available Bandwidth & Read-Write Ratio*** 이 두가지에 따라 어떻게 복제될지 결정된다.
  * Ratio 높을 시 : Transfer the **modified files** 수정된 파일 자체를 보낸다. - ***Pushing Updates*** by Server
  * Ratio 낮을 시 : Propagate the **invalidation** of update 수정되었음을 알린다. - ***Pulling Updates*** by Client
  * Bandwidth & Processing power : Propagate the **update operation**

- ***Read-Update Ratio***
  - ***Pushing updates*** : Server initiated approach / 요청에 관계없이 수정될 시 수정된 데이터를 전달한다.
  - ***Pulling updates*** : Client initiated approach / 클라이언트의 요청에 의해 서버로부터 수정된 데이터를 가져온다.

<br/><br/>

###  ***Consistency Protocols***

실제 일관성을 맞추기 위해 어떠한 방식들이 있는지에 대해 논의

***분류***

* ***Data-centric consistency***

  * ***Primary-Backup protocols***

    * 모든 ***write oper*ation**는 ***primary se*rver**에서 처리되야한다.

      All ***write operation*** need to be forwarded to the ***fixed primary server***

    * **Process**

      1. Write request
      2. Forward write request to the primary server
      3. ( Write request is operated at the primary server )
      4. Tell backup servers to update
      5. Acknowledge update to primary server
      6. Acknowledge write is completed to client

    * ***Drawback***

      * Client is blocked until all process is completed

      * Non - Blocking approach : Return modified data when write request is operated at the primary server

      * Consistency Problem

        When using Non - bloking approach is used, Consistency problem may be caused.

  * ***Primary-based protocols : Local-Write protocols***

    * ***Update*** 가 요청된 지점으로 프라이머리 서버를 ***이주***시킨다.

      Primary ***migrates*** to the process wanting to perform an update

    * **Process**

      1. Write request
      2. Move item x to new primary server
      3. Perfrom update
      4. Acknowledge write completed
      5. Tell backups to update
      6. Acknowledge update

    * ***Drawback*** : Consistency Problem

      Sequential, tight consistency may not be satisfied

  * ***Quorum-based protocols***

    읽기 혹은 쓰기 위해 각각 다른 복제된 서버로부터 허가를 얻어야하는 프로토콜이다.

    Need ***premission*** from multiple replica servers for file ***read*** or file ***write***

    - 용어

      - ***N*** 복제된 서버의 개수

      - ***Read quor*um** : 읽기 작업을 수행하기 위한 허가의 수 ***N(R)***

        N(R) + N(W) > N prevent read / write conflict

      - ***Write quoru*m** : 쓰기 작업을 수행하기 위한 허가의 수 ***N(W)***

        N(W) > N / 2 prevent write / write conflict

* ***Client-centic consistency***
