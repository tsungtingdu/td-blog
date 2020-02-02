---
title: Algorithms - Recursion
date: 2020-02-02 11:35:55
tags:
- JavaScript
- Algorithm
---

#### note

```js
let counter = 0
function inception() {
  if (counter > 3) {
    return 'done'
  }
  counter++
  inception()
}

inception()
```
在執行上方的程式碼的時候，會不斷的把 `inception()` 放入 call stack 直到 counter = 4，此時 return value = 'done'。之後，程式會 pop out call stack 裡面的 `inception()`，此時這些 `inception()` 的 return value 為 undefined

若要回傳 `done`，則需要在 inception function 的最後加上 `return inception()` 

```js
let counter = 0
function inception() {
  if (counter > 3) {
    return 'done'
  }
  counter++
  return inception()  // 在此行加上 return
}

inception()
```

Hints
1. identify base case
2. identify the recursive case
3. return when needed

#### Recursion v.s. Iterative

* pros of recursion
  * DRY
  * Readability
  * better for `merge sort`, `quick sort`, `tree traversal`, `graph traversal`
* cons
  * large stack

p.s. "Tail call Opimisation" can solve the problem of large stack

#### examples

Fibonacci with recursion
```js
// O(2^n)
function fibonacciRecursion(n) {
  if (n < 2) {
    return n
  } else {
    value = fibonacciRecursion(n - 1) + fibonacciRecursion(n - 2)
    return value
  }
}
```
Fibonacci with iterative
```js
// O(n)
function fibonacciIterative(n) {
  let arr = [0, 1]
  for (let i = 2; i < n + 1; i++) {
    arr.push(arr[i - 2] + arr[i - 1])
  }
  return arr[n]
}
```