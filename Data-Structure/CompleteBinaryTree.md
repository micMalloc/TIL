# 완전 이진 트리

> **완전 이진 트리의 속성**
>
> ~~~markdown
> * 레벨 k에 있는 최대 노드의 수는 2^(k-1)이다.
> * 높이가 h인 이진 트리의 최대 노드 개수는 2^(h - 1)
> * N 개의 노드를 가진 완전 이진트리의 높이는 log(N + 1)이다. <base 2>
> * 각 노드 당 최대 2개의 자식 노드를 가질 수 있다. (이진 트리)
> * 마지막 레벨을 제외한 각 레벨이 빠짐 없이 채워져 있어야 한다.
> * 마지막 레벨 역시 왼쪽 부터 차례대로 노드들이 채워져 있어야 한다.
> ~~~

>**리스트(배열) 을 통한 완전 이진 트리 구현**
>~~~markdown
>* tree[i]의 부모는 a[i / 2]
>* tree[i]의 왼쪽 자식은 a[2 * i]
>* tree[i]의 오른쪽 자식은 a[2 * i + 1]
>~~~



## HEAP 힙 

> 완전 이진트리를 통한 힙 구현
>
> ~~~markdown
> * 완전 이진트리의 성질을 가진 - 빈 노드가 있으면 안된다.
> * 자식 노드는 부모 노드보다 높은 순위를 가지면 안된다.
> 	- Max heap 부모 노드는 자식 노드보다 큰 값을 가진다.
> 	- Min heap 부모 노드는 자식 노드보다 작은 값을 가진다.
> ~~~



#### 구현

> ~~~c
> 
> // 최대 힙 개수는 2^h-1
> // h = logN (N 노드 개수 / Base 2)
> const int HEAP_SIZE = 100;
> 
> // 루트는 항상 1
> const int ROOT = 1;
> 
> int heap[HEAP_SIZE];
> int node_count = 0;
> 
> int max_cmp (int left, int right) {
>     return heap[left] < heap[right];
> }
> 
> int push_heap (int key) {
>     int parent, child;
> 
>     ++ node_count;
> 
>     // Overflow
>     if (node_count > HEAP_SIZE) return 0;
> 
>     heap[node_count] = key;
> 
>     child = node_count;
>     parent = child >> 1;
> 
>     // Heapify - 힙 성질 유지
>     while (parent > 0 && max_cmp(parent, child)) {
>         int tmp = heap[parent];
>         heap[parent] = heap[child];
>         heap[child] = tmp;
> 
>         child = parent;
>         parent = child >> 1;
>     }
> 
>     return 1;
> }
> 
> int pop_heap () {
>     int top;
>     int parent, child;
> 
>     // Underflow
>     if (node_count == 0) return 0;
> 
>     top = heap[ROOT];
> 
>     heap[ROOT] = heap[node_count];
>     heap[node_count --] = 0;
> 
>     parent = ROOT;
>     child = parent << 1;
> 
>     // Heapify - 힙 성질 유지
>     while (child <= node_count) {
> 
>         if (heap[child] < heap[child + 1]) child ++;
>         if (max_cmp(parent, child) == 0) break;
> 
>         int tmp = heap[parent];
>         heap[parent] = heap[child];
>         heap[child] = tmp;
> 
>         parent = child;
>         child = parent << 1;
>     }
> 
>     return top;
> }
> ~~~

