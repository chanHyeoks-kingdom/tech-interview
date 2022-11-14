### [1. 트리]
#### (1) 완전 이진트리는 뭔가요?

```
자식 노드의 개수가 최대 2개인 이진 트리를 의미합니다.
```

#### (2) 아 그래요? 트리 얘기가 나와서 여쭤보는건데, 트리를 구현하는 방법엔 크게 어떤게 있나요?
```
클래스를 이용해 표현할수도 있고 배열을 이용해서 표현할수도 있습니다.
배열로 표현하는 경우에는 완전 이진 트리를 표현할 수 있는데 편의상 0번 인덱스를 비워주고 상대적 위치를 이용해 '부모', '형제' 노드등을 파악합니다.
```

#### (3) 완전 이진트리에서 자식노드나 부모 노드로의 접근은 어떻게 하나요?

```
1. 현재 인덱스 * 2 -> 왼쪽 자식의 인덱스
2. 현재 인덱스 * 2 + 1 -> 오른쪽 자식의 인덱스
3. 현재 인덱스 // 2 -> 부모의 인덱스
```
```
* reference
트리를 구현할 때는 편의성을 위해 0번째 인덱스는 사용되지 않습니다!
그래서 None 값을 배열에 넣고 시작합니다! [None]

      8      Level 0 -> [None, 8] 첫번째 레벨의 8을 넣고,
    6   3    Level 1 -> [None, 8, 6, 3] 다음 레벨인 6, 3을 넣고
   4 2 5     Level 2 -> [None, 8, 6, 3, 4, 2, 5] 다음 레벨인 4, 2, 5를 넣으면 됩니다!

자 그러면, [None, 8, 6, 3, 4, 2, 5] 라는 배열이 되는데
다시 역으로 이 배열을 활용해서 트리 구조를 분석해보겠습니다.
다음과 같은 방법으로 트리 구조를 파악할 수 있습니다.

1. 현재 인덱스 * 2 -> 왼쪽 자식의 인덱스
2. 현재 인덱스 * 2 + 1 -> 오른쪽 자식의 인덱스
3. 현재 인덱스 // 2 -> 부모의 인덱스

예를 들어서 1번째 인덱스인 8의 왼쪽 자식은 6, 오른쪽 자식은 3 입니다.
그러면 1 * 2 = 2번째 인덱스! 6!
그러면 1 * 2 + 1 = 3번째 인덱스! 3! 입니다!
부모를 찾아보면, 3 // 2 = 1번째 인덱스 8 이므로 부모를 찾을 수 있습니다.

이를 다시 생각해보면
[None, 8, 6, 3, 4, 2, 5] 는
8 밑에 6, 3 이 있고, 6, 3 밑에 4, 2, 5가 있는 완전 이진 트리구나! 생각할 수 있습니다.

```
#### (4) 그럼 이진트리에서 리프 노드까지 각 레벨에 노드가 꽉 차있을 경우 노드의 최대 레벨 라인의 노드 개수는 몇개인가요?
```
높이를 n이라고 할 때 2^n개요.
```

#### (5) 그럼 모든 노드의 개수는 어떻게 구하는지 아세요?
```
높이를 h라고 했을때 2^(h+1)-1 이요.
반대로 말하면 모든 노드의 개수가 n이면 트리의 높이는 log2(n+1)-1이어서요 
결국 트리의 높이는 최대로 해봤자 O(log2N)임을 알 수 잇습니다.
```


### [2. 힙]

#### (1) 혹시 힙에 대해서 아시나요? 특징이 뭔가요?

```
힙은 완전이진트리의 한 종류인데요, 최댓값과 최솟값을 빠르게 구하기 위해 고안되었습니다.
결국 최댓값 최솟값을 찾는 문제에선 힙을 쓰면 되것죠?

이를 위해 힙은 항상 큰 값을 상위 레벨로, 작은 값을 하위 레벨로 유지하는 완전이진트리입니다.
따라서 가장 큰 값이나 작은 값을 맨 위로 올리기 때문에 최댓값, 최솟값을 찾기가 쉽습니다.
최댓값이 루트 노드에 있으면 (MAX Heap), 최솟값이 루트 노드에 있으면 (MIN Heap)라고 합니다.
```

#### (2) 한번 구현해보세요
```
class MaxHeap:
    def __init__(self):
        self.items = [None]

    def insert(self, value):
        self.items.append(value)
        cur_index = len(self.items) - 1

        while cur_index > 1:  # cur_index 가 1이 되면 정상을 찍은거라 다른 것과 비교 안하셔도 됩니다!
            parent_index = cur_index // 2
            if self.items[parent_index] < self.items[cur_index]:
                self.items[parent_index], self.items[cur_index] = self.items[cur_index], self.items[parent_index]
                cur_index = parent_index
            else:
                break

    def delete(self):
        self.items[1], self.items[-1] = self.items[-1], self.items[1]
        delete_data = self.items.pop()
        cur_index = 1

        while cur_index <= len(self.items)-1:
            left_child_index = self.items[cur_index]
            right_child_index = self.items[cur_index]

            max_index = cur_index

            if left_child_index <= len(self.items) -1 and self.items[left_child_index] > self.items[max_index]:
                max_index = left_child_index
            if right_child_index <= len(self.items) - 1 and self.items[right_child_index] > self.items[max_index]:
                max_index = right_child_index

            if max_index == cur_index:
                break

            self.items[cur_index], self.items[max_index] = self.items[max_index], self.items[cur_index]
            cur_index = max_index

        return delete_data  # 8 을 반환해야 합니다.


max_heap = MaxHeap()
max_heap.insert(8)
max_heap.insert(6)
max_heap.insert(7)
max_heap.insert(2)
max_heap.insert(5)
max_heap.insert(4)
print(max_heap.items)  # [None, 8, 6, 7, 2, 5, 4]
print(max_heap.delete())  # 8 을 반환해야 합니다!
print(max_heap.items)  # [None, 7, 6, 4, 2, 5]
```






