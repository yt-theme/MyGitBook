#### ajax
数据交互技术

> AJAX技术的基础是XMLHttpRequest对象<br/>
> XMLHttpRequest用于在后台与服务器交换数据,可在不重新加载整个网页的情况下,对网页的某部分进行更新

创建XMLHttpRequest对象

```
let a = new XMLHttpRequest()
```

检测浏览器是否支持XMLHttpRequest

```
let XH
if (window.XMLHttpRequest) {
	XH = new XMLHttpRequest()
} else {
	XH = new ActiveXObject('Microsoft.XMLHTTP')
}
```

XMLHttpRequest向服务器发送请求

> open()规定请求的类型,URL,是否异步(true:异步）<br/>
> url为服务器上的文件,可以是任何类型<br/>
> send()将请求发送到服务器 (send(string)仅用于POST请求)

```
XH.open('GET', 'myUrl', true)
XH.send()
```

GET请求

```
XH.onreadystatechange = function(){
	if (XH.readyState ==  && XH.stateus == 200){
        console.log(XH.responseText)
    }
    XH.open('GET', 'myUrl', true)
    XH.send()
}
```

防止请求的是缓存的结果可加一个随机ID

```
XH.open('GET', 'xxx.asp?t=' + Math.rendom(), true)
XH.send()
```

GET添加信息

```
XH.open('GET', 'xxx.asp?itema=asa&name=win', true)
XH.send()
```

POST请求

```
XH.open('POST', 'xxx.asp', true)
XH.send()
```

POST发送类表单使用setRequestHeader()添加HTTP头

> setRequestHeader(header, value) header为头名称,value为头的值

```
XH.open('POST','xxx.asp',true)
XH.setRequestHeader('Content-type','xxx/xx')
XH.send('itema=asa&name=win')
```

### AJAX 服务器响应
> responseText属性 获得字符串形式的响应数据<br/>
> responseXML属性  获得XML形式的响应数据

如果来自服务器的响应并非XML,使用responseText

```
console.log(XH.responseText)
```

```
<html>
    <head>
    <script type="text/javascript">
    function loadXMLDoc() {
        var xmlhttp;
        if (window.XMLHttpRequest) {
            xmlhttp=new XMLHttpRequest();
        } else {
            xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
        }
        xmlhttp.onreadystatechange=function() {
          if (xmlhttp.readyState==4 && xmlhttp.status==200) {
            document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
          }
        }
        xmlhttp.open("GET","/ajax/test1.txt",true);
        xmlhttp.send();
    }
    </script>
    </head>
<body>
<div id="myDiv"><h2>Let AJAX change this text</h2></div>
	<button type="button" onclick="loadXMLDoc()">通过 AJAX 改变内容</button>
</body>
</html>
```

onreadystatechange事件

> 当readyState改变时,触发onreadystatechange事件<br/>
> readyState属性存有XMLHttpRequest状态信息

XMLHttpRequest对象三个重要属性

```
|---------------------|---------------------------------------
|         属性        | 描述
| onreadystatechange  | 存储函数或函数名,每当readyState属性改变就会调用该函数
|---------------------|---------------------------------------
|      readyState     | 存有XMLHttpRequest状态,
|                     | 0: 请求未初始化
|                     | 1: 服务器连接忆建立
|                     | 2: 请求已接收
|                     | 3: 请求处理中
|                     | 4: 请求完成且响应就绪
|---------------------|---------------------------------------
|            status   | 200: 'OK'
|                     | 404: 未找到页面
```

Callback函数

>  以参数形式传递给另一个函数

```
<html>
<head>
<script type="text/javascript">
    var xmlhttp;
    function loadXMLDoc(url,cfunc){
        if (window.XMLHttpRequest) {
            xmlhttp=new XMLHttpRequest();
        } else {
            xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
        }
        xmlhttp.onreadystatechange=cfunc;
        xmlhttp.open("GET",url,true);
        xmlhttp.send();
    }
    
    
    function myFunction() {
    	loadXMLDoc("/ajax/test1.txt",function() {
			if (xmlhttp.readyState==4 && xmlhttp.status==200) {
       			document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
        	}
      	});
	}
</script>
</head>
<body>

<div id="myDiv"><h2>Let AJAX change this text</h2></div>
<button type="button" onclick="myFunction()">通过 AJAX 改变内容</button>

</body>
</html>

```

动态请求数据例子

```
<html>
<head>
<script type="text/javascript">
    function showHint(str) {
    	var xmlhttp;
        if (str.length==0) { 
            document.getElementById("txtHint").innerHTML="";
            return;
        }
        if (window.XMLHttpRequest) {
            xmlhttp=new XMLHttpRequest();
        } else {
            xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
        }
   		xmlhttp.onreadystatechange=function() {
            if (xmlhttp.readyState==4 && xmlhttp.status==200) {
                document.getElementById("txtHint").innerHTML=xmlhttp.responseText;
            }
        }
        xmlhttp.open("GET","/ajax/gethint.asp?q="+str,true);
        xmlhttp.send();
    }
</script>
</head>
<body>

<h3>请在下面的输入框中键入字母（A - Z）：</h3>
<form action=""> 
姓氏：<input type="text" id="txt1" onkeyup="showHint(this.value)" />
</form>
<p>建议：<span id="txtHint"></span></p> 

</body>
</html>
```