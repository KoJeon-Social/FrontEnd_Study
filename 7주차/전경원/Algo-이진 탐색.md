# 이진 탐색

**이진 탐색(Binary Search)**는 정렬 되어있는 요소들을 반씩 제외하며 찾는 알고리즘이다.

![image](https://github.com/user-attachments/assets/9a5f4cc6-7718-43a0-9a20-61105d6e2706)

> O(log n) 만큼 시간 복잡도가 걸린다.

### 특징

- 반드시 정렬이 되어있어야 사용할 수 있다.
- 배열 혹인 이진 트리를 이용하여 구현할 수 있다.
- 시간 복잡도가 O(log n)인 만큼 상당히 빠르다.
- 이진 탐색은 배열과 트리를 이용해 구현할 수 있다.

### 문제점

- 최악의 경우 한쪽으로 편향된 트리가 될 수 있다.
- 그런 경우 순차 탐색과 동일한 시간복잡도를 가진다.
- 이를 해결하기 위해 AVL 트리, 레드-블랙 트리 자료구조를 이용할 수 있다.

### 이진 탐색 구현

- 반복문

```python
def binary_search(target, data):
    data.sort()
    start = 0 			# 맨 처음 위치
    end = len(data) - 1 	# 맨 마지막 위치

    while start <= end:
        mid = (start + end) // 2 # 중간값

        if data[mid] == target:
            return mid 		# target 위치 반환

        elif data[mid] > target: # target이 작으면 왼쪽을 더 탐색
            end = mid - 1
        else:                    # target이 크면 오른쪽을 더 탐색
            start = mid + 1
    return
```

- 재귀

```python
def binary_search(target, start, end):
    if start > end:		 # 범위를 넘어도 못찾는다면 -1을 반환
        return -1

    mid = (start + end) // 2  # 중간값

    if data[mid] == target:	# 중간값의 데이터가 target과 같다면 mid를 반환
        return mid

    elif data[mid] > target: # target이 작으면 왼쪽 탐색
        end = mid - 1
    else:                    # target이 크면 오른쪽 탐색
        start = mid + 1

    return binary_search(target, start, end) # 줄어든 범위를 더 탐색

def solution(target, data):
    data.sort()  # 정렬(필수)
    start = 0
    end = len(data) - 1
    return binary_search(target, start, end)
```
