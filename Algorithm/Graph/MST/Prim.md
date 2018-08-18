# Prim's Algorithm

## Definition

Prim's Alogorithm is a **_Greedy Algorithm_** that finds a **_Minimum Spanning Tree_**

* **_Spanning Tree_** : A **Tree** that connects **all vertices** in a **Graph**
* **_Minimum Spanning Tree_** : A **Spanning Tree** of _Minimum Weight_ 
* **_Greedy Alogorithm_** : A locally optimal choice is globally optimal
* Prim's Algo. is based on Vertices

<br>

## Description

1. Use **Queue** Data-Structure
2. Start from a arbitary node and **Undirected Connected Graph**
3. Examine **_All Adjacent Nodes_** of the **Selected node**
4. Pick a **Minimum-Weight Edge**
5. **Continue** from the selected adjacent node
6. Continue until **All Nodes** of the graph have been included and **All Edges** have been considered **at least one**

<br>

## Application
* **Network Protocol** ( *Spanning Tree Protocol* )
<br>

## Complexity
* **_Time Complexity_**
  * O( **V * V** ) (Implemented by Array)
  * O( **E log V (base 2)** ) (Implemented Binary Heap)
* **_Space Complexity_** 
<br>

## Implementation

* **_Code (C)_**

  ```c
  /*Psuedo Code
  Q <- V
  for each v ¡ô V
  	key[v] <- IN
  key[s] <- 0 // some arbitrary v ¡ô V
  while Q != 0
  	do u <- Extract_Min(Q)
  	for each v ¡ô Adj[u]
  		do if v ¡ô Q and w(u, v) < key[v]
  			then key[v] <- w(u, v)
  				 n[v] <- u
  */
  
  #include <stdio.h>
  #define INFINITY 99999
  
  int isEmpty ();
  int isFull ();
  void insert (int);
  int Delete ();
  int isInQ (int);
  int Extract_Min ();
  void mergeSort (int, int);
  void merge (int, int);
  void mst_prims(int);
  
  int key[101], prev[101], cost[101][101], Q[101], tmp[101];
  int front, back, n;
  
  int main ()
  {
  	int i, j;
  	int a, b, w;
  	int current;
  	
  	front = back = -1;
  
  	scanf("%d", &n);
  	for (i = 1; i <= n; ++ i)
  		insert(i);
  
  	for (i = 1; i <= n; ++ i)
  	{
  		for (j = 1; j <= n; ++ j)
  			cost[i][j] = INFINITY;
  	}
  	for (i = 0; i < 10; ++ i)
  	{
  		scanf("%d %d %d", &a, &b, &w);
  		cost[a][b] = cost[b][a] = w;
  	}
  	
  	//Prim's Algorithm
  	for (i = 1; i <= n; ++ i)
  		key[i] = INFINITY;
          
  	key[4] = 0;
  	while (isEmpty())
  	{
  		current = Extract_Min();
  		for (i = 1; i <= n; ++ i)
  		{
  			if (isInQ(i) && cost[current][i] < key[i])
  			{
  				key[i] = cost[current][i];
  				prev[i] = current;
  			}
  		}
  	}
  
  	return 0;
  }
  
  int isEmpty ()
  {
  	if (front >= back)
  		return 0;
  	else
  		return 1;
  }
  int isFull ()
  {
  	if (back >= n)
  		return 0;
  	else
  		return 1;
  }
  void insert (int key)
  {
  	Q[++ back] = key;
  }
  int Delete ()
  {
  	return (Q[++ front]);
  }
  int isInQ (int current)
  {
  	int i;
  
  	for (i = front + 1; i <= back; ++ i)
  	{
  		if (Q[i] == current)
  			return 1;
  	}
  
  	return 0;
  }
  
  int Extract_Min ()
  {
  	mergeSort(front + 1, back);
  
  	return (Delete());
  }
  
  void mergeSort (int start, int end)
  {
  	int mid;
  
  	if (start < end)
  	{
  		mid = (start + end) / 2;
  		mergeSort(start, mid);
  		mergeSort(mid + 1, end);
  		merge(start, end);
  	}
  }
  void merge (int start, int end)
  {
  	int mid = (start + end) / 2;
  	int left, right, idx, i;
  
  	left = start; right = mid + 1;
  
  	idx = 0;
  	while (left <= mid && right <= end)
  	{
  		if (key[Q[left]] < key[Q[right]])
  			tmp[idx ++] = Q[left ++];
  		else
  			tmp[idx ++] = Q[right ++];
  	}
  
  	while (left <= mid)
  		tmp[idx ++] = Q[left ++];
  	while (right <= end)
  		tmp[idx ++] = Q[right ++];
  
  	for (i = 0; i < idx; ++ i)
  		Q[start + i] = tmp[i];
  }
  ```

* **_Code (C ++)_**

