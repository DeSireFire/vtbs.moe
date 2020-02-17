<h1 align="center">
  <img src="./assets/dd-left.png" width=24>
  vtbs.moe
  <img src="./assets/dd-right.png" width=24>
</h1>

<h3 align="center">
  VTBs on bilibili - B站虚拟主播统计网站
</h3>

<p align="center">
  <a href="https://github.com/dd-center/vtbs.moe/commits/master">
    <img src="https://img.shields.io/github/commit-activity/w/dd-center/vtbs.moe.svg?color=green">
  </a>
  <a href="https://github.com/dd-center/vtbs.moe/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/dd-center/vtbs.moe.svg">
  </a>
  <br>
  <a href="https://vtbs.moe/">
    <img src="https://img.shields.io/endpoint.svg?url=https://api.vtbs.moe/endpoint/vtbs">
  </a>
  <a href="https://vtbs.moe/live">
    <img src="https://img.shields.io/endpoint.svg?url=https://api.vtbs.moe/endpoint/live">
  </a>
  <a href="https://vtbs.moe/macro">
    <img src="https://img.shields.io/endpoint.svg?url=https://api.vtbs.moe/endpoint/guardNum">
  </a>
  <a href="https://vtbs.moe/macro">
    <img src="https://img.shields.io/endpoint.svg?url=https://api.vtbs.moe/endpoint/onlineSum">
  </a>
</p>

你好呀→\_→

欢迎来到 <https://vtbs.moe> 的 Github 项目主页

前后端包括数据库都在这个 repository

## 介绍

