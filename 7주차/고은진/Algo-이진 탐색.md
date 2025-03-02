# 이진 탐색(Binary Search)

<br />

## 이진 탐색이란?

**이진 탐색(Binary Search)** 이란 정렬 되어있는 요소들을 반씩 제외하며 찾는 알고리즘이다.

<br />

## 이진 탐색의 특징

- 반드시 정렬이 되어 있어야 사용할 수 있다.
- 배열 혹은 이진 트리를 이용하여 구현할 수 있다.
- O(log n)의 시간복잡도인 만큼 상당히 빠르다.

<br />

## 이진 탐색 트리의 문제점

- 최악의 경우 한쪽으로 편향된 트리가 될 수 있다.
- 그런 경우 순차 탐색과 동일한 시간복잡도를 가진다.
- 이를 해결하기 위해 다음과 같은 자료구조를 이용할 수 있다.
  - AVL 트리
  - 레드-블랙 트리

<br />

## JavaScript에서 사용하는 방법

**배열(Array)로 구현**

```jsx
function binarySearch(array, findValue) {
  let left = 0;
  let right = array.length - 1;
  let mid = Math.floor((left + right) / 2);

  while (left <= right) {
    if (array[mid] === findValue) {
      return mid;
    }

    array[mid] < findValue ? (left = mid + 1) : (right = mid - 1);
    mid = Math.floor((left + right) / 2);
  }

  return -1;
}

const array = [1, 2, 5, 124, 400, 599, 1004, 2876, 8725];

console.log(binarySearch(array, 2876)); // 7
console.log(binarySearch(array, 1)); // 0
console.log(binarySearch(array, 500)); // -1
console.log(binarySearch(array, 2)); // 1
console.log(binarySearch(array, 1004)); // 6
```

<br />

**트리(Tree)로 구현**

```jsx
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  insert(value) {
    const newNode = new Node(value);

    if (this.root === null) {
      this.root = newNode;
      return;
    }

    let currentNode = this.root;

    while (currentNode !== null) {
      if (currentNode.value < value) {
        if (currentNode.right === null) {
          currentNode.right = newNode;
          break;
        }

        currentNode = currentNode.right;
      } else {
        if (currentNode.left === null) {
          currentNode.left = newNode;
          break;
        }

        currentNode = currentNode.left;
      }
    }
  }

  has(value) {
    let currentNode = this.root;

    while (currentNode !== null) {
      if (currentNode.value === value) {
        return true;
      }

      if (currentNode.value < value) {
        currentNode = currentNode.right;
      } else {
        currentNode = currentNode.left;
      }
    }

    return false;
  }
}

const tree = new BinarySearchTree();

tree.insert(5);
tree.insert(4);
tree.insert(7);
tree.insert(8);
tree.insert(5);
tree.insert(6);
tree.insert(2);

console.log(tree.has(8)); // true
console.log(tree.has(1)); // false
```
