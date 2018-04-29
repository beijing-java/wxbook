### 小程序的组成
微信小程序无需下载，扫码即用。符合了微信官方所说“即用即走的理念”。
程序有主app框架，与多个page页面组成。
app与page的关系式：1->n 
无论app也好，还是page，每个文件夹里边都包含这四个文件。xxx.js /xxx.json /xxx.wxml /xxx.wxss

### .JSON配置
根目录app下的app.json以及页面下的page.json。
1. app.json 全局配置文件
其中包含所有页面路径、界面表现、网络超时时间、底部tab等。
- pages：页面路径数组，代表整个项目页面加载路径。其中数组第一项代表小程序的初始页面
```
{
  "page":["pages/index/index","pages/xxx/xxx"]
}
```
- window:小程序所有页面的顶部背景颜色，文字颜色定义在这里的
```
  "window":{
    "backgroundTextStyle":"light",//下拉背景字体，loading图的样色。
    "navigationBarBackgroundColor": "#fff",//导航栏 背景颜色
    "navigationBarTitleText": "WeChat",//导航栏标题文字
    "navigationBarTextStyle":"black"//导航栏文字颜色
  }
```
- tabBar :用于页面切换。类似于android的TabBar控件。(支持2-5个tab)
```
{
  "tabBar":{
              "color": "#fff",              // tab 上的文字默认颜色
              "selectedColor": "#fff",      // 文字选中时的颜色
              "backgroundColor": "#000",    // tab 的背景色
              "borderStyle": "white",       // tabbar上边框的颜色， 仅支持 black/white
              "position": "bottom",         // tabbar的位置，可选值 bottom、top
              "list":[{
                      "pagePath":"pages/log/logs",
                      "text":"Tab日志"
              }]
    }
}
```
- networkTimeout:网络请求超时
```
{
  "networkTimeout": {
    "request": 10000,//超时时间，默认60000,单位毫秒，6分钟
    "connectSocket":6000,
    "downloadFile": 10000,
    "uploadFile":10000
  }
}
```
- debug:小程序开发调试开关，开发时开启，上线时关闭
`{"debug":true}`
2. 工具配置project.config.json
通常大家在使用开发工具时，会设置自己喜欢的个性样式，例如开发工具颜色，文字大小，编译配置等。但是当你新换电脑，你需要从新配置相关配置。
给予这样的不便，小程序开发者工具在每一个项目下生成一个project.config.json文件。当你重新安装开发工具时，直接导入旧的配置环境就可以了。
3. page.json 页面局部配置文件
这里的配置，是可以单独配置当前页面，覆盖全局配置文件。只对当前页面生效。

### .WXML模板
WXML解释 :类似于网页编程HTML文件，但它是微信自定义的文件，它于HTML标签不同。它还代表着组件。
WXML于HTML的不同：
1. html 常用标签是div,p,span.开发者在写一个页面的时候可以根据这些基础标签组合成不同组件。wxml直接使用标签，不需要单个组合。常用标签view，button，text等等。
2. 多了wx:if这样的属性这样的表达式。使用MVVM的开发模式，把渲染和逻辑分离。
```
<text>{{msg}}</text>
js管理状态
this.setData({msg:"Hello World"})
```
WXML在微信中具体使用方式：
- 数据绑定

```
xx.wxml
<view>{{message}}</view>
xx.js
Page({
  data:{
    message:"数据绑定"
  }
})
```

- 列表渲染
```
xx.wxml
<view wx:for="{{array}}">{{item}}</view
xx.js
Page({
  data:{
    array:[1,2,3,4,5]
   }
})
```
- 条件渲染
```
xx.wxml
<view wx:if="{{姓名=="王"}}">王</view
<view wx:elif="{{姓名=="晟"}}">晟</view>
xx.js
Page({
  data:{
    姓名:“晟“
  }
})
```
- 模板
```
xx.wxml
<template name="模板">
  <view>
    我是模板:{{moban}}
  </view>
</template>
<template is="模板" data="{{....mobanA}}"></template>
<template is="模板" data="{{....mobanB}}"></template>
xx.js
Page({
  data:{
      mobanA:{moban:"复制品A"},
      mobanB:{moban:"复制品B"}
  }
})
```
- 事件
```
xx.wxml
<view bindtap="shijian">{{tan}}</view>
xx.js
Page({
  data:{
    tan:""
  },
  shijian:function(e){
    this.setData(
       {
          tan:"弹出事件"
      }
    )
  }
})

```


### .WXSS样式
### .JS       逻辑
### MVVM模式
