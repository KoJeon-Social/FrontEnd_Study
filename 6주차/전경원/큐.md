# 큐

**큐(Queue)**는 **FIFO(First In First Out)**이라는 개념을 가진 선형 자려구조이다.

**선형 큐(Linear Queue)**와 **원형 큐(Circular Queue)**가 존재한다. \*\*\*\*

- Python에서는 데이터를 집어넣는 enqueue를 위해서 **put()**, dequeue를 위해서 **get()**을 사용한다.

> 추가로 Python에서는 deque 클래스를 사용하여 데이터를 양방향에서 추가하고 제거할 수 있다. - **appendleft(), popleft()**

```python
from collections import deque

queue = deque()
# 삽입(5) - 삽입(2) - 삽입(3) - 삽입(7) - 삭제() - 삽입(1) - 삽입(4) - 삭제()
queue.append(5)
queue.append(2)
queue.append(3)
queue.append(7)
queue.popleft()
queue.append(1)
queue.append(4)
queue.popleft()

print(queue)
```
