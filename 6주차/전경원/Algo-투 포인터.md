# 투 포인터

**투 포인터** 알고리즘은 일차원 배열에 두 개의 포린터를 두고 조작하는 알고리즘이다.

보통 연속적인 구간에 대한 계산을 할 때 많이 사용된다.

### 예시

**특정한 합을 가지는 부분 연속 수열 찾기**

```python
n = 5 # 데이터의 개수 N
m = 5 # 찾고자 하는 부분합 M
data = [1, 2, 3, 2, 5] # 전체 수열

count = 0
interval_sum = 0
end = 0

# start를 차례대로 증가시키며 반복
for start in range(n):
    # end를 가능한 만큼 이동시키기
    while interval_sum < m and end < n:
        interval_sum += data[end]
        end += 1
    # 부분합이 m일 때 카운트 증가
    if interval_sum == m:
        count += 1
    interval_sum -= data[start]

print(count)
```

- start, end를 이용하여 두 값을 조건에 맞춰 증가 시키며 투 포인터 코드 구현
