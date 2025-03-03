# 트라이(Trie)

<br />

## 트라이란?

**트라이(Trie)** 는 탐색 트리의 일종이다. 동적 집합이나 연관 배열을 저장하는 데 사용되는 트리 자료 구조다.

<br />

## 트라이의 특징

- 검색어 자동 완성, 사전 찾기 등에 응용할 수 있다.
- 문자열을 탐색할 때 단순하게 비교하는 것보다 더 효율적으로 찾을 수 있다.
- L이 문자열의 길이일 때 탐색, 삽입은 O(L) 만큼 걸린다.
- 각 정점이 자식에 대한 링크를 전부 가지고 있으므로 저장 공간을 더 많이 사용한다.

<br />

## 트라이 구조

![Image](https://github.com/user-attachments/assets/4c3eb2d7-48e1-4fad-a5d8-4892e708b389)

- 루트는 비어 있다.
- 각 간선(링크)은 추가될 문자를 키로 가진다.
- 각 정점은 이전 정점의 값 + 간선의 키를 값으로 가진다.
- **해시 테이블**과 **연결 리스트**를 이용하여 구현할 수 있다.

<br />

## JavaScript에서 사용법

```jsx
class Node {
  constructor(value = "") {
    this.value = value;
    this.children = new Map();
  }
}

class Trie {
  constructor() {
    this.root = new Node();
  }
  // 요소 추가
  insert(string) {
    // root부터 탐색 시작
    let currentNode = this.root;

    for (const char of string) {
      // 현재 정점 간선에 char 글자가 없으면
      if (!currentNode.children.has(char)) {
        // 새로운 정점 만들어 추가
        currentNode.children.set(char, new Node(currentNode.value + char));
      }
      // 다음 정점으로 이동
      currentNode = currentNode.children.get(char);
    }
  }

  // 요소 존재 여부
  has(string) {
    // root부터 탐색 시작
    let currentNode = this.root;

    for (const char of string) {
      // 현재 정점 간선에 char 글자가 없으면
      if (!currentNode.children.has(char)) {
        return false;
      }
      // 다음 정점으로 이동
      currentNode = currentNode.children.get(char);
    }

    return true;
  }
}

const trie = new Trie();

trie.insert("cat");
trie.insert("can");

console.log(trie.has("cat")); // true
console.log(trie.has("can")); // true
console.log(trie.has("cap")); // false
```
