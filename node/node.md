### 通过nodejs模块
```
var b=require("./index.js") //引入自己的js模块 导入index.js导出的东西 当导入文件模块时路径必须添上 ./
module.exports=a //导出模块
```
#### node模块分类
1. 核心模块-自带 
2. 文件模块-自己写 
3. 第三方模块-插件

#### 第三方模块导入时
```
 npm run xx #执行package.json脚本
```
### lodash按需加载
	npm install lodash --save
```
 import findIndex from "lodash/findIndex"
```
<br/>
<br/>
<br/>
### babel
babel 将es6转换es5
webpack 模块导入导出 打包工具
react 用es6 jsx技术

### 回调函数 异步依赖于回调

阻塞代码实例

```
vim input.txt

# 内容
hello

vim main.js

# 内容

let fs   = require('fs')
let data = fs.readFileSync('input.txt')
console.log(data.toString())
console.log('aa')
```

非阻塞代码实例 使用回调

```
vim input.txt

# 内容
hello

vim main.js

# 内容
let fs = require('fs')
fs.readFile('input.txt', function (err, data) {
    if(err) return console.log(err)
    console.log(data.toString)
})
console.log("aa")
```

### 事件循环

```
// 引入events模块
let events = require('events')
// 创建eventEmitter对象
let eventEmitter = new events.EventEmitter()
let connectHandler = function connected() {
    console.log('linked')
    // 触发data_received
    eventEmitter.emit('data_received')
}
// 绑定connection事件处理程序
eventEmitter.on('connection', connectHandler)
// 使用匿名函数绑定data_received事件
eventEmitter.on('data_received', function() {
    console.log('received')
})
```