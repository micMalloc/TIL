# Dijkstra's Algorithm

**_Single Source Shortest Path Algorithm_**

**_단일 시작점 최단 경로 알고리즘_**

```
하나의 시작점에서 다른 모든 정점까지 가는 최단거리를 구하는 알고리즘
```

<br>

**너비 우선 탐색( _Breadth -First - Search_ ) 확장 알고리즘** 

<br>

## 조건

**_Weighted - Directed - Graph_**

가중치는 음수를 가지지 않는다.

<br>

## Psuedo Code

```
d[s] ← 0 // s is source
for each v in V - {s}
	d[v] ← INFINITY

S ← 0 // zero set
Q ← V
while Q is not empty
	do u ← Extract-Min(Q)
	add u to S
	for each v in adj[u]
		/* RELAXATION STEP */
		do if d[v] > d[u] + w(u, v)
			then d[v] ← d[u] + w(u, v)
```



<br>

## Implementation
```c
#include<cstdio>
```

<br>
## 정당성

**_귀류법_** 을 통한 증명

```
귀류법이란, 어떤 명제를 반대로 가정했을때, 모순을 이끌어내어 가정이 거짓임을 증명하는 방법을 뜻한다.
또 다른 말로는 간접 증명이라고도 한다.
```



