# git
git init 将本地文件夹变成git仓库<br/>
git add 将某些文件添加到git的缓存区    .代表所有的修改<br/>
git add index.html让git跟踪修改<br/>
git commit -m "版本信息" 将本次的修改做成一个版本,并提交版本信息<br/>
git status 查看当前仓库状态<br/>
第一次使用git commit会弹出提示信息<br/>
git push 没有推送目标 第一次推送提示没有目标<br/>
ssh-keygen钥匙<br/>
git-pull拉取远程的更新到本地<br/>
cp xx xx复制<br/>
mv xx xx剪切 重命名<br/>
gh-pages分支<br/>
git branch查看当前仓库分支<br/>
git branch 分支名 创建新的分支<br/>
git branch gh-pages 特殊分支<br/>
git checkout 分支名 切换到分支<br/>
当创建新的分支时，分支里面的内容默认和master一样<br/>
如果仓库有gh-pages分支 可用 用户名.github.io/仓库名访问 gh-pages分支下的页面<br/>
merge合并分支<br/>
apm install emmet atom编辑器安装插件<br/>
npm init 管理文件<br/>
npm i jquery --save 非工具类<br/>
npm i xx --save-dev 工具类<br/>
npm i jquery@版本号 --save 安装某种版本包<br/>
npm unistall jquery 卸载jq<br/>
npm i 安装package.json里的包<br/>
.gitignore 文件 git上传时写在该文件内的文件被忽略上传 比如node_modules<br/>
将本地仓库删除 克隆网上的仓库到本地 将node_modules删除再上传 此时网上就没有了node_modules<br/>
然后本地 npm i node_modules 就会出现 此时新建.gitignore 再上传 此时本地的node_modules 就会上传不上去了<br/>
npm i zepto -g 全局包此电脑任何地方都能使用<br/>
npm uninstall zepto -g 删除全局包<br/>
通过nodejs模块<br/>
var b=require("./index.js") 引入自己的js模块 导入index.js导出的东西 当导入文件模块时路径必须添上 ./ <br/>
module.exports=a 导出模块<br/>
node 模块分类 1,核心模块-自带 2,文件模块-自己写 3,第三方模块-插件<br/>
第三方模块导入时<br/>
npm run xx 执行package.json脚本<br/>
let es6声明变量的方式 1,拥有块级作用域 只要在大括号内声明就会形成作用域<br/>
						2,同一个作用域下不允许重复声明相同变量<br/>
							3,变量声明不提升<br/>
								4,在let作用域内声明之前使用变量会报错<br/>
									```{
										ket a=10
										console.log(a)
									```}//简写封装形式
const 常量<br/>
#字符串模板
var username="a"
			var age=10
				var c="my name is"+username
					var c=`my name is ${username}`
箭头函数
参数除了一个之外必须使用小括号 当有一个参数可省略小括号 箭头右面是要做的事 当要做的<br/>
事不止一句时必须加上大括号 当只有一句执行时,可以省略大括号 但是同时这名会被当作该函数<br/>
的返回值 当需要写返回值时需要在大括号最后面添加return 箭头函数内的this对象是定义时所<br/>
在的对象而不是使用时所在的对象 不可以当作构造函数new命令 箭头函数不可使用arguments对<br/>
象 可用rest参数代替<br/>
```
let add=(a)=>console.log(a)
let add=(a,b)=>console.log(a+b)
let add=(a,b)=>{console.log(a+b);console.log(b)}
let add=()=>{
	var a=10
	var b=20
	var c=30
	var c=a+b
	return c
}
new xx({

})
```

var a=x||0 当x为undefined时a=0<br/>
函数声明时在小括号内部直接给参数赋值  相当于给参数默认值<br/>
es6函数参数集合<br/>
let sum=(...rest)=>console.log(rest) rest剩余参数<br/>
函数默认参数<br/>
...rest 剩余参数

```
class 类
	class Person(){
		constructor(name){ //私有 constructor默认固有不能改名
			this.name=name
		}
		say(){
			console.log(1)
		}
	} //class内部写方法,并且方法之间不能加逗号
		当执行new class时默认执行constructor
	let people=new Person()


Object.assgin() 合并对象 将第一个参数之后的对象合并到第一个对象参数内
let obj={
	name:"aaa",
	age:"11"
}
let obj1=Object.assign({},obj)
obj1.name="a"
console.log(obj1,obj)
```

findIndex 方法 查找索引值<br/>
map方法 通过原来的数组生成新的数组<br/>
find 方法找数组中某一项<br/>
```let obj=arr.find(item=>item.name==="aaa")
console.log(obj)
```


