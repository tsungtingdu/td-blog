---
title: Data structure - linked list
date: 2020-01-06 16:46:53
tags:
- JavaScript
- Data Structure
---

#### note

* With value & pointer
* There are a head & a tail (point to null) in a linked list
* There are singly & doubly linked list
* Pros
  * Fest insertion/deletion
  * Ordered
  * Flexible size (compare to static array)
  * prepend `O(1)`
  * append `O(1)`
* Cons
  * slow lookup
  * need more memory
  * loopup `O(n)`
  * insert `O(n)`
  * delete `O(n)`
* garbage collection
* Ref: [https://visualgo.net/en](https://visualgo.net/en)

#### Create a singly linked list
```js
class Node {
  constructor(value) {
    this.value = value
    this.next = null
  }
}

class LinkedList {
  constructor(value) {
    this.head = {
      value: value,
      next: null,
    }
    this.tail = this.head
    this.length = 1
  }

  append(value) {
    const newNode = new Node(value)
    this.tail.next = newNode
    this.tail = newNode
    this.length++
    return this
  }

  prepend(value) {
    const newNode = new Node(value)
    newNode.next = this.head
    this.head = newNode
    this.length++
    return this
  }

  printList() {
    const array = []
    let currentNode = this.head
    while (currentNode !== null) {
      array.push(currentNode.value)
      currentNode = currentNode.next
    }
    console.log(array)
    return array
  }

  insert(index, value) {
    if (index >= this.length) {
      return this.append(value)
    } else if (index === 0) {
      return this.prepend(value)
    } else {
      const newNode = new Node(value)
      const leader = this.traverseToIndex(index - 1)
      const holdingPointer = leader.next
      leader.next = newNode
      newNode.next = holdingPointer
      this.length++
      return this
    }
  }

  remove(index) {
    if (index >= this.length - 1) {
      index = this.length - 1
      const leader = this.traverseToIndex(index - 1)
      leader.next = null
      this.tail = leader
    } else if (index <= 0) {
      this.head = this.head.next
    } else {
      const leader = this.traverseToIndex(index - 1)
      leader.next = leader.next.next
    }
    this.length--
    return this
  }

  traverseToIndex(index) {
    let counter = 0
    let currentNode = this.head
    while (counter !== index) {
      currentNode = currentNode.next
      counter++
    }
    return currentNode
  }
}
```

#### Create a doubly linked list
```js
class Node {
  constructor(value) {
    this.value = value
    this.next = null
    this.prev = null
  }
}
class DoublyLinkedList {
  constructor(value) {
    this.head = {
      value: value,
      next: null,
      prev: null
    }
    this.tail = this.head
    this.length = 1
  }

  append(value) {
    const newNode = new Node(value)
    newNode.prev = this.tail
    this.tail.next = newNode
    this.tail = newNode
    this.length++
    return this
  }

  prepend(value) {
    const newNode = new Node(value)
    newNode.next = this.head
    this.head.prev = newNode
    this.head = newNode
    this.head.prev = null
    this.length++
    return this
  }

  printList() {
    const array = []
    let currentNode = this.head
    while (currentNode !== null) {
      array.push(currentNode.value)
      currentNode = currentNode.next
    }
    console.log(array)
    return array
  }

  insert(index, value) {
    if (index >= this.length) {
      return this.append(value)
    } else if (index <= 0) {
      return this.prepend(value)
    } else {
      const newNode = new Node(value)
      const leader = this.traverseToIndex(index - 1)
      const holdingPointer = leader.next
      leader.next = newNode
      newNode.prev = leader
      newNode.next = holdingPointer
      this.length++
      return this
    }
  }

  remove(index) {
    if (index >= this.length - 1) {
      index = this.length - 1
      const leader = this.traverseToIndex(index - 1)
      leader.next = null
      this.tail = leader
    } else if (index <= 0) {
      this.head.prev = null
      this.head = this.head.next
    } else {
      const leader = this.traverseToIndex(index - 1)
      leader.next.next.prev = leader
      leader.next = leader.next.next
    }
    this.length--
    return this
  }

  traverseToIndex(index) {
    let counter = 0
    let currentNode = this.head
    while (counter !== index) {
      currentNode = currentNode.next
      counter++
    }
    return currentNode
  }
}
```