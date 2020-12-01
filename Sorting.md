### Sorting
**여러가지 정렬알고리즘 중에서 빠른축에 속하는 Quick sort, Merge sort, Heap sort에 대해 간단히 정리한다.**<br>

> Don`t do Bubble Sort!

이 글에서는 위 세가지 정렬이 어떻게 이루어지는지 간단한 영상을 게시하고 파이썬 코드로 구현하는 정도로 넘어가겠다.

#### Quick Sort (퀵정렬)
##### 시간복잡도 : O(nlogn)
<img src="https://github.com/Wook-2/Breaking_CodingTest/blob/main/image/quick_sort.gif?raw=true" width = "350px">

```python
def quick_sort(arr):
	if len(arr) <= 1:
		return arr
	pivot = arr[len(arr)//2]
	small, big, equal = [], [], []
	for i in arr:
		if i < pivot:
			small.append(i)
		elif i > pivot:
			big.append(i)
		else:
			equal.append(i)
	return quick_sort(small) + equal + quick_sort(big)
```
#### Merge Sort (병합정렬)
##### 시간복잡도 : O(nlogn)
<img src = "https://github.com/Wook-2/Breaking_CodingTest/blob/main/image/merge_sort.gif?raw=true" width = "350px">

```python
def merge_sort(arr):
	if len(arr) < 2:
		return arr
	mid = len(arr)//2
	left = merge_sort(arr[:mid])
	right = merge_sort(arr[mid:])
	merged_arr = []
	l = r = 0
	while l < len(left) and r < len(right):
		if left[l] < right[r]:
			merged_arr.append(left[l])
			l += 1
		else:
			merged_arr.append(right[r])
			r += 1
	merged_arr += left[l:]
	merged_arr += right[r:]
	return merged_arr
```
#### Heap Sort (힙정렬)
##### 시간복잡도 : O(nlogn)
<img src = "https://github.com/Wook-2/Breaking_CodingTest/blob/main/image/heap_sort.gif?raw=true" width = "350px">

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

```
