# 큐(Queue)

<br />

## 큐

**큐(Queue)** 는 FIFO(First In First Out)라는 개념을 가진 선형 자료구조다. 선형 큐(Linear Queue)와 원형 큐(Circular Queue)가 존재한다.

> **큐**
>
> - 데이터를 집어넣을 수 있는 **선형(linear) 자료형**이다.
> - 먼저 집어넣은 데이터가 먼저 나온다. (**FIFO**)
> - 데이터를 집어넣는 enqueue, 데이터를 추출하는 dequeue 등의 작업을 할 수 있다.
> - **순서대로 처리해야 하는 작업을 임시로 저장해두는 버퍼(buffer)**로서 많이 사용된다.

<br />

## 선형 큐(Linear Queue)

![Image](https://github.com/user-attachments/assets/ec613fed-d393-4769-a3c7-899e1b950f0c)

<br />

**선형 큐 - 배열(Array)로 구현**

```jsx
class Queue {
  constructor() {
    this.queue = [];
    this.front = 0;
    this.rear = 0;
  }

  enqueue(newValue) {
    this.queue[this.rear++] = newValue;
  }

  dequeue() {
    const value = this.queue[this.front];

    delete this.queue[this.front];
    this.front += 1;

    return value;
  }

  peek() {
    return this.queue[this.front];
  }

  size() {
    return this.rear - this.front;
  }
}

const queue = new Queue();
```

<br />

**선형 큐 - 연결 리스트(Linked List)로 구현**

```jsx
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Queue {
  constructor() {
    this.head = null;
    this.tail = null;
    this.size = 0;
  }

  enqueue(newValue) {
    const newNode = new Node(newValue);

    if (this.head === null) {
      this.head = this.tail = newNode;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }

    this.size += 1;
  }

  dequeue() {
    const value = this.head.value;

    this.head = this.head.next;
    this.size -= 1;

    return value;
  }

  peek() {
    return this.head.value;
  }
}

const queue = new Queue();
```

<br />

## 원형 큐(Circular Queue)

원형 큐(Circular Queue)는 Front와 Rear가 이어져 있는 Queue이다.

> 원형 큐는 연결 리스트로 구현했을 때 이점이 없다.

![Image](https://github.com/user-attachments/assets/afc42c12-11cf-4bf4-b3f2-24183b7b4dc1)

<br />

**원형 큐 - 배열(Array)로 구현**

```jsx
class Queue {
  constructor(maxSize) {
    this.maxSize = maxSize;
    this.queue = [];
    this.front = 0;
    this.rear = 0;
    this.size = 0;
  }

  enqueue(newValue) {
    if (this.isFull()) {
      console.log("Queue is full.");
      return;
    }

    this.queue[this.rear] = newValue;
    this.rear = (this.rear + 1) % this.maxSize;
    this.size += 1;
  }

  dequeue() {
    const value = this.queue[this.front];

    delete this.queue[this.front];
    this.front = (this.front + 1) % this.maxSize;
    this.size -= 1;

    return value;
  }

  isFull() {
    return this.size === this.maxSize;
  }

  peek() {
    return this.queue[this.front];
  }
}

const queue = new Queue(4);
```
