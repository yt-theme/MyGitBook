#### cookies/sessionStorage/localStorage
cookie储存在用户本地,标识用户身份,过期时间内有效,数据不能超4k<br/>
localStorage持久数据,浏览器关闭后数据不丢失<br/>
sessionStorage临时存储数据,浏览器窗口关闭后自动删除
#### HTML5离线储存
> 用户没有网络时,可正常访问站点与应用,网络连接时,更新用户电脑上缓存文件

离线存储加载方法<br/>
1.浏览器发现html标签有manifest属性,则请求manifest文件<br/>
2.如果是每一次访问页面,则根据manifest描述将资源存储<br/>
3.如果是访问过的资源则浏览器使用离线页面,然后比较本地与新manifest文件<br/>
4.如果manifest文件改变则加载新文件<br/>
5.如果manifest文件不改变则无操作<br/>

##### cache manifest文件
1. manifest是一个后缀minifest文件
2. 浏览器按manifest文件规则来访问或更新页面

##### minifest特点
1. 离线浏览
2. 速度快
3. 减轻服务器负载

#### 使用

1.创建一个和html同名manifest后缀文件


```
touch index.html
touch index.manifest
```
2.index.html中<html>标签加入属性
```
<html lang="en" mainfest="index.manifest">
```
3.manifest文件中写入
```
CACHE MANIFEST
#version 0.1

CACHE:
	index.css
	main.css
    img/logo.png
NETWORK:
	*
FALLBACK:
	*.html /404.html
```
> CACHE:必须,哪些文件需要缓存,路径可相对可绝对,不可使用'×' <br/>
> NETWORK:可选,绕过缓存直接读取的文件,可使用'×'<br/>
> FALLBACK:可选,后备页面,资源不能访问时则使用该页面

#### 缓存更新
> 通过manifest<br/>
> 通过javascript<br/>
> 清除浏览器缓存

js更新缓存方法
```
window.applicationCache.update()
```

> 不同浏览器对缓存数据容量限制不同(5MB)
> 更新某缓存失败则继续全部使用旧缓存
> manifest与引用manifest的文件同源同域
> FALLBACK和manifest文件同源
> manifest文件发生改变,资源请求本身也触发更新


#### window.applicationCache方法
```
oncached         //当离线资源存储完成后触发
onchecking       //当浏览器对离线资源更新检查时触发
ondownloading    //当浏览器开始下载离线资源时触发
onprogress       //池浏览器在下载每一个资源时触发
onupdateready    //当浏览器对离线资源更新完成后触发
ononupdate       //当检查更新发现没有资源更新时触发
```


#### 清除浏览器缓存
firefox
```
//缓存位置
/home/<name>/.cache/mozilla/firefox
```
chrome/chromium
```
//输入在网址栏
chrome://settings/clearBrowserData 
```

#### 浏览器兼容
```
// 数据存储
if (window.localStorage) {
    localStorage.setItem("menuTitle", arrDisplay);
} else {
    Cookie.write("menuTitle", arrDisplay);
}

// 数据读取
var strStoreDate = window.localStorage? localStorage.getItem("menuTitle"): Cookie.read("menuTitle")	

// 存储strStoreDate
strStoreDate.split(",").each(function(display, index) {
    //根据存储的display触发相对应的动作
});
```
