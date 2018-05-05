## 小程序讲解-wxml

### .WXML模板
WXML解释 :类似于网页编程HTML文件，但它是微信自定义的文件，它于HTML标签不同。它还代表着组件。
WXML于HTML的不同：
1. html 常用标签是div,p,span.开发者在写一个页面的时候可以根据这些基础标签组合成不同组件。wxml直接使用标签，不需要单个组合。常用标签view，button，text等等。
2. 多了wx:if这样的属性以及{{}}这样的表达式。使用MVVM的开发模式，把渲染和逻辑分离。
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
