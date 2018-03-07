html5新动画api

> 后接一个回调作为参数

```
ani = requestAnimationFrame(callback)
```

```
let timer = requestAnimationFrame(function() {
	console.log(1)
})
console.log(timer)
```

cancelAnimationFrame取消动画

```
let timer = requestAnimationFrame(function() {
	console.log(1)
})
cancelAnimationFrame(1)
```

制作进度条效果

```
<div id="myDiv" style="background-color: lightblue;width: 0;height: 20px;line-height: 20px;">0%</div>
<button id="btn">run</button>
<script>
var timer;
btn.onclick = function(){
    myDiv.style.width = '0';
    cancelAnimationFrame(timer);
    timer = requestAnimationFrame(function fn(){
        if(parseInt(myDiv.style.width) < 500){
            myDiv.style.width = parseInt(myDiv.style.width) + 5 + 'px';
            myDiv.innerHTML =     parseInt(myDiv.style.width)/5 + '%';
            timer = requestAnimationFrame(fn);
        }else{
            cancelAnimationFrame(timer);
        }    
    });
}
</script>
```