reduce() 累加器<br/>


Object.keys() 获取对象所有属性值的数组<br/>


require("./aaaaaaa.js") 导入模块<br/>
es6将每个js当成一个模块<br/>


es6模块导入导出 模块导入必须在当前模块最顶端<br/>
	1,命名导出 export{a} //加大括号<br/>
	  命名导入 import {a} from "./module" //.js可省略<br/>
		命名导出 导入的变量名和导出必须一致<br/>
		import {b as a} from "./modules" 这as相当重命名 变量名无冲突问题<br/>
		import * as name from "./modeles" 全部导入<br/>
	2,默认导出 export default a 只有一个 只能在文件中写一遍<br/>
	  命名导入 import b from "./modules" 命名随意<br/>
		   console.log(b)<br/>


npm install lodash --save<br/>
lodash 按需加载 import findIndex from "lodash/findIndex"<br/>
babel 将es6转换es5<br/>
webpack 模块导入导出 打包工具<br/>
react 用es6 jsx技术<br/>
angular 用typescript技术<br/>


引入react方式<br/>
	核心包react与react-dom<br/>
import React from "react" //格式模板<br/>
import ReactDom from "react-dom"//至此两行必须 本身规定<br/>


react 允许使用js写之中html语法<br/>
jsx严格区分大小写 标签必须闭合 单闭合标签后加斜杠 <input type="text"/> 一个jsx节点必须包裹在一个闭合标签内<br/>
jsx内部嵌入js语法 使用大括号内部必须是一个值<br/>
```jsx 注释
	1, //xxx
	2, /*xxx*/
	3, {
		    //<h1></h1>
	   } 加大括号变成jsx才能注释否则解析网页上显示 大括号不能与注释一行
ReactDom.render 只更新文本节点改变的地方
组件
	函数式声明组件 函数名首必须大写
	function Welcome(){ 写组件
		return <h1>hello</h1>
	}
	ReactDom.render(<Welcome/>,document.getElementById("root")) 使用组件
	组件一定复用 组件代码100行左右

```
新建目录 Component 放组件<br/>


```
import React from 'react'
class App extends React.Component{}
可写成
import React,{Component} from 'react'
class App extends Component{}
```

#react
单页面应用<br/>
css全局使用 尽量所有名称不重复<br/>

react内部有props属性 接收父组件传过的参数 如果是函数组件函数的第一个参数默认是props<br/>
如果是es6 class组件 组件内部使用this.props获取props<br/>


props对象只读<br/>
当父组件传给子组件一个react节点的时候子组件使用this.props.children接收<br/>

```
constructor(){
	super()
	//
	this.handleClick=this.handleClick.bind(this)
}

```
给react组件中的节点绑定事件必须使用行内事件方式 事件名称驼峰命名 有个问题就是当在行内绑定事件的时候事件函数内部的this就会指向window所有在组件内部声明事件函数时通常使用箭头函数也可使用constructor方法在其内部改变事件函数的this指向<br/>

react事件函数最后一个参数默认是事件对象<br/>

```
state={
	num:1
}
let {num}=this.state
setState({
	num: num+1
})
```
组件名称首字母大写<br/>


函数方式写组件<br/>
```
function App(){
  return <h1>hello</h1>
}
```

组件文件夹首字母大写<br/>
多个单词组成的话驼峰命名<br/>
文件夹下的js首字母大写 css全部小写  使用多个单词最好使用-连接<br/>


#组件复用
props默认属性 值是对象 该对象内部存储的是父组件传过来的值<br/>
在子组件内部获取props使用 this.props<br/>
props只读不可改变<br/>


jsx内部嵌套js(必须是一个值)<br/>
<button>{text||"按钮"}</button><br/>


props默认有一个children属性<br/>


在一个组件内部使用另外组件<br/>
```
<Wrap>
	<Button/>
</Wrap>
```

bind方法 函数名.bind(对象)<br/>
返回一个新的函数 和原函数内部功能一样 但是函数内部this已经指向了bind方法 的第一个参数<br/>
在该实例任何地方使用 handleClick()<br/>


state状态组件的state变 组件重新渲染 页面就改变 state是一个对象<br/>
使用this.state.xxx状态值<br/>


使用setState修改state值<br/>


setState异步操作 异步阻塞 同步非阻塞<br/>


组件里使用setInterval当作属性写
```
this.timer=setInterval( ()=>{
	this.setState({
		eat:eats[Math.floor(Math.random()*eats.length)]
	})
},1000)
requestAnimationFrame setTimeout的另外写法 依硬件性能执行
```

