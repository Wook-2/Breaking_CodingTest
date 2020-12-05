## Heap

### 사전 지식
1. 완전 이진 트리
    - 루트부터 노드가 채워져있으면서 같은 레벨에서는 왼쪽에서 오른쪽으로 노드가 채워져있는 이진트리를 완전이진트리(complete binary tree)라고 한다.
<img src = "https://github.com/Wook-2/CS_Summary/blob/main/image/%EC%99%84%EC%A0%84%EC%9D%B4%EC%A7%84%ED%8A%B8%EB%A6%AC.PNG?raw=true" alt = "완전이진트리" width ="350px"></img>
2. 우선순위 큐
    - 우선순위 큐는 '우선순위'를 가진 데이터를 저장하는 큐를 의미한다. 
    데이터를 꺼낼 때 우선순위가 높은 데이터가 가장 먼저 나온다는 특징이 있어 많이 활용되고 있다.
    - 우선순위 큐는 트리 구조로 보는 것이 합리적이다. 
    일반적으로 우선순위 큐는 최대 힙을 이용하여 구현한다.

### Heap
- **완전 이진 트리**의 일종, **우선순위 큐**를 위해 만들어진 자료구조.
- 여러개의 값들 중 최댓값 or 최솟값을 빠르게 찾아준다. (최대 힙 , 최소 힙)
- 반정렬 상태를 유지한다.
    - 부모노드의 값이 자식노드의 값보다 크다.

### Heap의 구현
- 힙의 표준 자료구조는 **배열**이다.
- 힙에서의 부모노드와 자식노드간의 관계
    - **Index = 1부터 시작할 때**
        - 왼쪽 자식 index = 2 * (부모 index)
        - 오른쪽 자식 index = 2* (부모 index) + 1
        - 부모 index = (자식 index) / 2
    - **Index = 0 부터 시작할 때**
        - 왼쪽 자식 index = 2 * (부모 index) + 1
        - 오른쪽 자식 index = 2* (부모 index) + 2
        - 부모 index = (자식 index) / 2
<img src = "https://github.com/Wook-2/CS_Summary/blob/main/image/heap.PNG?raw=true" alt ="heap" width = "350px"></img>

### 코드 구현

- **Import**

    ```python
    import heapq

	heap_list = [] # heap구조를 저장할 리스트 선언
    ```

- **Insert**

    ```python
    heapq.heappush(heap_list, 3)
    heapq.heappush(heap_list, 5)
    heapq.heappush(heap_list, 1)

    print(heap_list)
    # => [1, 5, 3]
    ```

    - heapq의 default 자료구조는 최소힙.
    - 시간 복잡도: **O(logN)**
    - 최솟값은 항상 맨앞 heap_list[0]에 위치하나 인덱스 순으로 작은 값이 저장되어있지는 않음.
    ***ex) 2번째로 작은값이 heap_list[1]에 위치하지 않을 수 있음!***
- **Pop & Top**
    - **Pop**

        **시간 복잡도: O(logN)**

        ```python
        value = heapq.heappop(heap_list) # [1, 5, 3]
        print(value) # 1
        print(heapq.heappop(heap_list) # [3, 5]
        ```

    - **Top**

        ```python
        value = heap_list[0] # [3, 5]
        print(value) # 3
        print(heap_list) # [3, 5]
        ```

- **Convert**

    ```python
    heap_list = [4, 1, 7, 3, 8, 5]
    heapq.heapify(heap_list)
    print(heap_list)
    # [1, 3, 5, 4, 8, 7]
    ```

- **Maximum Heap**

    ```python
    import heapq

    nums = [4, 1, 7, 3, 8, 5]
    heap = []

    for num in nums:
      heapq.heappush(heap, (-num, num))  # (우선 순위, 값)

    # heap = [(-8, 8), (-7, 7), (-5, 5), (-1, 1), (-3, 3), (-4, 4)]

    while heap:
      print(heapq.heappop(heap))

    # 8, 7, 5, 4, 3, 1
    ```

- **Heap Sort**

    ```python
    import heapq

    def heap_sort(nums):
      heap = []
      for num in nums:
        heapq.heappush(heap, num)
      
      sorted_nums = []
      while heap:
        sorted_nums.append(heapq.heappop(heap))
      return sorted_nums

    print(heap_sort([4, 1, 7, 3, 8, 5]))

    # [1, 3, 4, 5, 7, 8]
    ```
