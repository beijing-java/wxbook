#小程序讲解~wxss样式

### WXSS样式
- 名词解释:

 wxss(WeiXin Style Sheets)是一套微信开发的样式语言,主要用于描述WXML的 *组件* 样式。
 wxss用来决定WXML的组件如何展示。
- 与CSS对比

  1.尺寸单位  
  css: 使用单位 px像素，em字体尺寸，pt(1pt=1/72in)
  wxss: 使用单位 rpx (reponsive pixel) 可以根据屏幕的宽度自适应.
       例如：iphone6屏幕宽为375px,共有750物理像素。750rpx=375px=750物理像素
  表格:
  
|  设备| rpx转换px  |  px转换rpx | 
|------|------|------|
| iphone5  | 1rpx=0.42px  | 1px=2.34rpx  |
|  iphone6 | 1rpx=0.5px  | 1px=2rpx  |
| iphone6 plus | 1rpx=0.552px |1px=1.81rpx   |

> 官方建议:UI设计师以iphone6为设计稿标准，1:2设计尺寸
  
  
    2.样式引入
  
> css:

  - 行内引入
  
     示例：
      `<p style="color=red;">style引入</p>`
  - 内部样式引入       
      示例：
      
```
        <style type="text/css">
          p{
            color:red;
          }
        </style>
        html的组件引入内部样式
        <p>内部定义好后就相当于引入成功</p>
```
      
  - 外部样式引入 
      将css样式保存在.css样式表中，HTML文件引入.css样式文件，这里也有两种方式:链接式，导入式
    1. 链接式
  
      `<link type="text/css" rel="styleSheet" href="css文件路径" />`
   2. 导入式
   
     ```
     <style type="text/css">
       @import url("css路径")
     </style>
     ```
> wxss:

     wxss也包括外部样式引入，内联样式
  - 外部样式
> wxss使用@import引入,@import后跟需要导入的外联样式表的相对路径，用;表示语句结束。

     示例： 
     
            ```
            /**wxss1样式**/
            .p1{
            color:red;
            }
            ```
            
            ```
            /**wxss2样式,引入wxss1样式**/
            @import "wxss1";
            .p2{
             color:red;
            }
            ```
  - 内联样式
  
    1.style:静态的样式统一写到class中，style接收动态的样式，为了不影响渲染速度，建议使用动态加载
    
    `<view style="color:{{color}};"></view>`
    2.class:用于指定样式规则，其属性值是样式规则中类选择器名(样式类名)的集合，样式类名不需要带上.，样式类名之间用空格分隔。
    
    `<view class="normal_view" />`
  
     