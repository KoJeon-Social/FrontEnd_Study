# BFS & DFS

# BFS(너비 우선 탐색)

너비 우선 탐색은 그래프 탐색 알고리즘으로 같은 깊이에 해당하는 정점부터 탐색하는 알고리즘이다.

![image](https://github.com/user-attachments/assets/56acd2eb-fd6f-420d-9ea1-cceedcf0b994)

- Queue를 이용하여 구현할 수 있다.
- 시작 지점에서 가까운 정점부터 탐색한다.
- V가 정점의 수, E가 간선의 수일 때 BFS의 시간 복잡도는 O(V + E) 이다.

# DFS(깊이 우선 탐색)

깊이 우선 탐색은 그래프 탐색 알고리즘으로 그래프에서 깊은 부분을 우선적으로 탐색하는 알고리즘이다.

![image](https://github.com/user-attachments/assets/76678722-6d40-4e2c-8815-3039cad12ac1)

- Stack을 이용하여 구현할 수 있다.
- 시작 정점에서 깊은 것부터 찾는다.
- V가 정점의 수, E가 간선의 수일 때 DFS의 시간 복잡도는 O(V + E) 이다.
