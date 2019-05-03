# 퀵 정렬 (Quick Sort)

> ***퀵 정렬***이란 **Pivot** 값을 정하여 그 기준으로 **작은값들을 왼쪽**으로, **큰 값들은 오른쪽**으로 위치를 변경시키는 작업을 **반복적으로 수행**하여 정렬을 시키는 알고리즘이다.

<br>

### 퀵 정렬의 수행

----

1. 현재 고려되는 구간에서의 Pivot 값을 선정한다.
2. Pivot을 기준으로 왼쪽과 오른쪽에서 각각 크거나 작은 값을 찾아 위치를 바꾸어준다.
3. 최종적으로 Pivot과 반복문 수행 뒤의 오른쪽 Index의 위치를 바꾸어준다.
4. 위의 작업을 구간의 길이가 1이 될 때까지 반복적으로 수행한다.

<br>

> Pivot 값 선정시 일반적으로 랜덤하게 선택한다. 
>
> 예) 첫 번째 혹은 마지막 값

<br>

### 시간 복잡도

----

평균적으로 퀵 정렬의 반복적 수행은 트리로 나타낼 수 있는데 해당 트리의 높이가 주로 log N이고 각 트리의 레벨마다 N 번씩 비교 연산을 수행하게 된다.

따라서, 가장 많이 쓰이는 퀵 정렬은 평균적으로 O(N log N) <base 2>의 시간 복잡도를 가진다.

단, 퀵 정렬은 불균등 분할을 하기 때문 최악의 경우 트리의 높이가 N이 될 수 있다.

이러한 경우, 퀵 정렬은 O(N^2)의 시간 복잡도를 가지게 된다.

~~~
이미 리스트가 정렬이 되어 있는 경우 최악의 시간 복잡도를 가지게 된다.
따라서, 불균등 분할로 인한 최악의 경우를 갖지 않기하기 위해선 최대한 중간값을 Pivot으로 선정하는게 중요하다.
~~~

<br>

### 구현

----

~~~c

int partition (int* data, int start, int end) {
    int pivot;
    int left, right;

    pivot = data[start];
    left = start + 1;
    right = end;

    while (left <= right) {

        while (data[left] <= pivot) {
            left ++;
        }
        while (data[right] >= pivot && right > start) {
            right --;
        }

        if (left < right) {
            swap(&data[left], &data[right]);
        }
    }

    swap(&data[start], &data[right]);

    return right;
}

void quick_sort (int* data, int start, int end) {
    int pivot;

    if (start < end) {
        pivot = partition(data, start, end);

        quick_sort(data, start, pivot - 1);
        quick_sort(data, pivot + 1, end);
    }
}
~~~