修改数组元素
```
state={
	arr=[1,2,3]
}
let arr1=this.stat.arr
arr.push(4)
this.setState({

})
```

当组件中放一组相同jsx节点时需要给每个节点一个唯一的key值这个key值最好是一直不变的
```<button key={index}></button>
```

子组件修改父组件的状态值<br/>
将父组件改变状态值的方法(函数)当做props传递给子组件 让子组件执行这个方法(函数) 从而子组件可以改变父组件的状态值<br/>


constructor函数内部不做设置拿不到父组件传过来的props 想要拿到需要在constructor函数传一个props参数 并且需要在super方法内传一个参数 props这样就可以在constructor内部获取到props<br/>
```
constructor(props){
	super(props)
	this.state={
		show:this.props.show
	}
}
```
组件生命周期<br/>
组件实例首次创建和插入DOM中时调用下面四个方法<br/>
```
constructor()
componentWillMount()执行一次
render()
componentDidMount()执行一次 通常当页面出现时绑定事件用 获取数据
```

属性props或状态state的改变会触发一次更新 当一个组件在被重渲时 这些方法 将会被调用<br/>
当修改state时下面生命周期函数会被执行除componentWillReceiveProps()外执行	 此时在这些函数内不能修改state<br/>
```
componentWillReceiveProps()只在修改props调用
shouldComponentUpdate()
componentWillUpdate()
render()
componentDidUpdate()
```

组件销毁或不被挂载时执行
```
componentWillUnmount()
```

当父组件修改子组件状态时需要父组件传props修改子组件状态 但是props传递时有五个周期周期函数被触发只有componentWillReceiveProps这个生命周期函数可以修改state<br/>


组件默认props<br/>
在class外写<br/>
```Modal.defaultProps={
	title:"default title"
	children:<p>默认内容</p>
}
```

一个事件写两个函数
```onClick={
	()=>{
		this.handleClose()
		this.props.onCancle()
	}
}
onClick={
	()=>{
		this.handleClose()
		onClacle && onCancle()
	}
}
```
合并对象style style1
```let New=Object.assign({},style,style1)
```

react获取真实dom<br/>
```
<button ref={xx=>this.btn=xx}></button>

```
ref函数内部参数xx代表真实dom<br/>
this.xx=btn将真实dom赋值给组件的xx属性<br/>
利用ref在父组件中得到子组件<br/>
父组件直接可以调用子组件方法<br/>
ref 
	> 1获取真实dom节点<br/>
	> 2获取组件<br/>


this.button 获取button组件<br/>
```
<button></button>
```

报警
```
<input value="x></input>
```
无报警
```
<input defaultValue="x></input>
```

受控组件 
		> 1将变化的值设置为state<br/>
		> 2修改state使用onChange事件<br/>
非受控组件 value不受state控制 只能使用真实dom节点获取<br/>
		都有	
			>1value
			>2checked
			>3selecte
		变化的 值不受state控制 只能使用dom节点获取

```
<form action="https://www.baidu.com" method="GET">//GET||POST
	用户名<input type="text" name="username"></input>
		<input type="submit"></input>
</form>如果不使用form本身提交功能传递数据而使用ajax提交依然想使用type=sumbit按钮提交的话注意要阻止submit按钮的默认事件event.preventDefault()
```

如果一个带参数的事件函数 要使用event参数 需要把event放在参数最后面<br/>


单页面应用SPA<br/>


单个页面传网上<br/>
```
reduce((sum,item)=>{return sum+item.price*item.count},0)
```


修改子组件
```
ref={goods=>this.goods=goods}
```

...对象展开





以下为格式
```
return (
    <Router> 
      <div>
          <ul>
              <li><Link to=""></Link></li>
              <li></li>
          </ul>
        <Route path="/" exact//严格匹配 component={Home}/>
        <Route path="/about" component={About}/>
      </div>
    </Router>
  )
```

react路由<br/>
装react-router-dom包<br/>


#动态路由
```
<div>
    <h1>about</h1>
    <ul>
      <li>
        <Link to={`${match.url}/dijia`}>dijia</Link>
      </li>
      <li>
        <Link to={`${match.url}/poi`}>poi</Link>
      </li>
    </ul>
    <Route path={`${match.url}/:name`} component={Dijia}/>//动态路由 匹配变量name页面
  </div>
```


其它页面重定向到404 
```
return <Redirect form={props.match.url} to="/404"/>
```


