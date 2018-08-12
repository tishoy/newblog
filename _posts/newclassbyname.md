---
title: egret引擎，TS动态创建类，及微信小游戏中使用。
---
最近又在用egret搞开发，目标是一个微信中的小游戏。开发了几天之后，略微感觉有些棘手，毕竟ts开发之后，在小游戏中测试的还是编译后的js。感觉不如js的引擎。好多人推荐我layabox。说实话，一直不觉得这个是个靠谱的东东。感觉搞定这个项目之后，不如再试试cocos。
话题扯远了，先说我这次要做的游戏是一个巨多关卡的游戏，如果一次性new这么多关卡出来，明显会浪费好多内存。所以在ts中每个关卡都是单独的一个类。localstorage中存储这当前到达的关卡id，独取出来之后，创建之。

## TS动态创建类
在ts中，是可以这样写的。

``` bash
$ let stageId = localstorage.getItem("curStage");
$ let CurStage = new window["Stage" + stageId];
$ this.addChild(CurStage); //Stage 添加到相应位置
```

当然更加完善点的

``` bash
$ let instanceceparameters; // 目标构造函数参数
$ let className; // 目标类
$ let newInstance = Object.create(window[className].prototype);
$ newInstance.constructor.apply(newInstance, instanceceparameters);
```

但是发现打包到微信小游戏里，window并没有这部分内容。通过对比浏览器版本跟小游戏版本的window，最后在新版本egret中的scripts目录下wxgame.ts中进行了一些修改，得以解决。

在wxgame.ts的第38行

``` bash
$ content += ";window.Main = Main;"
```

不难理解，这就是忘生成后的小程序中window注入了这个类。我们根据自己的需求，将目标类都挂到了window下。这样，在微信小程序中就可以动态实例化想要的关卡了。