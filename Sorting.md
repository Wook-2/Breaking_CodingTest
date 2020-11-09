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

<details>
    <summary>잡담</summary>
    
평소에 머리속에서 수도코드(?)로만 대충 떠오르던 정렬알고리즘들을 막상 코드로 구현하고 이해하자니 꽤 오랜시간이 걸렸다...<br>
역시 알고리즘을 이해 + 약간의 암기(?)를 하고 백지상태에서 코드로 구현해보니 조금더 미세한 절차? 순서? 까지 이해가 간 것 같다.  (오래 기억에 남을진 모르겠다. 그랬음 좋겠다.)<br>
아 이제 앞으로 한 챕터 정리를 완성할 때 마다 약간의 잡담?코멘트?를 남길 것이다.  내가 이 글을 남길 때 어떤 기분이었고, 어떤 생각을 하면서 작성했을지 나중에 돌아보고 싶다는 생각이 들었다 ㅋㅋ;.<br>
아무튼 내가 이렇게 알고리즘과 CS개념에 대해 정리하는 글을 쓰는 이유는 2020/11/12 에 있을 코딩테스트 & 면접 ? 때문이다. <br>
지금의 나는 동사무소에서 공익으로 근무하고있다. 그런데 전에 학생인턴으로 일했던 스타트업 회사에서 이번에 병특허가를 받게되어서 나보고 산업기능요원으로 편입할 생각은 없냐고 연락이 왔다. 일단 너무 좋은 기회이다. <br>
돈도 더 받을것이고 경력도 쌓을 수 있으며 실무능력까지 성장시킬 수 있을것이다. 그리고 회사자체도 굉장히 좋은 회사이며 나에게 과분한 기회가 왔다고 생각한다. <br>
근데 갈지 말지 너무 고민이 된다. 최근에 정신적으로 너무 힘들다. 그냥 쉬고싶다는 생각밖에 들지 않는다. 아무튼 면접을 보러가서 내가 어떤일을 하게될것인지 듣고나서 결정할 생각이긴하다.. <br>
그때 어떤 선택을 하고 나중에 이 글을 보게되었을 때 내가 후회할지 아님 그 선택에 만족할지 돌이켜 볼 수 있었으면 좋겠다 . 

</details>

