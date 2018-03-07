### DOM节点/元素
    document object medum 文档对象模型
    1. 元素节点
    2. 属性节点
    3. 文本节点
### API
    接口
### js代码
    1. 严格区分大小写
    2. 非js代码套套引号
### 阻止跳转方法
```
    return false
    
    event.preventDefault()
```
### 控制台输出
```
    console.log()
```
### let ES6声明方式
1. 拥有块级作用域 
2. 只要在大括号内声明就会形成作用域
3. 1,拥有块级作用域 只要在大括号内声明就会形成作用域
4. 变量声明不提升
5. 在let作用域内声明之前使用变量会报错
```
 { 
 	let a=10 console.log(a)
 } 
 /*简写封装形式 const 常量*/
```
### 字符串模板
```
 var username="a"
 var age=10 var 
 c="my name is"+username 
 var c=`my name is ${username}`
```
### mouseenter/mouseleave与mouseover/mouseout区别 -> 触发方式不一样
    前者触发一次,后者可触发多次子元素
### 删除字符串左右空白符
```
    .trim()
```
### 函数
	形参:函数声明于小括号后面,形参相当于在函数内部声明了变量并且没有赋值,当调用函数时传入了实参的话相当于给形参赋值
	实参:调用函数时从小括号传入的
	每个参数用括号隔开
```
	function name(a,b){ //函数首字母不大写 a,b形参
		//语句集合
	}
```
### 箭头函数

> 1. 参数除了一个之外必须使用小括号 当有一个参数可省略小括号
> 2. 箭头右面是要做的事,当要做的事不止一句时必须加上大括号
> 3. 当只有一句执行时,可以省略大括号 但是同时这名会被当作该函数的返回值
> 4. 当需要写返回值时需要在大括号最后面添加return
> 5. 箭头函数内的this对象是定义时所在的对象而不是使用时所在的对象
> 6. 不可以当作构造函数new命令
> 7. 箭头函数不可使用arguments对象,reset参数代替

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

函数声明时在小括号内部直接给参数赋值 相当于给参数默认值
####  es6函数参数集合
```
let sum=(...rest)=>console.log(rest) //rest剩余参数
```
### 作用域
	1. 只有函数有作用域
	2. 声明在作用域内的变量/函数,其他不相关的作用域内是不能访问的,只有子作用域可以访问或修改
	3. 最大作用域为创建的全局变量
	4. 父级作用域不能访问子集作用域
	5. 全局变量越多,越会污染全局环境
### 函数返回值
```
	return x
```
	1.返回值必须在函数后面写
	2.return 作用(1)跳出函数执行(2)返回结果
### 将一个匿名函数赋值给一个变量,相当于是创建一个函数并且这个函数也就像变量一样
```
	var fun = function(){
		console.log(1)
	}
```
### 对象->object
	1. 内置对象:内部封闭的对象 (数组,日期,正则表达式,数字,数学,字符串,布尔)
	2. 自定义对象:自己封装或模拟
	3. 浏览器对象:浏览器信息/属性
### 创建对象
```
	var obj = {
		a:1,
		b:2,
		name:"123"
	}
```
### 数组
	定义数组
```
	var arr = [ 1, 2, 3 ]
	var src = arr[0] //数组内容的第一项赋值给src
```
### 数组方法
	1. arr.push()    向数组最后添加一个或多个元素,并返回新的数组长度
	2. arr.pop()     数组删除其中最后一项,返回被删除的元素
	3. arr.unshift() 向数组前面添加一个或多个元素并返回数组长度
	4. arr.shift()   删除数组第一个元素并返回删除的元素
	5. arr.concat()  合并两个或多个数组
```
	var a = [ 1, 2, 3 ]
	var b = [ 4, 5, 6 ]
	var d = [ 7, 8, 9 ]
	var c = a.concat( b, d )
	console.log( c )
	// [ 1, 2, 3, 4, 5, 6, 7, 8, 9 ]
```
	6. arr.reverse() 颠倒数组顺序
	7. arr.join()    将数组以某个连接符合并为字符串并返回这个字符串,原数组不变
```
	var num  = [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 ]
	var stri = num.join( "a" )
	console.log( stri )
	// 1a2a3a4a5a6a7a8a9a0
```
	8. arr.slice(a,b)数组截取,从a开始(包括a)截取到b(不包括b),返回截取的数组,原数组不变
```
	var num    = [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 ]
	var newArr = num.slice( 1,2 )
	console.log( newArr )
	// [ 2 ]
```
	9. arr.splice()  添加/删除元素,返回一个数组,数组内部放被删除的元素,如果不进行删除则返回一个空数组
