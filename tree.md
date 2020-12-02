### Tree
** 오늘은 많이 들어봤을 이진트리 부터 시작해서 조금은 생소할 수도 있는 레드블랙트리, Splay 그리고 AVL 트리에 대해 정리해보겠다. **
#### What is Tree?
여러가지 트리에 대해 알기전에 트리가 무엇인지 부터 알아보자.<br>
트리란 아래의 그림처럼 생긴 자료구조를 말한다. <br>
가장 상위에 있는 노드(더이상 부모가 없는)를 루트노드(root node)라고 부르고, 가장 가장자리에 있는(더이상 자식이 없는) 노드를 리프노드(leaf node)라고 한다. <br>
<img src = "https://github.com/Wook-2/CS_Summary/blob/main/image/tree.PNG?raw=true" width = "330px"></img><br>
트리구조는 루트노드에서부터 시작하여 자식노드를 뻗어나가면서 형성되는데<br>
그모습이 마치 나무와 유사하여 트리라는 이름이 붙었다고 한다.
##### Tree의 특징
트리구조는 몇가지 특징을 갖고있다.<br>
이 성질들을 만족하지 못하면 그 데이터구조는 트리구조가 아닌것이다.<br>
- 순환(cycle)이 존재하지 않는다.
- 한 노드에서 다른노드로 도달하는 경로는 한가지만 존재한다.
- 모든 노드가 서로 연결되어있다.
- 간선(Edge)의 수 = 노드의 수 - 1

#### 이진트리(Binary Tree)
이진트리는 모든 노드가 최대 2개의 자식노드를 갖는 트리를 말한다.<br>
<img src="https://github.com/Wook-2/CS_Summary/blob/main/image/btree.PNG?raw=true" height="250px"><br>
위 그림에서 왼쪽트리같은 경우는 모든 노드들의 자식노드의 수가 2개 이하이므로 이진트리가 맞다.<br>
하지만 오른쪽 트리를 보면 자식노드가 3개인 노드가 존재하므로 이진트리가 아니다.<br>
<br>
이진트리에서도 완전 이진트리, 진 이진트리, 포화 이진트리 등으로 한번더 분류할 수 있다. <br>
간단히 설명하고 넘어가겠다.<br>
- 완전 이진트리
: 완전이진트리는 마지막 리프노드의 위치를 제외한 모든 칸이 채워져있는 이진트리를 말한다.
- 진 이진트리
: 리프노드를 제외한 모든 노드들이 2개 혹은 0개의 자식노드를 갖는 이진트리를 말한다.
- 포화 이진트리
: 트리의 깊이에 해당하는 층에 모든 노드가 채워져있는 이진트리를 말한다.



#### Trie Tree
##### Trie tree
: Trie(트라이)는 문자열 탐색에 특화된 트리구조이다. 여기서 Trie는 컴퓨터에서 검색을 의미하는 re**TRIE**val에서 따온 것이라고 한다.<br><br>
트라이의 전체적인 구조는 아래 그림과 같다.<br>
<img src = "https://github.com/Wook-2/CS_Summary/blob/main/image/trietree.PNG?raw=true" width = "400px"></img><br>
예를 들어 내 사전데이터에 단어 Hell, Hat, Car, Cap이 저장되어있다면 저장된 단어들을 Trie Tree로 나타내면 위 그림처럼 나타낼 수 있다. <br>
그림만그림만 봐도 일단 노드하나당 알파벳 하나씩 가지며 문자를 삽입 혹은 탐색할 때 루트노드에서부터 알파벳 하나씩 채워가면서 내려갈 것만 같은 느낌이 온다. 특징(?)이라고 하는게 맞는진 모르겠지만 암튼 정리하면 아래와 같다. 
##### 특징
- 하나의 노드당 하나의 알파벳이 저장되어있다.
- 모든 글자마다 시작하는 알파벳이 다르기 때문에 루트노드는 비워놓는다.
- 문자열의 길이가 m일때 O(m)의 시간복잡도를 가진다.
- 각 노드는 key 값을 알파벳, value값을 노드로 갖는 (파이썬에서)딕셔너리와, 해당노드의 알파벳으로 문자가 완성되는지를 나타내주는 boolean 변수로 이루어진다. 그림으로 설명하면 아래 그림과 같다고 보면된다.
<img src = "https://github.com/Wook-2/CS_Summary/blob/main/image/why_dictionary.PNG?raw=true" width = "400px"></img><br>
(~~ㅋㅋ;; 이쁘게 표로 만드는게 너무 귀찮아서 손으로 그렸다.. 사실 종이에는 이쁘게 그려져있는데 노트북으로 그리려니 못생겨진거다ㅇㅇ.~~)<br>
현재 노드에서 딕셔너리로 자식노드들을 저장하는것이 처음에는 뭔소린가 싶어서 그림으로 정리해보았다. 그러니까 음.. 그림을 보면 루트노드의 딕셔너리에 key값 H, C가 있는것을 확인할 수 있고 각각 자식노드를 value값으로 갖고있는걸 확인할 수 있다.<br>
물론 굳이 딕셔너리로 짜지않고
```python
class Node(object):
	def __init__(self, key):
		self.key = key
		self.children = []
```
처럼 노드가 알파벳을 가지게하고 자식노드를 배열로 만들어 배열에 자식노드를 넣는 방식으로 짤수도 있겠다. 하지만 탐색, 삽입할 때 배열을 통해 찾는것보다 해시테이블(딕셔너리)로 자식노드를 찾는게 더 빨라서 저렇게 구현하였다.<br>
(왜 더 빠른지 궁금하면 "해시테이블"을 키워드로 검색해보아라 파이썬에서 딕셔너리타입은 해시테이블구조로 이루어져있고 해시테이블은 O(1)의 시간복잡도를 갖는다. )

##### 코드 구현
###### 노드 자료구조
```python
class Node(object):
	def __init__(self, key):
		self.children = dict()
		self.isComplete = false
```
###### 트라이 자료구조 & 연산
```python
class Trie(object):
	def __init__(self):
		self.head = Node(None)
	
	def insert(self, val):
		pass
	
	def search(self, val):
		pass
	
	def prefix(self, val):
		pass
```

#### Red & Black Tree
##### Red Black tree
: 레드블랙트리는 대표적인 균형 이진 탐색트리의 한 종류이다. 모든 노드가 흑, 또는 적색이어서 레드블랙트리라고 불린다. <br>
<img src = "https://github.com/Wook-2/CS_Summary/blob/main/image/redblacktree.PNG?raw=true" width = "400px"></img><br>
**(리프노드인 nil은 Black Node로 보면 된다.)**<br>
각 연산에 대한 시간복잡도는 아래와 같다.<br>
- 탐색연산: O(logn)
- 삽입연산: O(logn)
- 삭제연산: O(logn)

##### 특징
- 모든 노드는 Red 또는 Black이다.
- 루트, 리프노드는 모두 Black이다.
- 노드가 Red이면 그 자식노드는 Black이다.
- 한 노드에서 리프노드까지 가는 모든 경로는 같은 수의 Black 노드를 갖는다.


##### 그 외 특이점
1. 모든 노드는 두개의 색깔을 나타낼 수 있는 1비트의 저장공간이 필요하다.
2. `루트로부터 가장 먼 리프노드의 깊이` <= 2 * `루트에서 가장 가까운 리프노드의 깊이`
	- 최단: All black nodes
	- 최장: red-black 반복

##### 코드구현
```python
print("hello world zz")
```

#### Splay & AVL Tree

#### BFS & DFS
