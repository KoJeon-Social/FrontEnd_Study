# 정렬(Sort)

<br />

## 정렬이란?

**정렬(Sort)** 이란 요소들을 일정한 순서대로 열거하는 알고리즘이다.

<br />

## 정렬의 특징

- 정렬 기준은 사용자가 정할 수 있다.
- 크게 비교식과 분산식 정렬로 나눌 수 있다.
- 대부분의 언어가 빌트인으로 제공해준다.
- 삽입, 선택, 버블, 머지, 힙, 퀵 정렬 등 다양한 정렬 방식이 존재한다.

<br />

## 비교식 정렬

**버블 정렬(Bubble Sort)**

- **서로 인접**한 두 요소를 검사하여 정렬하는 알고리즘이다.
- O(n^2)의 시간 복잡도

<br />

**선택 정렬(Selection Sort)**

- **선택한 요소와 가장 우선순위가 높은 요소**를 교환하는 정렬 알고리즘
- O(n^2)의 시간 복잡도

<br />

**삽입 정렬(Insertion Sort)**

- **선택한 요소를 삽입할 수 있는 위치**를 찾아 삽입하는 방식의 정렬 알고리즘
- O(n^2)의 시간 복잡도

<br />

## 분산식 정렬

**분할 정복(Divide and Conquer)**

- 문제를 작은 2개의 문제로 **분리**하고 더 이상 분리가 불가능할 때 처리한 후 합치는 전략
- 다양한 알고리즘에 응용된다.

<br />

**합병 전략(Merge Sort)**

- 분할 정복 알고리즘을 이용한 **최선과 최악이 같은** 안정적인 정렬 알고리즘
- O(n log n)의 시간 복잡도

<br />

**퀵 정렬(Quick Sort)**

- 분할 정복 알고리즘을 이용한 매우 빠르지만 **최악의 경우가 존재**하는 불안정 정렬 알고리즘
- O(n log n)의 시간 복잡도

<br />

## JavaScript에서 사용하기

```jsx
const array = [5, 9, 10, 3, 8, 3, 2];

array.sort(); // ASCII 문자 순서로 정렬된다.
console.log(array); // [10, 2, 3, 3, 5, 8, 9]

array.sort((a, b) => a - b); // 오름차순 정렬
console.log(array); // [2, 3, 3, 5, 8, 9, 10]

array.sort((a, b) => b - a); // 내림차순 정렬
console.log(array); // [10, 9, 8, 5, 3, 3, 2]
```
