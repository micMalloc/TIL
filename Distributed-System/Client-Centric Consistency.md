##### 1030 Review Distributed System

# Client - Centric Consistency model

> **Consistency Model** 이란, 시스템에서 일관성을 유지하기 위한 정책 혹은 규약

```markdown
앞서 배웠던 Data-Cetric Consistency model은 Client-Centric Consistency model 보다 더 tight한 일관성 정책이다.
Tight한 정책일수록, 자연스레 일관성을 유지하기위한 시스템 내부적 절차가 복잡해진다.(ex. 주고받는 메시지량 증가)
```

<br/>

### *Client-Centric Consistency model*

**_단일 클라이언트_**의 일정 수준의 데이터 접근 일관성을 보장하는 것을 의미한다.<br/>

여러 클라이언트의 동시 접근에 대해선 보장하지 않는다(즉, 데이터 중심의 일관성은 유지하지 않음)

**_Eventual Consistency_**<br/>

일관성 유지가 크리티컬하지 않은 시스템에서, 시스템 전체 데이터 일관성을 맞추기보다 각각의 특정한 클라이언트의 일관성을 맞추는 정책

> *Client-centric consistency model is to avoid __system wide consistency__* by __concentrating on what specific client want__, instead of what should be maintained bt server.

<br/>

~~~
<일관성 유지가 크리티컬하지 않은 시스템 예시>
[조건]
	1. write 작업이 거의 일어나지 않고, 대부분이 read 작업이 대부분인 경우
	2. 동시에 write가 거의 일어나지 않는 경우
- Database System
- Web Cache Server, Browser Cache
~~~

하지만, 클라이언트가 동일한 **Replica**에 항상 접근하는 경우에 **_Eventual Consistency_** 유지할 수 있지만, 클라이언트가 여러 **Replica**에 접근하게 되는 경우에 유지할 수 없게 된다. 이런 경우 추가적인 조치를 통해 일관성을 유지할 수 있는데 추가사항은 다음과 같다.

~~~
* Monotonic Read
* Monotonic Write
* Read-Your-Write
* Write-Follows-Reads
~~~

> **NOTATION**
>
> W(x1 ; x2) = W(x1) -> W(x2)
>
> W(x1 | x2), W(x1)와 W(x2)는 **_concurrent_** 하다. 즉, 둘의 순서를 알 수 없다.

<br/>

#### 추가조건 설명

* **Monotonic Read**

  단일 클라이언트가 다른 Replica에서 동일한 x에 접근하였을 경우 그 값이 반드시 같거나 최신의 값을 읽어야한다.

* **Monotonic Write**

  단일 클라이언트가 write 작업을 수행할 경우 반드시 동일 클라이언트로부터 수행된 이전의 write는 완료 되었어야한다.

  즉, 동일한 클라이언트로부터 수행된 쓰기 순서는 반드시 지켜져야한다.

* **Read-Your-Write**

  자신이 작성한 write를 read할 수 있어야 한다.

  즉, 자신이 수행한 write 작업에 대해서 추후에 read할 수 있어야 한다는 의미

* **Write-Follows-Read**

  동일 클라이언트가 write 수행할시 반드시 자신이 read한 값으로부터 작업을 수행하여야한다.

  즉, 쓰기 작업시 반드시 읽어드린 값과 동일하거나 최신의 값이어야한다.

<br/>

### **_결론_**

결국 시스템이 무엇을 요구하느냐에 따라 정책이 달라지는 것이다. 강력한 일관성이 요구된다면 Client-centric 보단 Data-centric 일관성이 적용되어야 하고 일관성 유지가 크리티컬하지 않는다면, Client-cetric 정책이 적용되는 것이다.