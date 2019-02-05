# Floyd-Warshall Algorithm

**_플로이드-워셜 알고리즘_** <br>

**_All-Pair Shortest Algorithm_** <br>

```
그래프에서 모든 꼭짓점 사이의 최단 경로의 거리를 구하는 알고리즘
음수 가중치를 갖는 간선도 음의 순환 혹은 싸이클만 없다면 잘 처리된다
삼중 루프를 사용하는데 제일 바깥쪽 루프문은 거쳐가는 꼭짓점을 의미하며, 두 번째 루프문은 출밣하는 꼭짓점, 세 번째 반복문은 도착하는 꼭짓점을 의미한다.
Reference : 위키백과
```

```c++
#include <cstdio>
#define MAX_SIZE 101

void floyd_warshall();

// The number of Nodes
int n

// Adjacent Matrix for representing a Graph
// In Floyd-Warshall Algo, You must use Adjacent Matrix
int adj_matrix[MAX_SIZE][MAX_SIZE];

// Distance Matrix for Recording All-Pair distance
int d[MAX_SIZE][MAX_SIZE];

int main (int argc, char* argv[]) {
    
    int m; // The number of edges in a Graph
    int u, v;
    int cost;
    
    // Construct Adjacent Matrix
    while (m--) {
        scanf("%d %d %d", &u, &v, &cost);
        adj_matrix[u][v] = cost;
    }
    
    return 0;
}

void floyd_warshall () {
    // Initialize Distance Matrix
    for (int i = 1; i < (n + 1); ++ i) {
        for (int j = 1; )
    }
}
```

