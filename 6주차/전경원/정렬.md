# 정렬

### 오름차순 정렬

**sort() / sorted()**

```python
#sort()
lst1 = [3, 1, 4, 2, 5]

lst1.sort() # 리스트를 오름차순으로 정렬
print(lst1) # [1, 2, 3, 4, 5]

#sorted()
lst2 = ['zah', 'abc', 'def', 'ag']

new_list = sorted(lst2) # 리스트를 오름차순으로 정렬
print(new_list) # ['abc', 'ag', 'def', 'zah']
```

### 내림차순 정렬

sort(reverse = True) / sorted(lst, reverse = True)

```python
#sort()
lst1 = [3, 1, 4, 2, 5]

lst1.sort(reverse=True) # 리스트를 내림차순으로 정렬
print(lst1) # [5, 4, 3, 2, 1]

#sorted()
lst3 = ['zah', 'abc', 'def', 'ag']

new_list = sorted(lst3, reverse=True) # 리스트를 오름차순으로 정렬
print(new_list) # ['zah', 'def', 'ag', 'abc']
```

### iterable을 원소로 가지는 List에서 정렬(lambda)

```python
# Tuple을 원소로 가지는 List에서 2번째 원소를 기준으로 오름차순 정렬
lst1 = [('apple', 3), ('banana', 1), ('kiwi', 2), ('orange', 4)]

lst1.sort(key=lambda x: x[1]) # 2번째 원소를 기준으로 오름차순 정렬
print(lst1) # [('banana', 1), ('kiwi', 2), ('apple', 3), ('orange', 4)]

# List를 원소로 가지는 List에서 2번째 원소를 기준으로 내림차순 정렬
lst2 = [['apple', 3], ['banana', 1], ['kiwi', 2], ['orange', 4]]

lst2.sort(key=lambda x: -x[1]) # 2번째 원소를 기준으로 내림차순 정렬
print(lst2) # [['orange', 4], ['apple', 3], ['kiwi', 2], ['banana', 1]]

# 2차원 List를 원소로 가지는 List에서 2번째 원소를 기준으로 내림차순, 3번째 원소를 기준으로 오름차순 정렬
lst3 = [['apple', 1, 300], ['banana', 2, 150], ['kiwi', 2, 400], ['orange', 1, 1000]]

lst3.sort(key=lambda x: (-x[1], x[2])) # 2번째 원소를 기준으로 내림차순, 3번째 원소를 기준으로 오름차순 정렬
print(lst3) # [['orange', 4], ['apple', 3], ['kiwi', 2], ['banana', 1]]
```
