### 小程序选择按钮
- 多选按钮
- 单选按钮
### checkbox-group
#### 解释
小程序多选按钮,内部有多个checkbox组件组成
#### 属性
- checkbox-group

| 事件       | 类型        | 默认值 | 说明                                                                     |
|------------|-------------|--------|--------------------------------------------------------------------------|
| bindchange | EventHandle |        | <checkbox-group/>中选中改变触发change事件，detail={value:[checkbox的value数组]} |

- checkbox

| 属性     | 类型    | 默认值 | 说明                                           |
|----------|---------|--------|------------------------------------------------|
| value    | String  |        | <checkbox/>的value标识，change事件触发后携带值 |
| disabled | Boolean | false  | <checkbox/>不可点                              |
| checked  | Boolean | false  | 为true时，默认选中状态                         |
| color    | Color   |        | checkbox小对勾的颜色                           |

#### 展示
![checkbox-group多选项](https://upload-images.jianshu.io/upload_images/2073711-88e95457c9ee6995.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 使用
```
    <view class="page-section page-section-gap">
      <view class="page-section-title">默认选择样式</view>
      <label class="checkbox">
        <checkbox value="cb" checked="true"/>选中
      </label>
      <label class="checkbox">
        <checkbox value="cb" />未选中
      </label>
    </view>

    <view class="page-section">
      <view class="page-section-title">多选展示样式</view>
      <view class="weui-cells weui-cells_after-title">
        <checkbox-group bindchange="checkboxChange">
          <label class="weui-cell weui-check__label" wx:for="{{items}}" wx:key="{{item.value}}">
            <view class="weui-cell__hd">
              <checkbox value="{{item.value}}" checked="{{item.checked}}" color="{{item.color}}" disabled="{{item.disabled}}"/>
            </view>
            <view class="weui-cell__bd">{{item.name}}</view>
          </label>
        </checkbox-group>
      </view>
    </view>
```
```
<!--checkbox-group.js-->
checkboxChange: function(e) {
    console.log('checkboxChange事件，携带value值为：', e.detail.value);
    var items = this.data.items, values = e.detail.value;
    for (var i = 0, lenI = items.length; i < lenI; ++i) {
      items[i].checked = false;
      // items[i].color="red";
      for (var j = 0, lenJ = values.length; j < lenJ; ++j) {
        if(items[i].value == values[j]){
          items[i].checked = true;//选中
          items[i].color="black";//改变颜色
          items[i].disabled=true;//设置不可点
          break
        }
      }
    }

    this.setData({
      items: items
    })
  }
```

### radio
#### 解释
小程序的单选按钮,内部有多个`<radio/>`组成
#### 属性
- radio-group

| 事件       | 类型        | 默认值 | 说明                                                                     |
|------------|-------------|--------|--------------------------------------------------------------------------|
| bindchange | EventHandle |        | <radio-group/>中选中改变触发change事件，detail={value:选中radio的value值} |
-radio

| 属性     | 类型    | 默认值 | 说明                                        |
|----------|---------|--------|---------------------------------------------|
| value    | String  |        | <radio/>的value标识，change事件触发后携带值 |
| disabled | Boolean | false  | <radio/>不可点                              |
| checked  | Boolean | false  | 为true时，默认选中状态                      |
| color    | Color   |        | radio小对勾的颜色                           |

#### 演示
![radio单选按钮](https://upload-images.jianshu.io/upload_images/2073711-9d0b1dfcffbd4b94.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 代码
```
<!--xx.wxml-->
 <view class="page-section">
      <view class="page-section-title">推荐展示样式</view>
      <view class="weui-cells weui-cells_after-title">
        <radio-group bindchange="radioChange">
          <label class="weui-cell weui-check__label" wx:for="{{items}}" wx:key="{{item.value}}">

            <view class="weui-cell__hd">
              <radio value="{{item.value}}" checked="{{item.checked}}"/>
            </view>
            <view class="weui-cell__bd">{{item.name}}</view>
          </label>
        </radio-group>
      </view>
    </view>
```
```
<!--xxx.js-->
  radioChange: function(e) {
    console.log('radio发生change事件，携带value值为：', e.detail.value)

    var items = this.data.items;
    for (var i = 0, len = items.length; i < len; ++i) {
      items[i].checked = items[i].value == e.detail.value
      if(items[i].checked){
        items[i].name = items[i].name + "选中了";
      }
    }
    this.setData({
      items: items
    });
  }
```