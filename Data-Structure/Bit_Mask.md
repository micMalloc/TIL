# 비트마스크(Bitmask)

정수의 이진수 표현을 자료구조로서 쓰는 기법을 ***비트마스크***(***Bitmask***)라고 부른다.<br>

정확하게는 자료 구조라고 할 수는 없지만, 굉장히 유용하게 쓰이는 도구이다.

-----

### 비트마스크 사용시 장점

- 더 빠른 수행 시간

- 더 간결한 코드

- 더 작은 메모리 사용량

- 연관 배열을 배열로 대체

  ~~~c++
  map<vector<bool>, int> 을 비트마스크를 통해 int[](배열)로 표현할 수 있다.
  이를 통해 시간과 메모리를 절약할 수 있다.
  ~~~

----

### 사용시 유의사항

- 비트가 1이면 "켜져 있다." / 0이면 "꺼져 있다"라고 한다.

- C 와 C++ 에서는 &, |, ^ 등의 비트 연산자의 우선순위는 == 혹은 != 등의 비교 연산자 보다 낮기 때문에 유의해야한다. 

  ~~~c
  int c = (6 & 4 == 4); // 4 == 4 연산이 먼저 계산된다.
  ~~~

- C++ 에서 N 비트 정수를 N 비트 이상 왼쪽 시프트를 하게 될 경우 0이 아니라 오류가 난다.

---

### 비트 연산자

- & (AND)  /  | (OR)  /  ^ (XOR)

- 표

  ![비트연산](/Users/heesu.lee/Desktop/비트연산.png)

----

### 비트마스크 연산을 이용한 집합의 표현

- 공집합

  ~~~c
  int s = 0
  ~~~

- 꽉찬 집합

  ~~~c
  /*
  집합의 전체 개수가 20인 경우
  */
  int s = (1 << 20) - 1;
  ~~~

- 집합에 원소 추가 (해당 비트 켜기)

  ~~~c
  /*
  s 란 집합에서 position 번째에 해당하는 비트 1로 바꾸기
  */
  s |= (1 << position);
  ~~~

- 집합에서 원소 삭제 (해당 비트 끄기)

  ~~~c
  /*
  s 란 집합에서 position 번째에 해당하는 비트 0으로 바꾸기
  */
  s &= ~(1 << position);
  ~~~

- 원소 토글 (켜져있다면 끄고 꺼져있다면 켜기)

  ~~~c
  /* XOR 연산을 이용한다. */
  s ^= (1 << position);
  ~~~

- 원소의 포함 여부 확인

  ~~~c
  if (s & (1 << position) == 1) {
      // 해당 비트가 1이면 켜져있는 것이다.
      printf ("found\n");
  } 
  ~~~

- 두 집합 연산

  ~~~c
  int added = (a | b); // 합집합
  int intersection = (a & b); // 교집합
  int removed = (a & ~b); // 차집합 a - b
  int toggled = (a ^ b); // a 와 b 중 하나에만 들어있는 원소들의 집합
  ~~~
