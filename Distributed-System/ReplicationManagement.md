##### 1031 Review Distributed-System

# Replication Management

실제 Replication이 누구에 의해서, 언제, 어떻게 할 것인지에 대한 논의

<br/><br/>

####**Replication Mangement** 의 핵심 두가지

* **_Content Placement_**

  Finding the best servers for placing content

  내용물을 위치시킬 최적의 서버 찾기

* **_Update Propagation_**

  Propagating the updated content to the relevant replica servers

  최신화된 데이터를 인접한 Replica 서버에 전송

  <br/><br/>

#### Replication의 유형

누구에 의해서, 언제, 어떻게 되는지에 따라 그 유형이 나뉘어짐

* **_Static Replication_**
  - **Permanent Replica** : Intial Set of Replica / Mirroring Sites 초기 복제 데이터 셋
* **_Dynamic Replication_**
  - **Server-initiated Replica** : 
  - **Client-initated Replica**