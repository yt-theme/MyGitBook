### 移动端

> 移动端网页<br/>
> 移动端Web App 有些使用浏览器私有功能

meta

```
<meta name="viewport" content="width=device-widthm, initial-scale=1, user-scalable=no, minimum-scale=1, maximum-scale=1"/>
```

详细

```
device-width 	// 设备宽度
initial-scale 	// 初始绽放比例
minimum-scale	// 允许用户缩放到的最小比例
maximum-scale	// 允许用户绽放到的最大比例
user-scalable	// 用户是否可以手动缩放
```

辅助功能

```
// 设备宽高缩放比
<meta name="viewport" content="width=320, initial-scale=1.5">

// 禁止自动识别电话号码和邮箱
<meta content="telephone=no, email=no" name="format-detection"/>

// 苹果手机删除默认的工具栏和菜单栏,网站开启对Web App程序支持
<meta content="yes" name="apple-mobile-web-app-capable"/>

// 苹果手机在Web App应用下状态条颜色,默认白色可定义black和black-translucent
<meta name="apple-mobile-web-app-status-bar-style" content="black"/>

// 苹果手机如果把一个Web App添加到主屏幕中,那么从主屏幕中打开这个App则全屏显示
<meta name="apple-touch-fullscreen" content="yes" />

// 苹果手机将应用添加到手机主屏幕会有一个icon可直接进入
<link rel="apple-touch-icon" href="/static/images/identity/HTML5_Badge_64.png" />
```

css3

```
/* 重置 */
body {
	word-wrap: break-word;
	font: 16px/1.5 Helvetica,Arial; /* 通用移动字体 */
	color: #333;
	-webkit-text-size-adjust: none; /* 设置文本不放大 */
}
body * {
	-webkit-tap-highlight-color: transparent; /* 透明点击状态背景色 */
	-webkit-user-select: none; /* 设置元素内的文字及子元素将不被选中 */
}
```

### 一些概念

```
物理像素 physical pixel
设备独立像素 density-independent pixel 密度无关像素 程序使用的虚拟像素 比如CSS像素
CSS像素 抽象 又称设备无关像素 device-independent pixel 简DIPs
屏幕密度 物理像素数量 PPI
设备像素比 device pixel ratio 简dpr 物理像素与独立像素的对应关系 设备像素比 = 物理像素 / 设备独立像素
```

### 一些操作

```
// js获取设备dpr
window.devicePixelRatio

// CSS获取dpr -> webkit & webview
-webkit-device-pixel-ratio
-webkit-min-device-pixel-ratio
-webkit-max-device-pixel-ratio
-webkit-max-device-pixel-ratio
```

### 一些单位
```
// rem相对于根元素<html>的font-size
```

### lib-flexible库

引用

```
// 其中将代码中的{{version}}换成对应的版本号0.3.4
<script src="http://g.tbcdn.cn/mtb/lib-flexible/{{version}}/??flexible_css.js,flexible.js"></script>
```

使用

```
<head>
	<script src="build/flexible_css.debug.js"></script>
	<script src="build/flexible.debug.js"></script>
</head>
```

设置meta

```
<meta name="flexible" content="initial-dpr=2" />
```

参考文献

```
// https://www.w3cplus.com/mobile/lib-flexible-for-html5-layout.html
```
