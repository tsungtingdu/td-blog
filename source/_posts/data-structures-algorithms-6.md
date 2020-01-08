---
title: Data structure - stacks & queues
date: 2020-01-08 11:47:00
tags:
- JavaScript
- Data Structure
---

#### note
* Pros
  * fast operation (insert/delete the first/last item)
  * fast pekk
* Cons
  * slow lookup
* 用 array 建立 queue 會需要 `O(n)` (need to shift index)

 #### Create a stack using linked list
 ```js
class Node {
  constructor(value) {
    this.value = value
    this.next = null
  }
}
class Stack {
  constructor() {
    this.top = null
    this.bottom = null
    this.length = 0
  }
  peek() {
    return this.top
  }
  push(value) {
    const newNdoe = new Node(value)
    if (this.length === 0) {
      this.top = newNdoe
      this.bottom = newNdoe
      this.length++
    } else {
      newNdoe.next = this.top
      this.top = newNdoe
      this.length++
    }
    return this
  }
  pop() {
    if (!this.top) {
      return null
    }
    this.top = this.top.next
    this.length--
    if (this.length === 0) {
      this.bottom = null
    }
    return this
  }
}
 ```
#### Create a stack using array
 ```js
class Node {
  constructor(value) {
    this.value = value
    this.next = null
  }
}
class Stack {
  constructor() {
    this.array = []
  }
  peek() {
    if (this.array.length === 0) {
      return null
    } else {
      return this.array[this.array.length - 1]
    }
  }
  push(value) {
    this.array.push(value)
    return this
  }
  pop() {
    if (this.array.length === 0) {
      return null
    } else {
      this.array.pop()
      return this
    }
  }
}
 ```

####  Create a queue using linked list
```js
class Node {
  constructor(value) {
    this.value = value
    this.next = null
  }
}
class Queue {
  constructor() {
    this.first = null
    this.last = null
    this.length = 0
  }
  peek() {
    return this.fist
  }
  enqueue(value) {
    const newNode = new Node(value)
    if (this.length === 0) {
      this.first = newNode
      this.last = newNode
    } else {
      this.last.next = newNode
      this.last = newNode
    }
    this.length++
    return this
  }
  dequeue() {
    if (this.length === 0) {
      return null
    } else if (this.length === 1) {
      this.first = this.first.next
      this.last = null
      this.length--
    } else {
      this.first = this.first.next
      this.length--
    }
    return this
  }
}
```
 ***
 chanllenge: create a queue using stack?