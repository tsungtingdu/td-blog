---
title: About Node.js (1)
date: 2020-01-04 12:40:54
tags:
---

#### note

* Node.js 的設計是適合 I/O intensive 的工作任務，而非 CPU intensive
* I/O bound
  * client-side (GUI, web, mobile, etc..)
  * server-side (web, REST, Ajax, HTTP, and messaging, IPC, monitoring, test, build, distributed, etc.. )
* Thinking beyond the web - Node.js 可以用來處理很多工作，譬如 IoT
* Many middleware tasks are I/O-bound (just like client-side scripting and databases)
* About Node.js
  * event loop
  * single-threaded & highly parallel
  * non-blocking (callback)
  * backwardism
* Global objects
* Important modules in Node.js
  * EventEmitter
  * Buffer
  * Stream
  * Child Process
***
#### Events (& EventEmitter)

Node.js 的設計重點為事件驅動，其中一個最重要的 module 就是 Event。許多 Node.js 裡面的 module 都是繼承/來自於Event 中的 class "EventEmitter"。舉例來說，如果去看 HTTP module 的文件，可以看到
```
Class: http.ClientRequest
Extends: <Stream>
```
然後點進 Stream 會看到
```
All streams are instances of EventEmitter.
```

另外也可以在不同的 module 當中，看到他們會產生 (emit) 的 event 類型

EventEmitter 有幾個常見的方法像是
* emitter.on(eventName, listener)
* emitter.once(eventName, listener)

等等

#### Buffer

> *Pure JavaScript is Unicode friendly, but it is not so for binary data. While dealing with TCP streams or the file system, it's necessary to handle octet streams. Node provides Buffer class which provides instances to store raw data similar to an array of integers but corresponds to a raw memory allocation outside the V8 heap.*

簡單來說，原本的 JavaScript 只能處理 Unicode (string) data，不擅長處理 binary data。但在 TCP 或 file system (fs) 都是 binary data，因此 Node.js 引入了 buffer 來負責處理 binary data stream。

所以 buffer 是 binary data，在 V8 heap 之外由 Buffer class 來管理。另外，Buffer 是global class，因此使用的時候不需要 require buffer module

Example
```js
let buf = new Buffer.from('This is a book')
console.log(buf)
```
會得到
```
<Buffer 54 68 69 73 20 69 73 20 61 20 62 6f 6f 6b>
```
如果把剛剛的 buf 轉成 json，轉成 buffer 後再轉成字串
```js
let json = JSON.stringify(buf)
let buf2 = new Buffer.from(JSON.parse(json).data)
console.log(buf2.toString())
```
會得到
```
This is a book
```

#### Stream

剛剛提到，stream 是 EventEmitter 的 instance，而許多 Node.js module 則是 stream 的 instance，譬如 `process.stdout`, `http.clientRequest` 等等

stream 是一種資料處理方法，讓我們在讀取大型資料的時候，能夠將資料將資料變成多個連續的 chunk ，分批寫入記憶體當中，以免記憶體被大型資料一口氣佔滿。因此使用 stream 的好處是
* 提升記憶體的使用效率
* 提升時間效率，在檔案全部讀取完畢之前，就能先開始處理先到的 data chunk

stream 主要有以下四種
* Writable streams
* Readable streams 
* Duplex streams (可讀可寫)
* Transform streams

以及四種主要的 events
* data - 當有 data 可以讀取時
* end - 沒有數據可讀時
* error
* finish - 所有數據已經被寫入時

#### Child Process

Node.js 的特色是 single-thread，但是如果有需要也可以額外開出 stread。譬如在 app.js 當中用 spawn 開啟一個 child process

```js
// app.js
const childProcess = spawn('node', ['app2.js'])
```
因此用 `node app.js` 啟動 server 時，同步也會執行 `node app2.js`

#### Others
  * arrow functions have another big advantage over their ancestral counterparts: they do not create a new scope for **this**

***
#### Reference
* [What do the terms “CPU bound” and “I/O bound” mean?](https://stackoverflow.com/questions/868568/what-do-the-terms-cpu-bound-and-i-o-bound-mean)
* [I/O-bound vs CPU-bound in Node.js](https://bytearcher.com/articles/io-vs-cpu-bound/)
* [Node’s Streams](https://jscomplete.com/learn/node-beyond-basics#streams-101)
* [Node.js Child Processes: Everything you need to know](https://www.freecodecamp.org/news/node-js-child-processes-everything-you-need-to-know-e69498fe970a/)
* [Node.js v13.5.0 APIs](https://nodejs.org/dist/latest-v13.x/docs/api/)