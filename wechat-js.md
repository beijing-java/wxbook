#小程序讲解~js事件
### 日常简单示例
js负责页面与用户的交互，动态修改页面的内容。使用js脚本来处理用户的操作。
```
<view>{{msg}}</view>
<button bindtap="点击事件">点我</button>
```
**操作解释:** 点击button按钮(点我),修改界面的msg显示为"BeiJing佩奇"

**绑定事件:** bindtap定义了"点击事件"

**j s 函数:** Page({定义函数对应bindtap})
```
Page({
  点击事件: function(){
    this.setData({msg : "BeiJing佩奇" })
  }
})
```
### 名词解释
> 事件是什么？？

- 事件是视图层到逻辑层的通讯方式。
- 事件可以将用户的行为反应到逻辑层进行处理。
- 事件可以绑定在组件上，当达到触发事件，就会触发逻辑层对应的事件处理函数。
- 事件对象可以携带event额外信息，如id，dataset，touches等。

### 如何使用
例如开头示例一样，组件绑定事件，js编写事件函数。
```
  xx.wxml

<view id="tapTest" data-hi="WeChat" bindtap="tapName">点击我</view>

  xx.js

Page({
  tapName:function(event){
    console.log(event)
  }
})
```
这里大概介绍下log打印的内容
```
{
"type":"tap",     事件类型
"timeStamp":895,  事件生成时的时间戳
"target": {       组件一些属性值集合
  "id": "tapTest",
  "dataset":  {
    "hi":"WeChat"
  }
},
"currentTarget":  { 当前组件属性值集合
  "id": "tapTest",
  "dataset": {
    "hi":"WeChat"
  }
},
"detail": { 额外信息
  "x":53,
  "y":14
},
"touches":[{  触摸事件，屏幕触摸点的信息
  "identifier":0, 触摸点标识符
  "pageX":53, 据文档左上角的距离
  "pageY":14,
  "clientX":53,  距离页面可视区域左上角距离
  "clientY":14
}],
"changedTouches":[{ 触摸事件，变化的触摸点信息
  "identifier":0,
  "pageX":53,
  "pageY":14,
  "clientX":53,
  "clientY":14
}]
}
```
------------------------------------
  ☞  *小生不才，附上 [博客地址](http://myblog.ia36.cn)*  ☜

------------------------------------

### 事件汇总
事件分为冒泡事件和非冒泡事件

1.冒泡事件:当一个组件被触发后，该事件以此向父节点传递。

2.非冒泡事件:当一个组件触发后，该事件不会向父节点传递。
### 冒泡事件
| 类型  |  触发条件 | 
|---|---|
|  touchstart | 手指触摸动作开始  | 
|  touchmove | 手指触摸后移动  |
| touchcancel  | 手指触摸动作被打断，如来电提醒，弹窗  | 
| touchend  | 手指触摸动作结束  | 
|  +++++++++ | ++++++++++  | 
|  tap | 手指触摸后马上离开  | 
| longpress  | 手指触摸后，超过350ms再离开(推荐)  | 
| longtap  | 手指触摸后，超过350ms再离开  | 
| +++++++++  | ++++++++++  | 
| transitionend  | 会在WXSS transition或wx.createAnimation动画结束后触发  | 
| animationstart  | 会在一个WXSS animation动画开始时触发  | 
| animationiteration  | 会在一个WXSS animation一次迭代结束时触发  |
| animationend  | 会在一个 WXSS animation 动画完成时触发  | 
| +++++++++  |+++++++++   | 
|touchforcechange   |  在支持 3D Touch 的 iPhone 设备，重按时会触发 |  

### 如何绑定
> 事件绑定的写法同组件的属性，以key,value形式出现。

- key: 以bind或catch开头，后面跟上事件类型(tap,touchstart ...),
  示例：**bindtap** , **catchtouchstart** 
  注：自基础版本1.5.0起，bind和catch后可以写:，再跟事件类型，同上述一样，如bind:tap.
- value: 字符串类型，名字可以随便起，但是一定要与Page中定义的函数名称一致。不然无法触发某事件。

> 绑定事件前缀分析bind、catch事件

- bind事件不会阻止冒泡事件向上传递冒泡

```
示例
<view id="parent_id" bindtap="bind事件1">
    父节点
    <view id="child_id" bindtap="bind事件2">
      子节点
    </view>
</view>
```
解释：当点击子节点时，会依次触发"bind事件2，bind事件1"
- catch事件会阻止冒泡事件向上传递冒泡
```
示例
<view id="parent_id" bindtap="bind事件1">
    父节点
    <view id="child_id"
catchtap="bind事件2">
      子节点
    </view>
</view>
```
解释：当点击子节点时，只触发"bind事件2"，而没有触发"bind事件1"

### 捕获事件
自基础班1.5.0起，触摸类事件支持捕获阶段。捕获阶段位于冒泡阶段之前。事件到达节点的顺序与冒泡相反。捕获事件采用的关键字为capture-bind、capture-catch，当然catch还是中断，取消冒泡阶段。

1.**示例1，执行顺序为hand2,hand4,hand3,hand1**

```
<view bind:touchstart="hand1" capture-bind:touchstart="hand2">
父节点
  <view bind:touchstart="hand3" capture-bind:touchstart="hand4">
  子节点
  </view
</view>
```
2.**示例2，加入capture-catch捕获事件，只执行hand2**

```
<view bind:touchstart="hand1" capture-catch:touchstart="hand2">
父节点
  <view bind:touchstart="hand3" capture-bind:touchstart="hand4">
  子节点
  </view
</view>
```