重定向
```
<Switch>
  单一匹配 只要一个成功匹配 其它则不匹配
</Switch>
Redirect
```

NavLink完全替代 Link<br/>


exact严格匹配<br/>


HushRouter可替代BrowserRouter<br/>


history<br/>
go<br/>
goBack<br/>
push想到哪儿是哪儿<br/>


withRouter将不是路由的组件变成路由<br/>
export default withRouter(help)<br/>


ajax异步页面局部刷新<br/>


后台发送数据<br/>
```
xml
$.ajax()
fetch
axios
```

向后台传递数据
var xml=new XMLHttpRequest()
xml.open("GET","",true)//true异步
xml.send()


GET POST
GET更快
POST更可靠稳定
atom://tree-view

将对象格式转化json格式
JSON.stringify()
将json格式转化对象格式
JSON.parse()




默认GET
$.ajax({
     url:"https://api.github.com/users/yt-theme",
     success:function(data,status,xhr){//data对象 status状态 xhr返回信息
       console.log(data,status,xhr)
       document.getElementById("name").innerHTML=data.login
     },
     error:function(error){
       console.log("获取数据失败")
       console.log(error)
     }
   })


//post向服务器发数据
   //设置发送数据类型contentType:"application/json"
   $.ajax({
     url:"https://cnodejs.org/api/v1/accesstoken",
     method:"POST",
     contentType:"application/json",
     data:'{"accesstoken":"5824f872-38c8-414f-8743-8b4fcd2ac91c"}',
     success:function(data,status,xhr){
       console.log(data,status,xhr)
       document.getElementById("name").innerHTML=data.login
     },
     error:function(error){
       console.log("获取数据失败")
       console.log(error)
     }
   })


//es6获取数据
   fetch("https://api.github.com/users/yt-theme")
     .then(function(data){
       return data.json()
     }).then(function(obj){
       console.log(obj)
     }).catch(function(){
       console.log(111)
     })


axios GET 数据
   axios.get("https://api.github.com/users/yt-theme")
     .then(function(res){
       console.log(res.data)
     })
     .catch(function(err){
       console.log(err)
     })


   // axios POST 数据

axios.post("https://cnodejs.org/api/v1/accesstoken",{
     accesstoken:"5824f872-38c8-414f-8743-8b4fcd2ac91c"
   })
     .then(function(res){
       console.log(res.data)
     })


react创建dom节点使用
dangerouslySetInnerHTML={<xxx></xxx>}


文字超出后显示三个点
text-overflow:ellipsis


本地存储
local Storage浏览器一直存储
localStorage.token=token
localStorage.clear(“token”)
sessionStorage用户关闭浏览器清除


将src打包生成静态文件
npm run build


material-ui


ant-design
npm install antd –save


serve .
将本地文件夹放到服务器上用本地可访问
安装
sudo npm i serve -g


webpack作用打包 压缩代码 给文件名加哈希值
.sass
.sess
建立webpack配件文件于根目录
webpack.config.js
装包
{
 "name": "webpack-react",
 "version": "1.0.0",
 "description": "webpack react",
 "main": "index.js",
 "scripts": {
   "build": "./node_modules/.bin/webpack"
 },
 "author": "yt-theme",
 "license": "ISC",
 "devDependencies": {
   "babel-core": "^6.26.0",
   "babel-loader": "^7.1.2",
   "webpack": "^3.10.0"
 }
}


编译es6 7 8装包
npm install babel-preset-env –save-dev
webpack.config.js之中使用babel-loader编译成通用的代码
use:{
           loader:'babel-loader',
           options: { 				//option是babel-loader配置参数
             presets: ['babel-preset-env'],
           }
         }
编译react装包

npm install babel-preset-react
webpack.config.js配置加入
use:{
           loader:'babel-loader',
           options: {
             presets: ['babel-preset-env','babel-preset-react'],
           }
         }
webpack.config.js加入
devtool: 'inline-source-map',
执行npm run build在命令行中查看react报错源位置


默认webpack打包js不打包css安装
npm install --save-dev css-loader style-loader
webpack.config.js加入
rules: [
       {
         test: /\.js$/,
         exclude: /node_modules/,
         use:{
           loader:'babel-loader',
           options: {
             presets: ['babel-preset-env','babel-preset-react'],
           }
         }
       },
       {
         test: /\.css$/,
         use: [ 'style-loader', 'css-loader' ]   //有先后顺序
       }
     ]


生产环境将css打包出去
npm install --save-dev extract-text-webpack-plugin


webpack


redux 状态容器
安装redux包
store是redux核心概念之一
内部state会存到store

