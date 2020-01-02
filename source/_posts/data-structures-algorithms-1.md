---
title: Data Structure & Algorithms - Big O
date: 2020-01-02 21:28:02
tags:
---

## About Big O

#### Note

* 好的程式碼需要 **Readable** & **Scalable**
* 要知道程式是否 scalable，可以從 **time complexity** & **space complexity** 來衡量
* Readibility, time complexity, space complexity 三者會互相 trade off
* 要計算 runtime，可以實際去計算一個程式的執行時間，但這會因不同的電腦的 CPU 有所差別。因此實務上，會去計算「會跑過多少行程式碼」，用 Big O 來說明程式的 time complexity
* Rules for calculating Big O:
    * Worst Case
    * Remove constant
    * Different input
    * Drop non-dominants

#### Examples

O(n)
```js
const array = ['a', 'b', 'c', 'd', 'e']

function findKeyWord (array) {
  for (let i = 0; i < array.length-1; i++) {
    if (array[i] === 'a') {
      console.log('Found a')
    }
  }
}

findKeyWord(array) //O(n)
```
O(1)
```js
const array = ['a', 'b', 'c', 'd', 'e']

function printFirstItem (array) {
  console.log(array[0])
}

printFirstItem(array) //O(1)
```
O(n^2)
```js
const array = ['a', 'b', 'c', 'd', 'e']

function logAllPairs (array) {
  for (let i = 0; i < array.lenght-1; i++) {
    for (let j = 0; j < array.lenght-1; j++) {
      console.log(array[i], array[j])
    }
  }
}

ogAllPairs(array) //O(n^2)
```
O(log n)
```js
const num = 31415926

function sumOfDigits (n) {
  let sum = 0;
  while (n > 0) {
    sum += n % 10
    n = Math.floor(n/10)
  }
}

sumOfDigits(num) //O(log n)
```
O(a+b)
```js
const a = ['a', 'b', 'c', 'd', 'e']
const b = ['f', 'g', 'h', 'i', 'j']

function loopTwoArray (array1, array2) {
  array1.forEach( i => console.log(i) )
  array2.forEach( i => console.log(i) )
}

loopTwoArray(a,b) //O(a+b)
```


#### Reference
* [Big-O Cheat Sheet](https://www.bigocheatsheet.com/)