这是我自娱自乐做出来的 Bilibili 虚拟主播状态记录页面 [vtbs.moe](https://vtbs.moe/)

<img alt="demo" src="./assets/demo.png" width="420" align="right" style="max-width: 50%">

网站用到的部分开源软件:

* 前端
  * 框架: [Vue.js](https://vuejs.org)
    * [Vue CLI](https://cli.vuejs.org/)
    * [Vuex](https://vuex.vuejs.org/)
  * 组件库: [Element](https://element.eleme.cn/)
  * 图表: [ECharts](https://echarts.baidu.com)
    * [v-charts](https://v-charts.js.org)
* 后端
  * 数据库: [level](https://github.com/Level/level)
  * 数据采集: [Bili-api](https://github.com/simon300000/bili-api)
  * 前后端API通讯: [socket.io](https://socket.io)
  * Open JSON API: [koa](https://koajs.com)
  * 万能的: [Node.js](https://nodejs.org/zh-cn/)

## Open API

vtbs.moe does provide some public APIs. Please do not abuse.

### V1 (JSON)

​	Simple JSON API.

* #### vtbs <https://api.vtbs.moe/v1/vtbs>

  => Array, `[...{mid, note}]`

  Return list of vtbs, without any further information.

  **Example:** <https://api.vtbs.moe/v1/vtbs>

  ```json
  [{
      "mid": 197,
      "uuid": "948ae126-061d-5245-a280-82423b5a5b7b"
    },
    {
      "mid": 4052,
      "uuid": "502bb1fb-5c01-57f7-bf63-315903559483"
    },
    {
      "mid": 5730,
      "uuid": "ffec77db-17ec-5e10-a809-68bc4d3f7a78"
    },
    ...
  ]
  ```
  

  Keys:

  * mid: Number

    The numbered user ID, appeared after <https://space.bilibili.com/>.

  * note: Array

    Just some Note...

* #### info <https://api.vtbs.moe/v1/info>

  => Array, `[...{mid, uname, …}]`

  Return records of all vtbs.

  **Example:** <https://api.vtbs.moe/v1/info>

  ```json
  [{
      "mid": 1576121,
      "uname": "帕里_Paryi",
      "video": 55,
      "roomid": 4895312,
      "sign": "我是paryipro的画师paryi~中国朋友们好~请大家关注我~paryi审核群：439902287",
      "notice": "",
      "face": "http://i2.hdslb.com/bfs/face/0f1f65edca3d354a974edb7a6bec01646bcfa4db.jpg",
      "rise": 1302,
      "topPhoto": "http://i0.hdslb.com/bfs/space/81a39f45e49364646274f6e6d4f406d18fdb6afd.png",
      "archiveView": 2691646,
      "follower": 94667,
      "liveStatus": 0,
      "recordNum": 958,
      "guardNum": 22,
      "liveNum": 1100,
      "lastLive": {
        "online": 121883,
        "time": 1560088457424
      },
      "averageLive": 42276996.14747928,
      "weekLive": 45900000,
      "guardChange": 270,
      "guardType": [0, 0, 22],
      "areaRank": 1000,
      "online": 0,
      "title": "b限定】明日方舟",
      "time": 1560102857468
    }
    ...
  ]
  ```

* #### Detail <https://api.vtbs.moe/v1/detail/:mid>

  => Object, `{mid, uname, …}`

  Return record of certain vtb based on given mid.

  **Example:** <https://api.vtbs.moe/v1/detail/349991143>

  ```json
  {
    "mid": 349991143,
    "uname": "神楽めあOfficial",
    "video": 188,
    "roomid": 12235923,
    "sign": "这里是神楽めあ(KaguraMea)！来自日本的清楚系虚拟YouTuber～weibo:@kaguramea　",
    "notice": "",
    "face": "http://i2.hdslb.com/bfs/face/49e143e1cae7f9e51b36c6c670976a95cc41ce12.jpg",
    "rise": 998,
    "topPhoto": "http://i0.hdslb.com/bfs/space/cde2a0fe3273ae4466d135541d965e21c58a7454.png",
    "archiveView": 21543188,
    "follower": 366159,
    "liveStatus": 0,
    "recordNum": 1268,
    "guardNum": 970,
    "liveNum": 559,
    "lastLive": {
      "online": 354234,
      "time": 1558976168120
    },
    "averageLive": 21271218.38426421,
    "weekLive": 0,
    "guardChange": 953,
    "guardType": [1, 15, 960],
    "areaRank": 2,
    "online": 0,
    "title": "【B限】MeAqua 協力お料理!!!!",
    "time": 1560103157470
  }
  ```

* #### All Guards <https://api.vtbs.moe/v1/guard/all>

  => Object, `{...[mid]: {uname, face, …}}`

  Return all the Guards.

  **Example:** <https://api.vtbs.moe/v1/guard/all>

  ```json
  {
    "119": {
      "uname": "狂气的芙兰",
      "face": "https://i0.hdslb.com/bfs/face/12020cb3bfc0dc7f2a2c47007b204b9559d492f0.jpg",
      "mid": 119,
      "dd": [
        [],
        [],
        [349991143]
      ]
    },
    "436": {
      "uname": "海星参上",
      "face": "https://i0.hdslb.com/bfs/face/a72b138ecd138f230ebe546bcc129ddac5f49c05.gif",
      "mid": 436,
      "dd": [
        [],
        [],
        [349991143, 380829248, 375504219]
      ]
    },
  	...
  }
  ```

  Keys:

  * dd: Array
    * 总督
    * 提督
    * 舰长

* #### Some Guards <https://api.vtbs.moe/v1/guard/some>

  => Object, `{...[mid]: {uname, face, …}}`

  Return some of the Guards, who is at least「提督」or DD.

  **Example:** <https://api.vtbs.moe/v1/guard/some>

  Same as the one above.

* #### Guards <https://api.vtbs.moe/v1/guard/:mid>

  => Array, `[{mid, uname, ...}]`

  Return the Guards of certain vtb based on given mid.

  **Example:** <https://api.vtbs.moe/v1/guard/1576121>

  ```json
  [{
      "mid": 110129,
      "uname": "朔海鸣音",
      "face": "https://i0.hdslb.com/bfs/face/862b9d84e0210c2c0c5b155bd95fb69d4c5c9cfa.jpg",
      "level": 2
    }, {
      "mid": 110232,
      "uname": "星野悠馬",
      "face": "https://i1.hdslb.com/bfs/face/5254186bdee6000da9ccae8c23f699abdb11ebcb.jpg",
      "level": 2
    },
    ...
  ]
  ```

  Keys:

  * level: Number

    `0`: 总督

    `1`: 提督

    `2`: 舰长

* #### Guards update time <https://api.vtbs.moe/v1/guard/time>

  => Number, `Number`

  Timestamp, when guards list updated.
  
  **Example:** <https://api.vtbs.moe/v1/guard/time>
  
  ```json
  1560050332931
  ```

### V2 (JSON)

​	Simple JSON API with Bulk Historical Data.

* #### Active <https://api.vtbs.moe/v2/bulkActive/:mid>

  => Array, `[...{archiveView, follower, time}]`

  History of video views and follower counts.

  **Example:** https://api.vtbs.moe/v2/bulkActive/349991143

  ```json
  [{
      "archiveView": 16222668,
      "follower": 298364,
      "time": 1555247781729
    }, {
      "archiveView": 16222668,
      "follower": 298942,
      "time": 1555276084544
    },
    ...
  ]
  ```

  Keys:

  * archiveView: Number

    Video views

  * follower: Number

    Followers

  * time: Number

    Timestamp

* #### Some active <https://api.vtbs.moe/v2/bulkActiveSome/:mid>

  => Array, `[...{archiveView, follower, time}]`

  History of video views and follower count;

  Same as above, but limited to recent `512` entries.
  
* #### Guard <https://api.vtbs.moe/v2/bulkGuard/:mid>

  => Array, `[...{guardNum, areaRank, time}]`

  History of guard changes.

### V3 (Buffer)

​	"Not so simple" Buffer API with Bulk Historical Data.

* #### All Active <https://api.vtbs.moe/v3/allActive>

  => Buffer:

  ```
         /-----------------------------------\
         |   (32bit UInt) [archiveView]      |
  data:  |   (32bit UInt) [follower]         |
         |   (64bit UInt) [time]             |
         \-----------------------------------/
  
         /------------------------------------\
         |  (32bit UInt) [size of this pack]  |
  pack:  |  (32bit UInt) [mid]                |
         |  [data][data][data][data...        |
         \------------------------------------/
  
  Buffer returned by API: [pack][pack][pack][pack...
  
  (Big Endian)
  ```

  All active data.
  
  Node.js decode example:
  
  ```javascript
  const decodeData = buffer => {
    const data = []
    while (buffer.length) {
      const archiveView = buffer.readUInt32BE()
      const follower = buffer.readUInt32BE(4)
      const time = Number(buffer.readBigUInt64BE(8))
      data.push({ archiveView, follower, time })
      buffer = buffer.slice(16)
    }
    return data
  }
  
  const decodePack = buffer => {
    const actives = []
    while (buffer.length) {
      const size = buffer.readUInt32BE()
      const mid = buffer.readUInt32BE(4)
      const data = decodeData(buffer.slice(8, size))
      buffer = buffer.slice(size)
      actives.push({ mid, data })
    }
    return actives
  }
  
  decodePack(buffer)
  ```
  
  


### vdSocket

​	Live danmaku integrated WebSocket.

​	Use Socket.io connect to `https://api.vtbs.moe/vds`

​	Document: https://github.com/dd-center/vtuber-danmaku#socketio

* #### Subscribe (join)

  ```javascript
  socket.emit('join', roomid)
  // or join all:
  socket.emit('join', 'all')
  ```

* #### Unsubscribe (leave)

  ```javascript
  socket.emit('leave', roomid)
  /// or leave all:
  socket.emit('leave', 'all')
  ```

* #### Danmaku

  ```javascript
  socket.on('danmaku')
  // {message: "233", roomid: 12235923, mid: 3499295}
  ```

### endpoint

​	Endpoint, used for `shields.io` endpoint

* Number of vtubers <https://api.vtbs.moe/endpoint/vtbs>
* Number of guards <https://api.vtbs.moe/endpoint/guardNum>
* Streaming now <https://api.vtbs.moe/endpoint/live>
* Total online <https://api.vtbs.moe/endpoint/onlineSum>

### vtbs.moe api (Socket.IO)

Advanced interface, please reference the source code available on GitHub.

### DD@Home

Websocket connection to `https://cluster.vtbs.moe`

#### Pull task:

Send String: `DDhttp` for more http task.

#### Task distribution:

Recive: (json, http task) 

```json
{
  "key": "SomeRandomString", // exmaple: "0.28634934784"
  "data": {
    "type": "http",
    "url": "some bilibili url" // example: "https://api.bilibili.com/x/space/acc/info?mid=349991143"
  }
}
```

#### Complete Task:

Send: (json)

```json
{
  "key": "SomeRandomString",
  "data": "hereIsResult" // example: "{"code":0,"message":"0","ttl":1,"data":{"mid":349991143,"name":"神楽Mea_Official","sex":"女","face":"http://i1.hdslb.com/bfs/face/4b951570bf09e0ca7fad2a0ae2b1cad3a7a9006b.jpg","sign":"你的人生前路未免太过灰暗了吧？","rank":10000,"level":6,"jointime":0,"moral":0,"silence":0,"birthday":"08-02","coins":0,"fans_badge":true,"official":{"role":1,"title":"bilibili 知名UP主","desc":""},"vip":{"type":2,"status":1,"theme_type":0},"is_followed":false,"top_photo":"http://i0.hdslb.com/bfs/space/cde2a0fe3273ae4466d135541d965e21c58a7454.png","theme":{},"sys_notice":{}}}"
}
```

Make sure the key is same for each task.

### DD Center org, Some internal relationship.

详情: https://dd-center.github.io

![dependency](https://dd-center.github.io/dependency.svg)

## 开发

[development.md](development.md)

## 贡献

想要加什么大功能可以先发 issue 讨论讨论，其他的比如vtb列表补全，修BUG什么的可以直接 Pull request

有什么问题可以开 issue

聊天也可以开 issue →\_→
