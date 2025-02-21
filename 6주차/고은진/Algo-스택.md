# 스택(Stack)

<br />

## 스택이란?

**스택(Stack)** 은 LIFO(Last In First Out)이라는 개념을 가진 선형 자료구조이다.

![Image](https://github.com/user-attachments/assets/7e8dd7ac-3dc9-4c4c-930a-003be695132e)

> **스택**
>
>- 데이터를 집어넣을 수 있는 **선형(Linear) 자료형**이다.
>- 나중에 집어넣은 데이터가 먼저 나온다. (**LIFO**)
>- 데이터를 집어넣는 push, 데이터를 추출하는 pop, 맨 나중에 집어넣은 데이터를 확인하는 peek 등의 작업을 할 수 있다.
>- 서로 관계가 있는 여러 작업을 연달아 수행하면서 **이전의 작업 내용을 저장해 둘 필요가 있을 때** 사용된다.


<br />

## JavaScript에서 사용하기

**배열(Array)로 구현**

```jsx
const stack = [];

// Push
stack.push(1);
stack.push(2);
stack.push(3);

console.log(stack); // [1, 2, 3]

// Pop
stack.pop();

console.log(stack); // [1, 2]
```

<br />

**연결 리스트(Linked List)로 구현**

```jsx
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Stack {
  constructor() {
    this.top = null;
    this.size = 0;
  }

  push(value) {
    const node = new Node(value);

    node.next = this.top;
    this.top = node;
    this.size += 1;
  }

  pop() {
    const value = this.top.value;

    this.top = this.top.next;
    this.size -= 1;

    return value;
  }

  size() {
    return this.size;
  }
}

const stack = new Stack();
```
