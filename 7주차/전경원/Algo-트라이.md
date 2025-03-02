  # 트라이
  **트라이(Trie)**는 탐색 트리의 일종으로 동적 집합이나 연관 배열을 저장하는 데 사용되는 트리 자료 구조이다.
  - 검색어 자동완성, 사전 찾기 등에 응용될 수 있다.
  - 문자열을 탐색할 때 단순하게 비교하는 것보다 효율적으로 찾을 수 있다.
  - L이 문자열의 길이일 때 탐색, 삽입은 O(L)만큼 걸린다.
  - 대신 각 정점이 자식에 대한 링크를 전부 가지고 있기에 저장 공간을 더 많이 사용한다.
  ### 구조
  - 루트는 비어있다.
  - 각 간선(링크)은 추가될 문자를 키로 가진다.
  - 각 정점은 이전 정점의 값 + 간선의 키를 값으로 가진다.
  - 해시 테이블과 연결 리스트를 이용하여 구현할 수 있다.
  ### 구현
  파이썬에서는 클래스를 통해 트라이 자료구조를 구현할 수 있다.
  ```python
  class Trie(object):
  	# 최초 생성 시 헤드 노드 생성
      def __init__(self):
          self.head = Node(None)

      # 트라이에 문자열 삽입
      def insert(self, string):
          curr_node = self.head

          for char in string:
              # 현재 노드에 해당하는 글자의 자식이 없다면 추가
              if curr_node.children.get(char) is None:
                  curr_node.children[char] = Node()
              # 다음 노드로 이동
              curr_node = curr_node.children[char]
          # 반복 종료 후 단어의 끝 표시
          curr_node.is_termianl = True

      # 트라이에서 전화번호 조회
      def search(self, string):
          curr_node = self.head

          for char in string:
              # 찾아야하는 글자가 없다면 해당 단어가 트라이에 없음
              if curr_node.children.get(char) is None:
                  return False
              # 다음 노드로 이동
              curr_node = curr_node.children[char]
          # 탐색이 종료되었다면 단어가 있다는 것이므로 True 반환
          return True
  ```
