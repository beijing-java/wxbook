## 小程序讲解~json
### app.json
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
"color": "#fff", // tab 上的文字默认颜色
"selectedColor": "#fff", // 文字选中时的颜色
"backgroundColor": "#000", // tab 的背景色
"borderStyle": "white", // tabbar上边框的颜色， 仅支持 black/white
"position": "bottom", // tabbar的位置，可选值 bottom、top
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


### page.json

这里的配置，是可以单独配置当前页面，覆盖全局配置文件。只对当前页面生效。

### project.config.json

通常大家在使用开发工具时，会设置自己喜欢的个性样式，例如开发工具颜色，文字大小，编译配置等。但是当你新换电脑，你需要从新配置相关配置。
给予这样的不便，小程序开发者工具在每一个项目下生成一个project.config.json文件。当你重新安装开发工具时，直接导入旧的配置环境就可以了。
