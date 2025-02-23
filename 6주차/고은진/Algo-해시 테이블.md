# 해시 테이블(Hash Table)

<br />

## 해시 테이블이란?

**해시 테이블(Hash Table)** 이란 키와 값을 받아 키를 해싱(Hashing)하여 나온 index에 값을 저장하는 선형 자료구조이다.

삽입은 O(1)이며 키를 알고 있다면 삭제, 탐색도 O(1)로 수행한다.

![Image](https://github.com/user-attachments/assets/f67025e4-a7c3-4f65-b39d-ccebbbd88d1c)

<br />

## 해시 함수란?

**해시 함수**는 입력받은 값을 특정 범위 내 숫자로 변경하는 함수다.

<br />

## 해시 충돌(Hash Collision)을 해결할 수 있는 방법

- **선형 탐사법**
  충돌 발생 시 옆으로 한 칸 이동하는 방법
- **제곱 탐사법**
  충돌 발생 시 충돌이 발생한 횟수의 제곱만큼 옆으로 이동하는 방법
- **이중 해싱**
  충돌 발생 시 다른 해시 함수를 이용하는 방법
- **분리 연결법**
  버킷의 값을 연결 리스트로 사용하여 충돌 발생 시 리스트에 값을 추가하는 방법

<br />

## 해시 테이블은 언제 사용하는 것이 좋은가?

빠르게 값을 찾아야 하는 경우 해시 테이블을 사용하는 것이 좋다.

<br />

## JavaScript에서 사용하기

**배열(Array)로 구현**

```jsx
const hashTable = [];

hashTable["key1"] = 100;
hashTable["key2"] = "David";

console.log(hashTable["key1"]); // 100

delete hashTable["key2"];

console.log(hashTable["key2"]); // undefined
```

<br />

**객체(Object)로 구현**

```jsx
const hashTable = {};

hashTable["key1"] = 100;
hashTable["key2"] = "David";

console.log(hashTable["key1"]); // 100

delete hashTable["key2"];

console.log(hashTable["key2"]); // undefined
```

<br />

**Map 객체로 구현**

```jsx
const hashTable = new Map();

hashTable.set("key1", 100);
hashTable.set("key2", "David");

console.log(hashTable.get("key1")); // 100

const object = { name: "John" };

hashTable.set(object, "A1"); // Map은 Object도 Key로 쓸 수 있다.

hashTable.delete(object);

console.log(hashTable.keys()); // { 'key1', 'key2' }

console.log(hashTable.values()); // { 100, 'David' }

hashTable.clear();

console.log(hashTable.values()); // {}
```

<br />

**Set 객체로 구현**

```jsx
const hashTable = new Set();

hashTable.add("key1"); // Key와 Value가 동일하게 들어간다.
hashTable.add("key2");

console.log(hashTable.has("key1")); // true
console.log(hashTable.has("key3")); // false

hashTable.delete("key2");

console.log(hashTable.size); // 1

table.clear();

console.log(hashTable.size); // 0
```
