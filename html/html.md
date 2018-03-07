## html基础部分
#### 浏览器内核
> 浏览器内核分成两部分
> 1. 渲染引擎
> 2. JS引擎

> 渲染引擎负责对HTML/XML/图形/css渲染
> JS引擎用于解析执行JS得到网页动态效果

常见浏览器引擎
```
	Trident (ie)
    Gecko   (firefox/seamonkey)
    Presto  (旧opera)
    Webkit  (chrome/chromium/safari)
```
#### HTML5变化
##### 新增
	canvas          画布
    video/audio     媒体回放
    localStorage    本地长期存储
    sessionStorage  数据临时储存,关闭标签丢失
    语意化标签
    calendar/date/time/email/url/search表彰控件
    webworkers/websoket/geolocation技术
##### 移除
	basefont/big/center/font/s/strike/tt/u等纯表现元素
    frame/frameset/noframes等影响可用性元素
    
###### webworker
	运行在后台的js不影响页面性能
> 独立于其它脚本<br/>
> 详见js分类

#### cookies/sessionStorage/localStorage
	cookies 
#### HTML语义化
1. 用正确的标签做正确的事情
2. 使页面内容结构化,结构清晰,便于对浏览器、搜索引擎解析
3. 即使在没有样式css情况下容易阅读
4. 搜索引擎的爬虫也依赖于HTML标签确定上下文 和各个关键字权重,利于SEO(优化搜索引擎)
5. 使阅读源代码的人对网站更容易将网站分块,便于阅读维护理解



#### <!DOCTYPE html>
声明位于HTML文档第一行<br/>
作用 告诉浏览器解析用什么文件标准

> HTML5与HTML4.01不同,html不基于SGML,不需要对DTD引用

#### 行内元素/块级元素/空元素
    1. 行内: a b span img input select strong
    2. 块级: div ul ol li dl dt dd h1-h6 p
    3. 空: br hr img input link meta area base col command embed keygen param source track wbr
#### link与@import
link为XHTML标签,页面加载同时link会被加载,可加载css与属性<br/>
@import只加载css,页面加载完毕后被加载
#### iframe
> 阻塞主页面onload事件<br/>
> 搜索引擎无法解读<br/>
> iframe和主页面共享连接池,而浏览器对相同域的连接有限制,影响页面并行加载<br/>
> 最好通过js动态给iframe添加src属性,可绕开以上问题

#### label作用
定义表彰控制间的关系,当用户选择该标签时,浏览器自动将焦点转到和标签相关的表单控件上
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>

  <label for="Name">num</label>
  <input type="text" name="Name" id="Name" />

  <label>date
    <input type="text" name="B" />
  </label>
  
</body>
</html>
```
##### 多浏览器内多个标签页之间通信
> WebSocket<br/>
> SharedWorker<br/>
> 调用localstorge<br/>
> 调用cookies<br/>

##### 在页面上实现一个圆形可点击区域
> map+area或svg<br/>
> border-raduis
> js圆形坐标算法

##### title与h1区别
> title属性没有明确意义只表示标题,h1表示层次明确标题,对页面信息抓取有很大影响
> 