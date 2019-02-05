# Kruskal's Algorithm

## Definition

**_Kruskal's Algorithm_** is a **Greedy Algorithm** that finds **a Minimum Spanning Tree**

- **_Spanning Tree_** : A **Tree** that connects **all vertices** in a **Graph**
- **_Minimum Spanning Tree_** : A **Spanning Tree** of _Minimum Weight_ 
- **_Greedy Alogorithm_** : A locally optimal choice is globally optimal
- Kruskal's Algo. is based on Edges

<br>

## Description

- Use **Union-Find** Data-Structure to **_Avoid Cycle_**
- Examine **All Edge** of an Undirected Graph
- Pick a **Minimum-Weight Edge**, avoiding cycles
- Continue until **All Nodes** of the graph have been included

<br>

## Application
* **Network Protocol** ( *Spanning Tree Protocol* )
<br>

## Complexity

* **_Time Complexity_**
  * Recommend to use Kruskal if Graph is Sparse
* **_Space Complexity_**

<br>

## Implementation

* **_Code (C ++)_**

  ```c++
  #include <cstdio>
  #include <vector>
  #include <algorithm>
  using namespace std;
  
  typedef struct EDGE {
  	int a;
  	int b;
  	int c;
  } Edge;
  
  bool cmp_Edge (Edge a, Edge b) {
  	return (a.c < b.c);
  }
  
  int find_set (int);
  bool union_set (int, int);
  int kruskal (int);
  
  vector<int> parent;
  vector<Edge> e;
  
  int main (int argc, char** argv) {
  	int n, m;
  	int a, b, c;
  
  	scanf("%d %d", &n, &m);
  	parent.resize(n + 1);
  	e.resize(m);
  	
  	for (int i = 0; i < m; ++ i) {
  		scanf("%d %d %d", &a, &b, &c);
  		e[i].a = a;
  		e[i].b = b;
  		e[i].c = c;
  	}
  	printf("%d\n", kruskal(n));
  
  	return 0;
  }
  
  int find_set (int u) {
  	if (u == parent[u]) {
  		return u;
  	} return parent[u] = find_set(parent[u]);
  }
  
  bool union_set (int a, int b) {
  	int p, q;
  
  	p = find_set(a);
  	q = find_set(b);
  
  	if (p != q) {
  		parent[p] = q;
  		return true;
  	} return false;
  }
  
  int kruskal (int n) {
  	int total = 0;
  	for (int i = 1; i <= n; ++ i) {
  		parent[i] = i;
  	}
  
  	sort (e.begin(), e.end(), cmp_Edge);
  	for (int i = 0; i < e.size(); ++ i) {
  		if (union_set(e[i].a, e[i].b)) {
  			total += e[i].c;
  		}
  	} return total;
  }
  ```

  

* **_Code (C)_**



