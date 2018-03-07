### node创建服务器

```
let http = require('http')
// 发送HTTP头部,HTTP状态值: 200: OK,内容类型: text/plain
http.createServer(function (request, response) {
    response.writeHead(200, {'Content-type': 'text/plain'})
    response.end('Hello World')
}).listen(8888)
console.log('server as running at http://127.0.0.1:8888/')
```

关于Content-Type<br/>
互联网媒体类型

```
text/html   HTML格式
text/plain   纯文本格式
text/xml     XML格式
image/gif    gif图片格式
image/jpeg  jpg图片格式
image/png   png图片格式

applicatioin/xhtml+xml   XHTML格式
application/xml          XML数据格式
application/atom+xml     Atom XML聚合格式
application/json         JSON数据格式
application/pdf          pdf格式
application/msword       Word文档格式
application/msword       Word文档格式
application/octet-stream 二进制流数据(常见文件下载)
application/x-www-form-urlencoded  <form 
encType=””>中默认的encType，form表单数据被编码为key/value格式发送到服务器（表单默认的提交数据的格式）

multipart/form-data            表单上传文件格式
```