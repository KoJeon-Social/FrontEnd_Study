# 스택

**스택(stack)**은 **LIFO(Last In First Out)**이라는 개념을 가진 선형 자료구조이다.

- Python에서는 가장 뒤 쪽에 데이터를 집어넣는 **append()**, 가장 뒤쪽에서 데이터를 꺼내는 **pop()**이 있다.
- 서로 관계 있는 여러 작업을 연달아 수행하면서 이전의 작업 내용을 저장해 둘 필요가 있을 때 사용된다.

```python
stack = []

# 삽입(5) - 삽입(2) - 삽입(3) - 삽입(7) - 삭제() - 삽입(1) - 삽입(4) - 삭제()
stack.append(5)
stack.append(2)
stack.append(3)
stack.append(7)
stack.pop()
stack.append(1)
stack.append(4)
stack.pop()

print(stack) # 최하단 원소부터 출력
print(stack[::-1]) # 최상단 원소부터 출력
print(stack[-1]) # 최상단 원소(top) 출력
```
