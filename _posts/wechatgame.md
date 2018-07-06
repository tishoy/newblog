---
title: 微信小游戏初探
---
最近这两天把提到的几款游戏引擎都尝试一番，感觉微信对游戏引擎的支持并没有我想象的那么好，对接的时候其实各种坑坑坎坎的。phaser我按着文章说的去搭建，可惜问题出现了。因为版本不一样，我下载了最新的phaser3。领会了一下精神，大概就是要对原有的引擎做一些手脚，所以我也做了。phaser3的引擎本身是webpack打包的，重新打包，把报错的地方修改了一下，就好用了。但是说实话，使用过程中还是怕会遇到坑。

## 自己实现

整体看下来，cocos2d对微信的支持，似乎是最到位的。但最后我决定不使用引擎了。
我使用了微信提供的demo 建立了游戏项目。项目是一个打飞机的游戏，先说关于配置的内容，再说游戏内容。
在README.md包含了项目的目录介绍，里边也具体表述了每个文件的内容。我这边再详细的重复磨叽一遍。
项目包含三个文件夹分别是audio、images、js。另外包含game.js、game.json、project.config.json

### 项目配置文件 project.config.json

打开project.config.json就是项目配置文件，这边跟小程序一样，不同的是compileType，游戏是game，小程序是miniprogram。

### game.json

游戏的配置文件，打开看里边只有一个配置就是 设备的方向，这里可以设置横屏为landscape，也可以保持原有竖屏portrait,默认就是竖屏，另外可以增加几个key：
    showStatusBar:true,//是否显示状态栏
    networkTimeout:60000,//网络请求超时时间单位毫秒
还可以对对网络请求做更细化的超时设置。另外可以设置worker 多线程。具体参考[https://developers.weixin.qq.com/minigame/dev/](https://developers.weixin.qq.com/minigame/dev/)

### js文件

game.js是入口，新建了Main实力。main.js就是主函数，其中结尾处的loop方法，就是游戏的主循环。循环中重要的两个方法就是update与render。update用于更新每一帧的数据，然后render用于显示。window.requestAnimationFrame是小程序(浏览器也有)提供的定时器，会在每一帧执行绑定的loop函数，这个过程不理解可以参考spriteKit，大部分游戏渲染都是这个逻辑。main.js另外还提供了一个Pool和DataBus的示例，这部分用于管理内存，dataBus是个全局的状态管理器，敌人飞机，我方炮弹，动画等内容都被其记录，当某个对象不在screen中显示后，并没有立刻回收对象，而是进入了对象池，以便再次使用。
其他的比如base文件夹下实现了游戏基础的动画与精灵，runtime里实现了游戏的背景与结束提示框相关内容。

### weapp-adapter.js

这部分是微信阉割后，再提供给我们的一些重要的内容，比如websocket、httprequest等，这一部分也是通过webpack打包生成后添加进来的。这个项目在github上可以搜到，我们可以通过修改这个项目，实现我们想添加进来的辅助内容，就比如说我有看到有人在开发weapp-phaser-adapter。