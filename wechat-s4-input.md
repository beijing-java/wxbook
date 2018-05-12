#### 解释
小程序input表单(文本,数字,密码)
`<input />`
#### 属性
| 属性名            | 类型        | 默认值              | 说明                                                       |
|-------------------|-------------|---------------------|------------------------------------------------------------|
| value             | String      |                     | 输入框的初始化内容                                         |
| type              | String      | "text"              | input类型(text,number,idcard,digit)                        |
| password          | Boolean     | false               | 是否显示密码类型                                           |
| placeholder       | String      |                     | 输入框中的占位符                                           |
| placeholder-style | String      |                     | 指定placeholder的样式                                      |
| placeholder-class | String      | "input-placeholder" | 指定placeholder的样式类                                    |
| disabled          | Boolean     | false               | 是否禁用,不能输入                                          |
| maxlength         | Number      | 140                 | 最大的输入长度,设置-1时无限制                              |
| cursor-spacing    | Number      | 0                   | 指定光标与键盘的距离,单位为px                              |
| auto-focus        | Boolean     | false               | 自动聚焦,拉起键盘                                          |
| focus             | Boolean     | false               | 获取焦点                                                   |
| confirm-type      | String      | "done"              | 键盘右下角的文字(send,search,next,go,done)                 |
| confirm-hold      | Boolean     | false               | 点击键盘文字,键盘是否收起                                  |
| cursor            | Number      |                     | 获取焦点focus后,光标位置                                   |
| adjust-position   | Boolean     | true                | 键盘弹起,页面自动向上推动                                  |
| bindinput         | EventHandle |                     | 有文字输入,触发input事件,e.detail={value值,cursor光标长度} |
| bindfocus         | EventHandle |                     | 输入框聚焦时触发,e.detail={value,height}                   |
| bind blur         | EventHandle |                     | 输入框失去焦点时触发e.detail={value}                       |
| bind confirm      | EventHandle |                     | 点击键盘完成时,触发e.detail={value}                        |
#### 演示

![小程序 input.wxml](https://upload-images.jianshu.io/upload_images/2073711-c60c4d5f9e206fb4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![小程序 input.js](https://upload-images.jianshu.io/upload_images/2073711-7819c381d7eb089c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 示例

```
<view class="weui-cells weui-cells_after-title">
        <view class="weui-cell weui-cell_input">
          <input class="weui-input"  maxlength="10" bindinput="bindKeyInput" bindblur='bindblurEvent' placeholder="输入同步到view中"/>
        </view>
      </view>
```
```
Page({
  data: {
    focus: false,
    inputValue: ''
  },
  bindKeyInput: function (e) {
    console.log('输入内容触发input事件',e.detail)
    this.setData({
      inputValue: e.detail.value
    })
  },
  bindblurEvent: function (e){
    console.log("失去焦点时",e.detail)
  },
  bindReplaceInput: function (e) {
    var value = e.detail.value
    var pos = e.detail.cursor
    var left
    if (pos !== -1) {
      // 光标在中间
      left = e.detail.value.slice(0, pos)
      // 计算光标的位置
      pos = left.replace(/11/g, '2').length
    }

    // 直接返回对象，可以对输入进行过滤处理，同时可以控制光标的位置
    return {
      value: value.replace(/11/g, '2'),
      cursor: pos
    }

    // 或者直接返回字符串,光标在最后边
    // return value.replace(/11/g,'2'),
  },
  bindHideKeyboard: function (e) {
    if (e.detail.value === '123') {
      // 收起键盘
      wx.hideKeyboard()
    }
  }
})

```