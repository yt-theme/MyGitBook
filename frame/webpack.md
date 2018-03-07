### 安装

> 提前安装nodejs 见linux笔记

```
# node -v 确定已安装
node -v
```

```
# 使用全局安装webpack可将webpack当作命令用
npm install -g webpack #某些发行版可以需要sudo&root权限
```

### 使用
```
mkdir hello-webpack
cd hello-webpack
npm init
# 生成了package.json
```

```
npm install --save-dev webpack
```

```
ls
# 有node_modules目录
```

```
# 源码
mkdir src

# 输出
mkdir dist

# 源文件
touch src/app.js
```

```
# 输出文件
webpack src/app.js dist/app.bundle.js

# vim dist/app.bundle.js
```

> 监听文件


```
# 监听文件 文件变化时即时输出 开发时经常用
webpack src/app.js dist/app.bundle.js --watch
```

> 压缩文件

```
# 压缩文件 生产环境常用 压缩文件内容 减小体积
webpack src/app.js dist/app.bundle.js -p
```

> 配置文件

```
touch webpack.config.js
vim webpack.config.js

# 内容
module.exports = {
	entry: './src/app.js',
	output: {
		filename: './dist/app.bundle.js'
	}
};

# 使用webpack可执行
webpack

# 可用webpack --watch
webpack --watch

# 可用webpack -p
webpack -p

# 常用命令应该写在package.json中
vim package.json
	# 内容
	{
	  "name": "hello-webpack",
	  "version": "1.0.0",
	  "description": "",
	  "main": "index.js",
	  "scripts": {
		"dev": "webpack --watch",   // 已更改
		"prod": "webpack -p"			// 已更改
	  },
	  "author": "",
	  "license": "ISC",
	  "devDependencies": {
		"webpack": "^3.11.0"
	  }
	}

# package.json更改后可以
npm run dev
# 或
npm run prod
# 这样可执行关键字后的指令
```

### 编写项目
一个例子<br/>
```
# 创建dist/index.html
# 内容
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<script src="./app.bundle.js"></script>
	<body>
	</html>
# 浏览器查看输出
~          
```

当文件名会改变时,需要使用一个插件<br/>

```
# 安装
npm install html-webpack-plugin --save-dev

# 使用
vim webpack.config.js
# 内容
var HtmlWebpackPlugin = require('html-webpack-plugin')
module.exports = {
	entry: './src/app.js',           # 已更改
	output: {
		path: __dirname + '/dist',	  # 已更改
		filename: 'app.bundle.js'     # 已更改
	},
	plugins: [new HtmlWebpackPlugin()] # 新增
};

# 运行
npm run dev

# dist/index.html改变为
# 内容
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Webpack App</title>     # 新增标题 
  </head>
  <body>
  <script type="text/javascript" src="app.bundle.js"></script></body>
</html>

# 如果想改变标题webpack.config.js内容plugins行改为
plugins: [
	new HtmlWebpackPlugin({
		title: 'new title',
	})
]

# 查看变化
npm run dev

# 加内容到页面可使用模板
vim webpack.config.js
# 更改plugins行内容
# 内容
plugins: [
	new HtmlWebpackPlugin({
		title: 'new title',
		template: './src/index.html'
	})
]
# 在src新建index.html
# 内容
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title></title>
</head>
<body>
	<p>webpack content</p>
</body>
</html>
# 再删除 dist/index.html 
rm dist/index.html
# 执行将自动创建目标
npm run dev
# 查看页面
chromium dist/index.html   
# 看到dist/index.html标题空
# 给dist/index.html增加标题 更改<title>行
vim src/index.html
# 内容
    <title><%= htmlWebpackPlugin.options.title %></title>
# 查看页面可看到标题

# 压缩html 编辑webpack.config.js内容plugins行
# 内容
plugins: [
	new HtmlWebpackPlugin({
		title: 'new title',
		template: './src/index.html',
		minify: {
			collapseWhitespace: true
		}
	})
]
# 查看页面源码可看到源码空格被压缩
# hash 获取key使用
# 内容
plugins: [
	new HtmlWebpackPlugin({
		title: 'new title',
		template: './src/index.html',
		minify: {
			collapseWhitespace: true
		},
		hash: true
	})
]
# 页面源码
<!DOCTYPE html><html><head><meta charset="UTF-8"><title>new title</title></head><body><p>webpack content</p><script type="text/javascript" src="app.bundle.js?89b1b400ce37394f881e"></script></body></html>
```

