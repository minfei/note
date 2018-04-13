**行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？**

- 行内元素有：`a b span img input select strong`（强调的语气）
- 块级元素有：`div ul ol li dl dt dd h1 h2 h3 h4…p`
- 常见的空元素:` <br> <hr> <img> <input> <link> <meta>`


**HTML5有哪些新特性？**

* 新增选择器 document.querySelector、document.querySelectorAll
* 拖拽释放(Drag and drop) API
* 媒体播放的 video 和 audio
* 本地存储 localStorage 和 sessionStorage
* 离线应用 manifest
* 桌面通知 Notifications
* 语意化标签 article、footer、header、nav、section
* 增强表单控件 calendar、date、time、email、url、search
* 地理位置 Geolocation
* 多任务 webworker
* 全双工通信协议 websocket
* 历史管理 history
* 跨域资源共享(CORS) Access-Control-Allow-Origin
* 页面可见性改变事件 visibilitychange
* 跨窗口通信 PostMessage
* Form Data 对象
* 绘画 canvas

**html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？**

- HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加
  - 绘画 canvas
  - 用于媒介回放的 video 和 audio 元素
  - 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失
  - sessionStorage 的数据在浏览器关闭后自动删除
  - 语意化更好的内容元素，比如 article、footer、header、nav、section
  - 表单控件，calendar、date、time、email、url、search
  - 新的技术webworker, websocket, Geolocation

-  移除的元素：
  - 纯表现的元素：basefont，big，center，font, s，strike，tt，u
  - 对可用性产生负面影响的元素：frame，frameset，noframes

- 支持HTML5新标签：
  - IE8/IE7/IE6支持通过document.createElement方法产生的标签
  - 可以利用这一特性让这些浏览器支持HTML5新标签
  - 浏览器支持新标签后，还需要添加标签默认的样式

- 当然也可以直接使用成熟的框架、比如html5shim


**HTML5的离线储存怎么使用，工作原理能不能解释一下？**

- 在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件

- 原理：HTML5的离线存储是基于一个新建的.appcache文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示

- 如何使用：
  - 页面头部像下面一样加入一个manifest的属性；
  - 在cache.manifest文件的编写离线存储的资源
  - 在离线状态时，操作window.applicationCache进行需求实现
```
CACHE MANIFEST
    #v0.11
    CACHE:
    js/app.js
    css/style.css
    NETWORK:
    resourse/logo.png
    FALLBACK:
    / /offline.html
```


**HTML5的form如何关闭自动完成功能？**

- 给不想要提示的 form 或某个 input 设置为 autocomplete=off。

**如何实现浏览器内多个标签页之间的通信? (阿里)**


* iframe + contentWindow
* postMessage
* SharedWorker(Web Worker API)
* storage 事件(localStorge API)
* WebSocket

**webSocket如何兼容低浏览器？(阿里)**

- Adobe Flash Socket 、
- ActiveX HTMLFile (IE) 、
- 基于 multipart 编码发送 XHR 、
- 基于长轮询的 XHR


**input 利用HTML5 的Datalist 元素实现输入提示**

```
input::-webkit-calendar-picker-indicator {
    display: none;
    -webkit-appearance: none;
}

你最喜欢的浏览器是： <input list="browsers">
<datalist id="browsers">
  <option value="Internet Explorer">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>

```

**HTML5 中新增的<details>标签**

```
<details>
    <summary>Google Nexus 6</summary>
    <p>商品详情：</p>
    <dl>
        <dt>屏幕</dt>
        <dd>5.96” 2560x1440 QHD AMOLED display (493 ppi)</dd>
        <dt>电池</dt>
        <dd>3220 mAh</dd>
        <dt>相机</dt>
        <dd>13MP rear-facing with optical image stabilization 2MP front-facing</dd>
        <dt>处理器</dt>
        <dd>Qualcomm® Snapdragon™ 805 processor</dd>
    </dl>
</details>

```

**html5 viewport**

```
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
// width    设置viewport宽度，为一个正整数，或字符串‘device-width’
// device-width  设备宽度
// height   设置viewport高度，一般设置了宽度，会自动解析出高度，可以不用设置
// initial-scale    默认缩放比例（初始缩放比例），为一个数字，可以带小数
// minimum-scale    允许用户最小缩放比例，为一个数字，可以带小数
// maximum-scale    允许用户最大缩放比例，为一个数字，可以带小数
// user-scalable    是否允许手动缩放

```
- 怎样处理 移动端 1px 被 渲染成 2px 问题
- 1 局部处理
    - meta标签中的 viewport属性 ，initial-scale 设置为 1
    - rem 按照设计稿标准走，外加利用transfrome 的scale(0.5) 缩小一倍即可；
- 2 全局处理
    - meta标签中的 viewport属性 ，initial-scale 设置为 0.5
    - rem 按照设计稿标准走即可


**可能用到的meta标签**
- 设置缩放
```
<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no, minimal-ui" />
 <!-- 可隐藏地址栏，仅针对IOS的Safari（注：IOS7.0版本以后，safari上已看不到效果） -->
 <meta name="apple-mobile-web-app-capable" content="yes" />
 <!-- 仅针对IOS的Safari顶端状态条的样式（可选default/black/black-translucent ） -->
 <meta name="apple-mobile-web-app-status-bar-style" content="black" />
 <!-- IOS中禁用将数字识别为电话号码/忽略Android平台中对邮箱地址的识别 -->
 <meta name="format-detection"content="telephone=no, email=no" />
```
- 其他meta标签

```
<!-- 启用360浏览器的极速模式(webkit) -->
    <meta name="renderer" content="webkit">
    <!-- 避免IE使用兼容模式 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
    <meta name="HandheldFriendly" content="true">
    <!-- 微软的老式浏览器 -->
    <meta name="MobileOptimized" content="320">
    <!-- uc强制竖屏 -->
    <meta name="screen-orientation" content="portrait">
    <!-- QQ强制竖屏 -->
    <meta name="x5-orientation" content="portrait">
    <!-- UC强制全屏 -->
    <meta name="full-screen" content="yes">
    <!-- QQ强制全屏 -->
    <meta name="x5-fullscreen" content="true">
    <!-- UC应用模式 -->
    <meta name="browsermode" content="application">
    <!-- QQ应用模式 -->
    <meta name="x5-page-mode" content="app">
    <!-- windows phone 点击无高光 -->
    <meta name="msapplication-tap-highlight" content="no">
```    


**android 4.x bug**

- 1.三星 Galaxy S4中自带浏览器不支持border-radius缩写
- 2.同时设置border-radius和背景色的时候，背景色会溢出到圆角以外部分
- 3.部分手机(如三星)，a链接支持鼠标:visited事件，也就是说链接访问后文字变为紫色
- 4.android无法同时播放多音频audio
- 5.oppo 的border-radius 会失效

**浏览器地址栏运行HTML代码**
```
data:text/html,<h1>Hello, world!</h1>
```

**把浏览器当编辑器**
```
data:text/html, <html contenteditable>
or
console执行 document.body.contentEditable='true';
```
