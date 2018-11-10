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
    - 어느 위치에 복제시킬지 결정하기 위해 Dynamic replication 알고리즘이 적용된다.
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

***Content Distribution*** Propagation of (updated) content to relevant replica server

* ***Available Bandwidth & Read-Write Ratio*** 이 두가지에 따라 어떻게 복제될지 결정된다.
  * Ratio 높을 시 : Transfer the **modified files** 수정된 파일 자체를 보낸다. - ***Pushing Updates*** by Server
  * Ratio 낮을 시 : Propagate the **invalidation** of update 수정되었음을 알린다. - ***Pulling Updates*** by Client
  * Bandwidth & Processing power : Propagate the **update operation**

<br/><br/>