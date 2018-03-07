### 查找一个字符串中所有子串位置

```
var str = "I think of other ages that floated upon the stream of life and love and death"
var positions = new Array();
function searchSubStr(str,subStr){
	var pos = str.indexOf(subStr)
	while(pos>-1){
		positions.push(pos)
		pos = str.indexOf(subStr,pos+1)
	}
}
searchSubStr(str,"o");
alert(positions);//8,11,29,37,51,64
```