利用es6的默认参数default params
把初始状态值initialState传给state参数
通过getState()接口可以读到store数据

combineReducers合并redux

装react-redux 订阅



数组接口
.map()
返回新数组
数组元素有变化
数组长度不变

.filter()
数组长度变

.find()
返回一个元素

.reduce()
万能接口
语法
const productsById=products.reduce((num,product)=>{
	return num
}


函数式编程
const users=[
  {
    name:"peter",
    gender:"male"
  },
  {
    name:"peter3",
    gender:"male"
  },
  {
    name:"peter2",
    gender:"female"
  }
]
// var tmp=[]
// for(var i=0;i<users.length;i++){
//   if(users[i].gender==="female"){
//     tmp.push(users[i])
//   }
// }
Array.prototype.filter=function(callback){//写一个filter方法给数组
  let tmp=[]
  for(let i=0;i<this.length;i++){
    if(callback(this[i])){
      tmp.push(this[i])
    }
  }
}
const check=users.filter(users=>{
  return users[i].gender==="female"
})
console.log(check);


设计规范
Material Design
https://www.mdui.org/

sass写css规范

使用styled-components做样式

用styled-components思路加样式可把css分成全局css和组件内css两部分
如图建立&&global.css
如图写
然后导入global.css
定情局部样式首先
安装styled-components
写样式思路
	在展示组件中添加”带样式组件”然后在当前组件内使用,所有样式只作用于当前组件,css是绝对不复用,复用是以组件为单位
以按钮复用为例
	1,在组件导入
	 import styled from "styled-components"
	2,写法如图
即基本用法首先导入styled
然后在文件末尾定义Wrap变量,这里首字母大写因为Wrap会作为一个所谓的”带样式的组件”来使用
`styled.div`表示 Wrap是基于html原生的div,也就是默认会继承div的所有样式，例如width:100%;,然后倒引号之中再来添加样式，这里只是添加 背景色
然后Wrap为组件来使用
下图button->Button
函数式编程数据不可改性
const res=[...comments].reserve()

为什么有id
数据库有
纯前端生成id
引入库shortid
const id=shortid()

兄弟组件之间进行通信
/////////////////////////
redux为数据管理工具
一切数据保存在store&&组件之中不存在state
/////////////////////////
使用redux 安装react-redux
import {createStore} from "redux"//创建库
const store =createStore(rootReducer)//rootReducer必写参数

react-redux负责连接react和redux

filter()筛选

redux-thunk



react styled-components过渡效果
react-transition-group

import {CSSTransition} from “react-transition-group”











vue
npm install -g vue-cli
vue-init webpack 项目名

npm run dev在开发环境运行

v- 的作用是提示编译环境这不是一个html原生属性而是一个vue指令,model的意思是数据模型

	a要使用 v-model 指令，等号后面是一个字符串，里面写变量名，这里是 	message 
      b变量要声明一下才能使用，也就是要到 data 里面，添加 message 冒号，值是空字符串 
      c真正在 script 标签中用的时候，变量名前面要添加 this 






slice()切片,但是里面不写值,相当于从头切到末尾,所以得到原始数组一个拷贝
另外获得数组拷贝方式是ES6展开运算符


vue传参
title内容写在data中如下图所示
	其中v-band:title简写
				:title

vue使用router单页面应用路由
npm i vue-router

(1)main.js


(2)router.js


采用history模式不显示网址#
mode:”history”,

无刷新跳转 <router-link></router-link

动态路由
有动态参数
获取参数this.$route.params.id

# json-server
json-server数据库服务器<br/>
npm i -g json-server<br/>
在项目根目录建立api/db.json<br/>
db.json
```{
"comments":[
  {
    "id":"1",
    "body":"af"
  },
  {
    "id":"2",
    "body":"wqr"
  }
]
}
```
json-server --watch db.json -p 3008运行<br/>
其中3008是端口<br/>
浏览器输入http://localhost:3008/comments<br/>



### replace()技巧
>replace只替换第一个匹配项 <br/>
>加上/g会将所有可匹配项完全替代

```
let s = "bob"
const replaced = s.replace("b", "l")
// replaced "lob"
```
```
let s = "bob"
const replaced = s.replace(/b/g,"l")
// replaced "lol"
```
### sort()技巧
默认使用字母数字(字符串Unicode码点)排序
```
[1, 2, 5, 10].sort()
// [1, 10, 2, 5]
```
如果需要由大到小排序
```
[1, 2, 5, 10].sort((a,b) => b-a)
// [10, 5, 2, 1]
// a-b从小到大
```