```
	num.splice( a, b, c )/*
							a 添加/删除位置
							b 删除个数
							c 添加的元素
						 */
	num.splice( a, b, c, d, e, f )/*
									其中cdef为添加多个参数								
								  */
	num.slice( 1, 0, 1 )/*
							其中0代表不删除
						*/
```
	10. arr.indexOf()检测数组里是否有某一个元素
```
	var index = num.indexOf( 5 ) //存在则返回第一个存在的索引,否则返回-1
```
	11. arr.sort()   数组排序,直接使用.sort()会将数字和字符串近首字符顺序排序
```
	var arr = [ "b", "a" ]
	arr.sort()
	// ["a", "b"]
```
	12. arr.filter() 筛选
```
	var arr    = [ 0, 6, 66 ]
	var newArr = arr.filter( function( item ){ // function必写参数
		return item > 10
	})
	console.log( newArr ）
	// [ 66 ]
```
	13. arr.find()   返回找到符合条件的第一个元素
```
	var pic = arr.find( function( item, index, array ){
		return item.limit == false
	}
```
	14. arr.map()    映射用于返回新的长度一样的数组,一般把数据变成标签
```
	var picArr = arr.map( function( item ){
		var pic = $( "<img>" )
		return pic
	})
```
### 数学对象Math
	1. rendom()      随机数
```
	var num = Math.rendom()              // rendom()返回0-1之间的随机数
```
	2. floor()       取整数
```
	Math.floor( num )
```
	3. ceil()        上进,小数点后有数就进
	4. round()       四舍五入
### 日期对象Date
```
	var time  = new Date()               // 创建一个日期对象
	var year  = time.getFullYear()       // 获取年
	var month = time.getMonth()          // 获取月
	var day   = time.getDate()           // 获取日
	var week  = time.getDay()            // 获取星期
	var hours = time.getHours()          // 获取时
	var minute= time.getMinutes()        // 获取分
	var second= time.getSeconds()        // 获取秒
	var msecs = time.getMilliseconds()   // 获取毫秒
	time.getTime()                       // 返回从1970.1.1 0:0:0 到现在已过毫秒数,可用于获取到一永不重复数
```
### 计时器
	1. setInterval()    计时器
```
	function fun(){
		console.log("stop")
	}
	var timerSetInterval = setInterval( fun, 10 )               // 函数名, 毫秒数
```
	2. clearInterval()  清除计时器
```
	clearInterval( timerSetInterval )
```
	3. setTimeout()     异步计时器
	4. clearTimeout     清除setTimeout()
### 正则表达式
		>RegExp
		>用来检测文本的规则
	1. 创建正则表达式
```
	var re    = /a/                         // 写正则表达式规则
	var str   = "abc"
	var bool  = re.test( str )              // 使用re这个正则表达式检测字符串str,检测成功返回true,反之false
	console.log( bool )
	// true
```
	2. 正则表达式规则
```
	[]                                      // 一位字符
	var re  = /[abc]/                       // 检测a或b或c
	var str = "12aaaxc"
	console.log(re.test(str))               // True
```
```
	var re  = /[abc][123]/			// 有 a或b或c 和 1或2或3
	var str = "a1"
	console.log(re.test(str))               // true
	var str = "aa11"
	console.log(re.test(str))		// true
	var str = "aa"
	console.log(re.test(str))               // false
```
```
	[0-9]                                   // 检测一位数字
	[a-z]                                   // 一位小写字母
	[A-Z]                                   // 一位大写字母
	[A-z]                                	// 一位字母或下划线
	[]+                                     // 多位
	[]*                                     // 0到多位
	[]?                                     // 0位或1位
	[]{1,}                                	// {}中要检测对象的出现次数
```
### a==1&&a==2&&a=3
对象方法里ValueOf和toString在对象比较时会自动执行
```
	const a = {
    	i : 1,
        toString : function () {
        	return a.i++
        }
    }
    if ( a == 1 && a == 2 && a == 3 ){
    	console.log("HelloWorld")
    }
    //HelloWorld
```
### var a=x||0
	当x为undefined时a=0

### 类
```
//class 类
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
#### 累加器 reduce()
#### Object.keys() 获取对象所有属性值的数组

### 导入出模块
> require("./aaaaaaa.js") 导入模块<br/>
es6将每个js当成一个模块

es6模块导入导出 模块导入必须在当前模块最顶端

1. 命名导出
```
export{a} //加大括号
```
2. 命名导入 
```
import b from "./modules" 命名随意
console.log(b)
```
```
import {a} from "./module" //.js可省略
```
命名导出 导入的变量名和导出必须一致
```
import {b as a} from "./modules" 这as相当重命名 变量名无冲突问题
```
```
import * as name from "./modeles" 全部导入
```
3. 默认导出 
```
export default a 只有一个 只能在文件中写一遍
```