### 使用loader处理css&sass
> 把文件图片等格式转化或处理变成另一类格式

```
# 对于css
# 安装css的loader
npm install --save-dev style-loader
npm install --save-dev css-loader

# 编辑 webpack.config.js
# 内容
var HtmlWebpackPlugin = require('html-webpack-plugin')
module.exports = {
	entry: './src/app.js',
	output: {
		path: __dirname + '/dist',
		filename: 'app.bundle.js'
	},
	module: {            			// 新增
		rules: [
			{
				test: /\.css$/,
				use: ['style-loader','css-loader']
			}
		]
	},	
	plugins: [
		new HtmlWebpackPlugin({
			title: 'new title',
			template: './src/index.html',
			minify: {
				collapseWhitespace: true
			},
			hash: true
		})
	]
};


# 在src新建app.css
touch src/app.css

# 内容
body{
	background:pink;
}

# 在src/app.js导入css
# 内容
import css from './app.css'
console.log("webpack")

# 查看页面变化

```

```
# 对于sass
# 安装sass的loader
npm install sass-loader node-sass webpack --save-dev

touch src/app.scss
vim src/app.scss

# 内容
body {
	background: pink;
	p {
		color: green;
	}
}

# 更改src/app.js内容import行
import css from './app.scss'

```

### webpack-dev-server 实现监听 localhost:xxx端口
```
# 安装
npm install -g webpack-dev-server --save-dev

# 修改package.json内容
"scripts": {
	"dev": "webpack-dev-server",
	"prod": "webpack -p"
}

# 如果想要监听其它端口 webpack.config.js加入
devServer:{
	port:9090
}

# 运行
npm run dev

# 浏览器输入端口地址出现页面

# 运行自动打开浏览器
# webpack.config.js内容devServer改为
devServer:{
	port: 9090,
	open: true
}
# 运行发现浏览器被自动打开页面
npm run dev
```

```
# 跨域
```

### 配置react开发环境
> 需要webpack babel<br/>
> babel 把react的代码jsx转成浏览器可读代码 也可es6 es7等相互转换

```
# 安装
npm install -save react react-dom
npm install --save-dev babel-core babel-preset-react babel-preset-env

# 创建配置文件.babelrc
touch .babelrc
# 内容
{
	"presets": ["env", "react"]
}

# 使用loader转化jsx
# 安装
npm install --save-dev babel-loader

# 添加配置文件webpack.config.js 内容的rules下
{ test: /\.js$/, loader: 'babel-loader', exclude: /node_modules/ },
{ test: /\.jsx$/, loader: 'babel-loader', exclude: /node_modules/ }

# 编辑src/app.js
# 内容
import css from './app.css';
import React from 'react';
import ReactDOM from 'react-dom';
import Root from './Root';

ReactDOM.render(
	<Root></Root>,
	document.getElementById('root')
);

# 编辑src/index.html内容body加一组标签
# 内容
<div id="root"></div>

# 创建src/Root.js
touch src/Root.js
# 内容
import React from 'react';
export default class Root extends React.Component {
	render() {
		return (
			<div style={{textAlign: 'center'}}>
				<h1>hello world</h1>
			</div>;
		)
	}	
}
# 运行
npm run dev
```

### clean-webpack-plugin清除文件是为获得最新编译的文件 先清空输出文件夹下的*.js再编译
```
# 修改webpack.config.js内容entry&output行
# 内容
entry: {
	'app.bundle': './src/app.js'
},
output: {
	path: __dirname + '/dist',
	filename: '[name].[chunkhash].js'
},

# 运行在生产环境
npm run prod

# dist下*.js文件变成app.bundle.(hashValue).js
# 文件内容改变 文件名跟着改变 就知道文件内容有没有改变 就要清除原来的缓存 一般用于线上环境

# 安装
npm i clean-webpack-plugin --save-dev

# 使用
# webpack.config.js内容加入
const CleanWebpackPlugin = require('clean-webpack-plugin')

# webpack.config.js内容plugins行
new CleanWebpackPlugin(['dist']),    # 清空dist文件夹下缓存

```


