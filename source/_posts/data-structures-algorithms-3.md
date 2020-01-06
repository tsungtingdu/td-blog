---
title: Data structure - array
date: 2020-01-03 14:16:12
tags:
- JavaScript
- Data Structure
---

#### note
* static v.s. dynamic array: 是否佔用有限空間
* Pros
  * fast lookups `O(1)`
  * fast push/pop `O(1)`
  * ordered
* Cons
  * slow inserts `O(n)`
  * slow deletes `O(n)`
  * fixed size (if it's a static array)

#### Create an array
```js
class MyArray {
  constructor() {
    this.length = 0
    this.data = {}
  }

  get(index) {
    return this.data[index]
  }

  push(item) {
    this.data[this.length] = item
    this.length++
    return this.length
  }

  pop() {
    const lastItem = this.data[this.length-1]
    delete this.data[this.length-1]
    this.length--
    return lastItem
  }

  delete(index) {
    const item = this.data[index]
    this.shiftItems(index)
    return  item
  }

  shiftItems(index) {
    for (let i = index; i < this.length-1; i++){
      this.data[i] = this.data[i+1]
    }
    delete this.data[this.length-1]
    this.length--
  }
}
```