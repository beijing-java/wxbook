## scroll-view
### 是什么?
微信小程序滚动视图，分为横向滚动，纵向滚动。以及滚动事件。

|         属性名        |     类型    | 默认值 |                                          说明                                          |
|:---------------------:|:-----------:|--------|:--------------------------------------------------------------------------------------:|
| scroll-x              | Boolean     | false  | 允许横向滚动                                                                           |
| scroll-y              | Boolean     | false  | 允许纵向滚动                                                                           |
| upper-threshold       | Number      | 50     | 距上部临界值，达到多远距离时， 触发scrolltoupper事件                                   |
| lower-threshold       | Number      | 50     | 距底部临界值，达到多远距离时， 触发scrolltolower事件                                   |
| scroll-top            | Number      |        | 设置竖向滚动条的位置                                                                   |
| scroll-left           | Number      |        | 设置横向滚动条的位置                                                                   |
| scroll-into-view      | String      |        | 值应为某子元素id,设置那个方向可滚动， 则在那个方向滚动到该元素                         |
| scroll-with-animation | Boolean     | false  | 在设置滚动条位置时使用动画过渡                                                         |
| enable-back-to-top    | Boolean     | false  | ios点击顶部状态栏，安卓双击标题栏时回顶部。                                            |
| bindscrolltoupper     | EventHandle |        | 滚动到顶部/左边，会触发scrolltoupper事件                                               |
| bindscrolltolower     | EventHandle |        | 滚动到底部/右边，会触发scrolltolower事件                                               |
| bindscroll            | EventHandle |        | 滚动时触发，event.detail={scrollLeft,scrollTop,scrollHeight,scrollWidth,deltaX,deltaY} |

### 如何用?
#### 纵向滚动-示例

> 使用竖向滚动时，需要给<scroll-view>一个固定高度，通过wxss设置height。

```
<view>
  <view>scroll-view 竖向滚动</view>
  <scroll-view scroll-y="true" style="height:200rpx;" 
                      bindscrolltoupper="upper" bindscrolltolower="lower"                         bindscroll="scroll">
    <view>视图1</view>
    <view>视图2</view>
    <view>视图3</view>
  </scroll-view>
</view>
```

注释:scroll-y不管为true跟false。只要写上scroll-y，它就代表竖向滑动

```
Page({
  upper:function (e){
    <!--触发顶部事件-->
    type:"scrolltoupper",
    detail:{direction:"top"}
  },
  lower:function (e){
        <!--触发底部事件--> 
       type:"scrolltolower",
    detail:{direction:"bottom"}
  },
  scroll:function (e){
       <!--只要滑动就会触发 滑动事件-->
      type:"scroll",
      
  },
})
```

#### 横向滚动-示例

```
<view>
  <view>
    <text>scroll-view横向滑动</text>
  </view>
  <view>
    <scroll-view scroll-x bindscroll="scroll" bindscrolltoupper="upper">
      <view>视图1</view>
      <view>视图2</view>
      <view>视图3</view>
    </scroll-view>
  </view>
</view>
```

注释：横向滚动与竖向滚动，都可以给绑定一些事件，包括到顶，到底，滑动事件。

### BeiJing佩奇
[博客地址](http://myblog.ia36.cn)