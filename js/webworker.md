https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers

#### webworkers API
> webworker可在后台线程运行脚本,不影响页面


一个worker是使用一个构造函数创建的一个对象运行一个命名的js文件<br/>
workers运行在另一个全局上下文中,不同于当前window,用window快捷方式获取当前全局范围在一个worker内将返回错误

##### 检测
```
if ( window.Worker ){
	alert("have")
}
```
##### 创建专用worker
```
var newWorker = new Worker("myscript.js")
```
##### worker消息接收与发送
```
postMessage()
onmessage
```
##### 终止worker
```
newWorker.terminate() //在主线程终止
close()               //在worker线程终止
```
##### 引用脚本
```
importScripts("myscript.js")
```
##### 共享worker
可被多个脚本使用,即使脚本被不同window,iframe或worker访问
```
var newWorker = new ShareWorker("myscript.js")
```
```
//父线程中调用
newWorker.port.start()
```
```
//worker线程调用
port.start()
```

#### 例子
```

```