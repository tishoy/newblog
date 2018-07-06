---
title: Next Plan 下一步
---
自从2017年初，微信小程序出来，就一直比较关注。不过微信需要开发者认证，一直以来都是没有对个人开发者的，至少是一个公司。那个时候，还就想把公司的管理系统做到微信小程序里，并对此深入开发一番，但是公司没有这个意思，所以也就一直没有动。加上之前我对rogue like游戏的设计体验，这次，我打算开发一款rogue like类型的微信小游戏。这边我先主要记录一些最近了解到的微信小程序相关的资源。

## 微信小程序

首先微信给出的模板是主程序app以及各自页面文件page，就先找一下模块化，组件化，MV*等的模板：

- WePY: [微信官方的框架](https://tencent.github.io/wepy/)
- labrador: [拉布拉多](https://github.com/maichong/labrador)

一个图表绘制组件
- wxapp-charts: [微信小程序图表](https://github.com/hawx1993/wxapp-charts)
- wxParse: [富文本解析](https://github.com/icindy/wxParse)
- wx-redux: [Redux绑定](https://github.com/charleyw/wechat-weapp-redux)

## 微信小游戏

小游戏就是重点啦，之前想过要把游戏投放到facebook,因为今年的facebook也是相当利好，不过在推广方面，还是被微信的这9亿用户（也就是你们）忽悠了。开发下游戏比较关注国内的几款引擎，都已经提供了一键生成这种，但是里边的坑，说不清。这边我也是精心筛选了最后还是选用pixi跟phaser，如果有3d的需要，还会用three.js，还是把探索的内容分享下：

- pixi: [官网](http://www.pixijs.com/), [微信小游戏解决方案](https://www.jianshu.com/p/38fcbcaf2930)
- phaser: [官网](http://phaser.io/), [微信小游戏解决方案](https://www.indienova.com/indie-game-development/run-phaser-on-wechat-game-platform/), [phaser小站](https://www.phaser-china.com/)
- cocos2d: [微信小游戏解决方案](https://github.com/hexcola/wxgame/wiki/Cocos)
- egret: [官网](https://www.egret.com/), [微信小游戏解决方案](http://developer.egret.com/cn/github/egret-docs/Engine2D/minigame/minigameFAQ/index.html)
- layabox： [官网](https://www.layabox.com/), [微信小游戏解决方案](https://ldc.layabox.com/doc/?nav=zh-as-5-0-0)
- three： [官网](https://threejs.org/), [微信小游戏解决方案](https://indienova.com/indie-game-development/run-threejs-on-wechat-game-platform/)

## 最终还是说下我的选择

小程序方面，无疑使用微信官方一点的WePY来作为基础开发，毕竟在人家大树下边好乘凉。Vue的语法，不用处理NPM的依赖，Async的使用，都是比较前卫的。

游戏方面，选择phaser是因为毕竟老引擎了，个人了解的也比egret、laya早，至于不选用cocos完全是个人原因，就是不喜欢cocos的语法，不是因为cocos不好，我要做个有个性的程序员。另外就是pixi真的小。


### 更多关于作者

诗歌集: [poetry](http://tishoy.com/poetry/)
