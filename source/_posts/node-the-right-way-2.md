---
title: About Node.js (2)
date: 2020-01-05 16:15:49
tags:
- Node.js
- JavaScript
---


#### Wrapping function

平常我們在寫 module 的時候像是
```js
function calculate(number) {
  //xxx
}

module.exports = calculate
```
但其實 Node.js 在外層包了一個 function
```js
(function (exports, require, module, __filename, __dirname){  
  function calculate(number) {
    //xxx
  }
  module.exports = calculate

 })
```
在 Node.js 當中的任何一個檔案裡面可以用 console.log 來查看 `exports`, `require`, `module`, `__filename`, `__dirname` 這些變數

#### Extent EventEmitter

假如目前有兩個檔案
```js
// app.js
const EventEmitter = require('events')
const emitter = new EventEmitter()
const log = require('./logger.js')

emitter.on('messageLogged', data => {
  console.log('Listener caleed ', data)
})

log('message')
```
and 
```js
// logger.js
const EventEmitter = require('events')
const emitter = new EventEmitter()
let url = 'https://tsungtingdu.github.io/td-blog/'

function log(message) {
  console.log(message)
  emitter.emit('meesageLogged', {
    id: 1,
    url: url
  })
}
```
如果啟動 `node app.js` 後，原本期待可以接收到從 logger.js emit 出來的 event，但結果不行。需要改成
```js
// app.js
const Logger = require('./logger.js')
const logger = new Logger()

logger.on('messageLogged', e => {
  console.log(e)
})
```
and
```js
// logger.js
const EventEmitter = require('events')
let url = 'https://tsungtingdu.github.io/td-blog/'

class Logger extends EventEmitter {
  log(message) {
    console.log(message)
    this.emit('messageLogged', {
      id: 1,
      url: url
    })
  }
}
module.exports = Logger
```