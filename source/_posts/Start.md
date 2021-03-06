---
title: 2019 年回顧 (1/2)
date: 2019-12-31 16:51:33
tags:
- Reviews
---

在 2019 年的最後一天，學會用 Hexo 架了一個自己的 blog。這已經不知道是我第幾次開 blog 了，不過這次選用 Hexo 的原因，主要是希望能夠用 markdown 來撰寫，另一方面，文章可以同步在本地端以及 Github 上有備份

期待 2020 以及未來的日子，可以在這裡勤快地記錄下我的學習，以及大大小小我想要紀錄的事情

既然是 2019 年最後一天，不如就先來寫寫個回顧吧

### 工作
#### 建立助教團隊

2018 年結束在新加坡的 bootcamp 後，我的工作重心就轉移到台灣的線上課程上，主要負責助教團隊的管理：從招募、培訓，到工作管理、成本控管等任務。目前助教團隊超過 30 人，一路以來有超過 50 人次擔任過助教

#### 打造助教團隊管理系統

在沒有技術開發團隊的支援下，我和 Walter 利用手邊有的工具加上自學，打造出團隊管理系統，讓助教團隊能夠提供學生及時的協助，滿足學習教練團隊所預期的課程體驗

系統主要包含 Admin dashboard、TA dashboard，以及成本預算管理等三個操作介面/工具

自動化功能包含
* 助教排班系統
* 工作分類（根據課程班級、週數、作業標籤判斷是否需要處理）
* 工作分配
* 提醒通知（排班通知、學生回覆通知、工作逾期通知等）
* 資料比對計算

主要使用到
* Python - 爬蟲與資料處理程式（主要由 Walter 負責）
* Google App Script
  * 負責資料呈現與運算
  * 執行 Cron job - 定期執行特定程式、打 API 接收資訊
* Ruby on Rails - 爬蟲程式與 API server

其他像是
* Slack webhook & API
* Bit.ly API
* Google Sheets query function (similar to SQL) 等

#### 導入 Freshdesk

協助團隊導入 Freshdesk 作為客服系統，取代原先的 inbox。經歷
* 研究並測試不同方案
* 設計並主持團隊測試 session，共同決定最後採用的解決方案
* 設計資料搬遷流程
* 設計使用規範、主持 training session

等不同階段，最後成功導入系統，成為團隊日常營運的一部分

#### 定義 Product Market Fit

最初要協助團隊重新定義產品的 product market fit，做了一些研究與使用者調查後，回歸到原先的 product roadmap 上，先共同定義出產品最重要的 metrics，以及討論針對特定 problem base 的 new ideas。最後發起 product meeting，讓團隊中每個人都能參與產品發展的討論，並有更高的視角去觀察與思考產品的未來

對我來說這是一個很特別的任務，在團隊中沒有人知道該怎麼做，因此需要自己去定義問題並尋找出路。一路上常常質問自己「到底有沒有問對問題？」，研究與討論過程中也看到許多公司對於產品的想法，但要如何將那些想法應用在自家的產品上，中間需要跟團隊成員有很多的討論、意見交流，並凝聚共識

#### 不同的工作型態: remote & part-time

因為種種原因，2019 三月底開始就轉為 part-time 工作者，這時候才發現時間管理的重要性。變成 part-time 之後，會更為認真的去思考工作的安排與時間投入，而我總是會投入許多的心力在工作上，不知不覺工作的比例就會超過原先對於 part-time 的設想。要如何「設下工作的邊界」、「提高工作效率」，都是未來需要思考與練習的課題

另外，也工作的重心與對象都在台灣，因此我不知不覺就成了一位 remote 工作者，每天在不同的咖啡店、圖書館等地方工作，也有機會去探索城市的不同角落，生活也多了些樂趣。但是同時會失去另一部分的方便性，譬如常常要去想哪裡有網路、電力、水、廁所等等，跑來跑去的過程中，其實也會花費掉不少的時間

跟在辦公室的工作者比起來，remote 工作者接收資訊的效率是遠遠落後。舉例來說，在一個會議上，除了語音資訊之外，其實也可以透過與會者的表情、肢體語言來收集到更多資訊與細節，更不用說會議前與會議後的小聊，這些都是 remote 工作者很難參與到的地方

***
### 學習
#### Web Dev (JavaScript & Node.js)
其實今年初才認真開始學 JavaScript（以前都是寫 Ruby），年中開始加入自家的 web dev 課程，一路上完第三學期、第四學期，並完成畢業專案通過口試

雖然之前學過 Ruby on Rails，但是學 JavaScript & Node.js 後，對於 web dev 有了重新的認識，覺得非常有趣，期待 2020 年能夠有更深入的學習

#### Machine Learning

一開始本來只是想自己學一下而已，後來因為揪團參加iT邦幫忙鐵人賽，因此就把剛剛開始學的這個主題拿來當參賽題目（結果當然是非常痛苦）

雖然後來沒有時間繼續深入學習 Machine Learning，不過過程中為了學 Python，花了不到一天的時間看完語法後，就直接上 Leetcode 玩，效果好像還不錯

[繼續閱讀下篇：2019 年回顧 (2/2)](/td-blog/2020/01/01/start-2/)