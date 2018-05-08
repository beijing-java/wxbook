## swiper
### 是什么?
swiper是小程序的轮播视图控件,包含指示器、滑动事件、方向、快慢等属性。

| 属性名                  | 类型        | 默认值        |                                         说明                                         | 注释                                         |
|-------------------------|-------------|---------------|:------------------------------------------------------------------------------------:|----------------------------------------------|
| indicator-dots          | Boolean     | false         | 是否显示指示器                                                                       |                                              |
| indicator-color         | Color       | rgba(0,0,0,3) | 指示器的颜色                                                                         | 1.1.0                                        |
| indicator-active-color  | Color       | #000000       | 当前选中的颜色                                                                       | 1.1.0                                        |
| autoplay                | Boolean     | false         | 是否自动播放                                                                         |                                              |
| current                 | Number      | 0             | 当前页面所在的index                                                                  |                                              |
| current-item-id         | String      |               | 当前所在页面的item-id,不能与current被同时指定                                        | 1.9.0                                        |
| interval                | Number      | 5000          | 自动切换时间间隔                                                                     | 只有在自动播放状态下，调节                   |
| duration                | Number      | 500           | 滑动动画时长                                                                         | 两个页面之间的滑动时间                       |
| circular                | Boolean     | false         | 是否采用衔接滑动                                                                     |                                              |
| vertical                | Boolean     | false         | 滑动方向是否为纵向                                                                   | 相应的指示器也会变化(支付宝小程序则不会变化) |
| previous-margin         | String      | "0px"         | 前边距,露出前一页的一小部分                                                          | 接收值为px，rpx                              |
| next-margin             | String      | "0px"         | 后边距，露出后一页的一小部分                                                         | 接收值为px,rpx                               |
| display-multiple-items  | Number      | 1             | 同时显示的滑块数量                                                                   |                                              |
| skip-hidden-item-layout | Boolean     | false         | 是否跳过未显示的滑块布局，在请求网络，加载数据慢的情况下，考虑优化，则可以设置为true |                                              |
| bindchange              | EventHandle |               | 页面改变时触发的事件，type="change"                                                  |                                              |
| bindanimationfinish     | EventHandle |               | 动画结束时触发的事件                                                                 |                                              |

### 显示效果

~~http://upload-images.jianshu.io/upload_images/2073711-d5d76469e204a5c8.gif?imageMogr2/auto-orient/strip~~

![swiper显示效果](http://upload-images.jianshu.io/upload_images/2073711-71f188417ef66cfe.gif?imageMogr2/auto-orient/strip)

### 如何用?
>在wxml文件中的定义

```
  <view>
    <!--indicator-dots是否显示指示器 autoplay是否自动播放 interval播放间隔 duration切换时长 -->
      <swiper indicator-dots="{{indicatorDots}}"
        autoplay="{{autoplay}}" interval="{{interval}}" duration="{{duration}}">
        <block wx:for="{{background}}" wx:key="*this">
          <swiper-item>
            <view class="swiper-item {{item}}"></view>
          </swiper-item>
        </block>
      </swiper>
    </view>
```

> js中定义

```
Page({
<!--如果需要动态修改data中值，可以在事件触发后动态修改-->
  data: {
    background: ['demo-text-1', 'demo-text-2', 'demo-text-3'],
    indicatorDots: true,
    vertical: false,
    autoplay: false,
    interval: 2000,
    duration: 500
  }
})
```
