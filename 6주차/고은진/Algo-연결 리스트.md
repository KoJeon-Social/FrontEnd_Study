# 연결 리스트(Linked List)

<br />

## 연결 리스트란?

**연결 리스트** 는 각 요소를 포인터로 연결하여 관리하는 선형 자료구조이다.

각 요소를 노드라고 부르며 데이터 영역과 포인터 영역으로 구성된다.

<br />

## 연결 리스트의 특징

- 메모리가 허용하는 한 요소를 제한 없이 추가할 수 있다.
- 탐색은 O(n)이 소요된다.
- 요소를 추가하거나 제거할 때 O(1)이 소요된다.
- 단일 연결 리스트(Singly Linked List), 이중 연결 리스트(Doubly Linked List), 단순 원형 연결 리스트(Circular Linked List)가 존재한다.

<br />

## 단일 연결 리스트(Singly Linked List)

![Image](https://github.com/user-attachments/assets/c47acf55-3c5e-4b7f-b108-90333d0ee66d)

> Head에서 Tail까지 단방향으로 이어지는 연결 리스트이며 가장 단순한 형태인 연결 리스트이다.

```jsx
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  find(value) {
    let currNode = this.head;

    while (currNode.value !== value) {
      currNode = currNode.next;
    }

    return currNode;
  }

  append(newValue) {
    const newNode = new Node(newValue);

    if (this.head === null) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }
  }

  insert(node, newValue) {
    const newNode = new Node(newValue);

    newNode.next = node.next;
    node.next = newNode;
  }

  remove(value) {
    let prevNode = this.head;

    while (prevNode.next.value !== value) {
      prevNode = prevNode.next;
    }

    if (prevNode.next !== null) {
      prevNode.next = prevNode.next.next;
    }
  }

  display() {
    let currNode = this.head;
    let displayString = "[";

    while (currNode != null) {
      displayString += `${currNode.value}, `;
      currNode = currNode.next;
    }

    displayString = displayString.substring(0, displayString.length - 2);
    displayString += "]";

    console.log(displayString);
  }
}

const linkedList = new SinglyLinkedList();
```

<br />

## 이중 연결 리스트(Doubly Linked List)

![Image](https://github.com/user-attachments/assets/5e258c26-dc4b-452a-9dd9-839d86be90df)

> 양방향으로 이어지는 연결 리스트다. 이중 연결 리스트는 포인터 변수가 하나 더 추가되기 때문에 단일 연결 리스트보다 자료구조의 크기가 더 크다.

<br />

## 단순 원형 연결 리스트(Circular Linked List)

![Image](https://github.com/user-attachments/assets/c1fc6b9a-61e3-4c1d-9947-2759c1da7c25)

> 단일 혹은 이중 연결 리스트에서 Tail이 Head로 연결되는 메모리를 아껴쓸 수 있다. 원형 큐 등을 만들 때도 사용한다.

<br />

## 배열과의 차이점

|           자료구조           | 요소 추가 또는 삭제 |                          요소 찾기                          |
| :--------------------------: | :-----------------: | :---------------------------------------------------------: |
|       **배열(Array)**        |        O(n)         | O(n) <br /> (만약 원하는 원소의 index를 알고 있다면 O(1)) |
| **연결 리스트(Linked List)** |        O(1)         |                            O(n)                             |
