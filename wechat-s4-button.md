## button按钮
#### 解释:
小程序的button按钮，常用于与用户交互使用。
#### 属性:
>button属性

| 属性名                 | 类型    | 默认值       |                          说明                          | 注释                                               |
|------------------------|---------|--------------|:------------------------------------------------------:|----------------------------------------------------|
| size                   | String  | default      | 按钮的大小                                             | 类型String,不是Number 只有default、mini,下文有解释 |
| type                   | String  | default      | 按钮展示的样式                                         | 下文有解释                                         |
| plain                  | Boolean | false        | 按钮是否镂空,背景色透明                                |                                                    |
| disabled               | Boolean | false        | 按钮是否禁用,不可点击                                  |                                                    |
| loading                | Boolean | false        | 名称前是否带loading图标                                |                                                    |
| ----以上为常用----     |         |              |                                                        |                                                    |
| form-type              | String  |              | 用于form组件的按钮(submit/reset)                       | 下文有解释                                         |
| open-type              | String  |              | 微信开发能力(分享，获取用户信息，客服聊天)             |                                                    |
| ---button动作----      |         |              |                                                        |                                                    |
| hover-class            | String  | button-hover | 按钮按下去的样式类，当hover-class="none"，没有点击效果 |                                                    |
| hover-stop-propagation | Boolean | false        | 阻止父节点出现点击态                                   |                                                    |
| hover-start-time       | Number  | 20           | 按住多久出现点击态，(毫秒)                             |                                                    |
| hover-stay-time        | Number  | 20           | 松开后点击保留时间,(毫秒)                              |                                                    |

##### size有效值

| 值      | 说明   |
|---------|--------|
| default | 默认值 |
| mini    |        |

##### type有效值

| 值      | 说明   |
|---------|--------|
| primary| 原色值 |
| default   |  默认值      |
| warn|  警告值      |

##### form-type有效值

| 值      | 说明   |
|---------|--------|
| submit| 提交表单 |
| reset |  重置表单  |

##### open-type有效值

| 值      | 说明   |
|---------|--------|
| contact| 打开客服,需要小程序后台配置 |
| share   |   打开分享面板     |
| getUserInfo |   可以在bindgetuserinfo中回调获取用户信息     |
| getPhoneNumber |  可以在bindgetphonenumber回调中获取用户信息      |
| launchApp |   打开App 可以通过app-parameter属性设置向app传的参数     |

#### 展示
![button展示效果](https://upload-images.jianshu.io/upload_images/2073711-c7e670f5a9590dc6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 使用:
```
  <view class="btn-area" id="buttonContainer">
      <!--原色-->
      <button type="primary">按钮原色</button>
      <button type="primary" loading="true">按钮Loading</button>
      <button type="primary" disabled="true">不可点Disabled</button>
      <!--默认-->
      <button type="default">默认值</button>
      <button type="default" disabled="true">默认值Disabled</button>
      <!--警告-->
      <button type="warn">警告类</button>
      <button type="warn" disabled="true">警告类操作 Disabled</button>

      <view class="button-sp-area">
        <button type="primary" plain="true">镂空按钮</button>
        <button type="primary" disabled="true" plain="true">不可点击</button>

        <button type="default" plain="true">按钮</button>
        <button type="default" disabled="true" plain="true">不可点按钮</button>

      <view class="mini-btn">
        <button  type="primary" size="mini">按钮</button>
        <button  type="default" size="mini">按钮</button>
        <button type="warn" size="mini">按钮</button>
      </view>
        <button type="primary" open-type="contact" session-from='BeiJing佩奇'>朋程</button>
      </view>
    </view>
```

-----------------------------------------------------------------
附上资源☺☟☟

[小程序官方示例代码](https://developers.weixin.qq.com/miniprogram/dev/demo.html)
文中代码均对小程序官方示例代码做出过修改,包括添加注释,新加代码测试。
[本文代码示例](https://code.aliyun.com/beijing-java/wechat-demo)
[小程序wiki](https://beijing-java.gitbooks.io/wechat-small-course/content/)