# blive

<p align="left">
<a href="https://npmjs.com/package/blive-ws"><img src="https://img.shields.io/npm/v/blive-ws.svg" alt="npm package"></a>
</p>

b站直播间的ws服务

## 安装

```shell
npm i blive-ws
```

```shell
yarn i blive-ws
```

```shell
pnpm i blive-ws
```

## 使用

```js
import WebPlayerSocket from 'blive-ws'

// 1. 实例化
const socket = new WebPlayerSocket({
    rid: '房间id',
    uid: '用户id',
    token: 'token',
    hostList: [],
    // debug: true,
})

// 2. 绑定事件
socket.addEventListener('open', ({detail}) => {
    console.log('直播间连接成功')
})
socket.addEventListener('close', ({detail}) => {
    console.log('直播间断开连接')
})
socket.addEventListener('DANMU_MSG', ({detail}) => {
    console.log('弹幕数据: ', detail)
})
```

## Options

| 参数名 |   类型   | 说明  | 必填  | 默认值 |
|:---:|:------:|:---:|:---:|:---:|
| rid | number | 房间号 |  是  | --  |
| uid | number | 用户id | 否 |  0  |
| token | string | 认证token | 是 | --  |
| hostList | string[] | ws服务列表 | 否 | [] |
| debug | boolean | 调试模式 | 否 | false |

## Events

|          事件名(大小写敏感)           |       说明       | 数据(event.detail) |
|:-----------------------------:|:--------------:|:----------------:|
|             open              |     直播间已连接     |    选项options     |
|             close             |     直播间已断开     |    选项options     |
|             error             |      出现错误      |      error       |
|          initialized          | websocket完成初始化 |        -         |
|        heartbeatreply         |      心跳应答      |       人气值        |
|     COMMON_NOTICE_DANMAKU     |      公共通知      |                  |
|          NOTICE_MSG           |      任务通知      |                  |
|      STOP_LIVE_ROOM_LIST      |    停播直播间列表     |                  |
|       HOT_RANK_CHANGED        |      热榜更新      |                  |
|      HOT_RANK_CHANGED_V2      |      热榜更新      |                  |
|    HOT_RANK_SETTLEMENT_V2     |      热榜结算      |                  |
|           DANMU_MSG           |      普通弹幕      |                  |
|       DANMU_AGGREGATION       |      聚合弹幕      |                  |
|      SUPER_CHAT_MESSAGE       |     超级聊天消息     |                  |
|    SUPER_CHAT_MESSAGE_JPN     |     超级聊天消息     |                  |
| ROOM_REAL_TIME_MESSAGE_UPDATE |   直播间实时信息更新    |                  |
|         INTERACT_WORD         |    直播间互动文字     |                  |
|        WATCHED_CHANGE         |   直播间观看人数更新    |                  |
|        ONLINE_RANK_V2         |   直播间高能用户排名    |                  |
|       ONLINE_RANK_COUNT       |    直播间高能用户数    |                  |
|       ONLINE_RANK_TOP3        |  直播间Top3高能用户   |                  |
|         ENTRY_EFFECT          |      进入特效      |                  |
|           GUARD_BUY           |      购买舰长      |                  |
|           SEND_GIFT           |      送礼物       |                  |
|          COMBO_SEND           |      连送礼物      |                  |
|             LIVE              |      开始直播      |                  |
|           PREPARING           |      准备中       |                  |
|       PK_BATTLE_PRE_NEW       |       PK       |                  |
|         WIDGET_BANNER         |   小部件          |                  |
|     LIVE_INTERACTIVE_GAME     |  现场交互游戏(弹幕？)   |                  |

## Methods

### 1. destroy 销毁实例
```js
socket.destroy()
```
