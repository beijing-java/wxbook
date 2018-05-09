### 基础内容-icon
##### 1.是什么？
小程序中规定的小图标，包括成功，失败，下载，搜索，清除。。。等
##### 2.属性
| 属性名 | 类型   | 默认值 | 说明                                                                                                  |
|--------|--------|--------|-------------------------------------------------------------------------------------------------------|
| type   | String |        | icon的类型，有效值：success, success_no_circle, info, warn, waiting, cancel, download, search, clear  |
| size   | Number | 23     | 单位像素，ico大小                                                                                     |
| color  | Color  |        | ico颜色                                                                                               |

##### 3.如何使用？
```
<view>
  <!--icon代表成功信息，大小93px,背景颜色为黑色-->
   <icon type="success" size="93" color="black"></icon>
</view>
```
> 其余的类型，无非乎type改变。大小，颜色，一样

##### 4.效果展示
![小程序ico](https://upload-images.jianshu.io/upload_images/2073711-190d421d2bcffcd7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 基础内容-text
##### 1.是什么？
小程序中的文本类型
##### 2.属性
| 属性名     | 类型    | 默认值 | 说明                                                                  |
|------------|---------|--------|-----------------------------------------------------------------------|
| selectable | Boolean | false  | 文本是否可选,测试基本没什么用处                                       |
| space      | String  | false  | 显示连续空格(ensp中文空格一半，emsp中文空格，nbsp 字体设置的空格大小) |
| decode     | Boolean | false  | 是否解码                                                              |

##### 3.如何使用？
``` xx.wxml
<view>
  <text>{{text}}</text>
  <button bindtap="changtext">改变文字</button>
</view>
```
``` xx.js
Page({
  data:{
    text : "我是文本"
  },
  changetext:function(e){
    this.setData{
      text:"我是改变之后的文本"
    }
  }
})
```

### 基础内容-rich-text
##### 1.是什么？
小程序中展示html,与原生html衔接的富文本
##### 2.属性
| 属性  | 类型         | 默认值 | 说明                 |
|-------|--------------|--------|----------------------|
| nodes | Array/String | []     | 节点列表/HTML String |

- **元素节点** : type=node

| 属性  | 类型         | 默认值 | 必填|说明                 |
|-------|--------------|--------|-----------|-----------|
| name| 标签名 | String     | 是|微信支持的HTML节点 |
| attrs    | 属性       | Object | 否 | 微信支持的信任html属性 |
| children | 子节点列表 | Array  | 否 | 结构和nodes一致        |
- **文本节点** : type=text

| 属性 | 类型 | 默认值 | 必填 | 说明        |
|------|------|--------|------|-------------|
| text | 文本 | String | 是   | 支持entites |
##### 3.如何使用？
```
<!--示例.wxml-->
<view>
  <rich-text nodes="{{nodes}}" bindtap="tap">我是富文本</rich-text>
</view>
```
```
<!--示例.js-->
Page({
  data:{
     nodes:[{
           type:text,
        text:"hello-world"       
    }]
  }]
  }，
tap(){
    this.setData({
       nodes: [{
      name: 'div',
      attrs: {
        class: 'div_class',
        style: 'line-height: 60px; color: red;'
      },
      children: [{
        type: 'text',
        text: 'Hello&nbsp;World!'
      }]
    }]
  })
  }
})
```
##### 4.效果展示
![小程序rich-text](https://upload-images.jianshu.io/upload_images/2073711-ea5c4fef7dac0936.gif?imageMogr2/auto-orient/strip)


### 基础内容-progress
##### 1.是什么？
小程序中的"进度条"
##### 2.属性

| 属性名          | 类型    | 默认值    |                           说明                          | 注释                           |
|-----------------|---------|-----------|:-------------------------------------------------------:|--------------------------------|
| percent         | Float   | 无        | 百分比0-100                                             | 10%的进度条                    |
| show-info       | Boolean | false     | 是否显示百分比                                          | 只要写上show-info,都显示百分比 |
| stroke-width    | Number  | 6         | 进度线条的宽度                                          |                                |
| color           | Color   | #09BB07   | 进度条颜色                                              | 跟activeColor效果一样          |
| activeColor     | Color   |           | 进度条已选择颜色                                        |                                |
| backgroundColor | Color   |           | 进度条背景颜色                                          |                                |
| active          | Boolean | false     | 进度条前进动画                                          |                                |
| active-mode     | String  | backwards | backwards: 动画从头播；forwards：动画从上次结束点接着播 | 测试，无效果                   |
##### 3.如何使用？
```
    <view class="page-section page-section-gap">
      <!--percent百分比 show-info显示百分比 stroke-width进度条宽度 active动画 activeColor进度条颜色-->
      <text>显示百分比</text>
      <view class="progress-box">
        <progress percent="20" show-info stroke-width="13"/>
      </view>
      <text>不显示百分比,进度条颜色</text>
      <view class="progress-box">
        <progress percent="40" activeColor="#1f1f13" stroke-width="3" />
        <icon class="progress-cancel" type="cancel"></icon>
      </view>
      <text>设置颜色，加动画</text>
      <view class="progress-box">
        <progress percent="60" active color="#10AEFF" stroke-width="3"/>
      </view>
    </view>
```
##### 4.效果展示
![小程序progress](https://upload-images.jianshu.io/upload_images/2073711-e4648e9206dc9b5c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-----------------------------------------------------------------
附上资源☺☟☟

[小程序官方示例代码](https://developers.weixin.qq.com/miniprogram/dev/demo.html)
文中代码均对小程序官方示例代码做出过修改,包括添加注释,新加代码测试。
[本文代码示例](https://code.aliyun.com/beijing-java/wechat-demo)