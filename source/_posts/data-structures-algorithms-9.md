---
title: Sorting
date: 2020-02-02 15:51:53
tags:
- JavaScript
- Algorithm
---

#### Bubble sort

* 較不效率的 sorting
* space complexity 低

```js
function bubbleSort(array) {
  for (let j = 0; j < array.length - 1; j++) {
    for (let i = 0; i < array.length - j - 1; i++) {
      if (array[i] > array[i + 1]) {
        let temp = array[i]
        array[i] = array[i + 1]
        array[i + 1] = temp
      }
    }
  }
  return array
}
```

(to be continued)

#### Selection sort
#### Insertion sort
#### Merge sort
#### Quick sort

#### Reference
* [https://www.toptal.com/developers/sorting-algorithms](https://www.toptal.com/developers/sorting-algorithms)
