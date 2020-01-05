---
title: Data structure - hash
date: 2020-01-05 17:30:09
tags:
---

#### note
* Pros
  * 和 array 比起來，hash table 的優勢在 `insert` 和 `delete` ，都是 O(1)，但是如果遇到 collisions 的狀況，就會可能變成 O(n)
  * improve time complexity
* Cons
  * unordered
  * slow key iteration
  * increase space complexity

#### Create an array
```js
class HashTable {
  constructor(size) {
    this.data = new Array(size)
  }

  // 利用 hash 建立位址
  _hash(key) {
    let hash = 0
    for (let i = 0; i < key.length; i++) {
      hash = (hash + key.charCodeAt(i) * i) % this.data.length
    }
    return hash
  }

  set(key, value) {
    let address = this._hash(key)

    if (!this.data[address]) {
      this.data[address] = []
    }
    this.data[address].push([key, value])
    return this.data
  }

  get(key) {
    let address = this._hash(key)
    const currentBucket = this.data[address]

    if (currentBucket) {
      // deal with collisions
      for (let i = 0; i < currentBucket.length; i++) {
        if (currentBucket[i][0] === key) {
          return currentBucket[i][1]
        }
      }
    }
    return undefined
  }

  keys() {
    const keyArray = []
    for (let i = 0; i < this.data.length; i++) {
      if (this.data[i]) {
        keyArray.push(this.data[i][0][0])
      }
    }
    return keyArray
  }
}
```

使用 hash table
```js
const myHashTable = new HashTable(50)
myHashTable.set('apple', 100)
myHashTable.set('bird', 200)
myHashTable.set('cider', 300)
console.log(myHashTable.data)
```
會得到
```js
[ <14 empty items>,
  [ [ 'apple', 100 ], [ 'cider', 300 ] ],   // collision here
  <18 empty items>,
  [ [ 'bird', 200 ] ],
  <16 empty items> ]
```