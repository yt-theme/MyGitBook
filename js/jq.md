###使用jq将style标签引入jq文件
###选择对象
```
    $(".button-first") //使用css选择器符号
    
    //css属性选择器
    //input[type=button]{width:100px}
    
    :eq //选择和nth-child类似,选择所有xxx中下标为n的对象(从0开始递增)
```
###更改属性
```
    .attr() //也可获取属性
    .attr("属性名","属性值")
    .attr("src","images/egzp.jpg")
```
###获取/设置宽
```
    var kuan=$(".aaa").width
    $(".aaa").width("1000%")
```
###类似bool添加删除
```
    .toggleClass("class") //有这个class就删除,没有就添加
```
###淡出/入
```
    fadeOut() //淡出
    fadeIn() //淡入
```
###消失/出现
```
    hide() //消失
    show() //出现
```
###回调/动画
```
    //动画名(500,function(){
    //    动画执行之后做的事
    //} //动画500ms之后执行
    
    //$("...").animate({},500,function(){
    //    回调函数
    //}
    
    /*例子*/
    $("div").animate({"height","1px"},500,function(){
        $("div").width("200px"})
    })
```
###function内部this
    指向function所在方法的绑定对象
###移动事件
```
    //.mousemove(function(){})
    
    $("div").mousemove(function(event){
        //event 事件对象
    })
```
###事件对象坐标
```
    //鼠标坐标
    event.pageX
    event.pageY
```
###删除元素包括内容
```
    .remove()
```
###判断class是否拥有
```
    .hasClass()
```
```
    var has = $("box").hasClass("active")
    if ( has==true ）{
        $(“box”).removeClass("active")
    }else{
        $(“box”).addClass("active")
    }
```
###属性选择器
```
    $("input=text")
```
###设置/获取属性值
```
    $("span").text("qwq")
    var value=$("input:text").val()
```
###建立标签
```
    var cli=$("<li>")
    
    //标签放入文字
    cli.text("value")
```
###添加元素
```
    a.append(b) //将b添加到a内部
    $("ul").append(cli)
```
###清空元素属性值
```
    $("input:text").val("")
```
###克隆
```
    $("ul").clone()
```
###将b添加到a内部(子级)位置最后一位
```
    a.prepend(b)
```
###将b添加到a后面(同级)位置最后一位
```
    a.after(b)
```
###将b添加到a内部(子级)位置第一位
```
    b.appendTo(a)
```
###将b添加到a内部(同级)位置前一个兄弟
```
    b.insertBefore(a)
```
###是否被选中
```
    x.prop("checked")
```
###遍历
```
    xx.each(function(){}) //遍历集合中所有元素依次做function
```
###是否改变
```
    xx.change()
```
###获取/失去焦点
```
    var fcs="获得焦点"
    var bl="失去焦点"
    $("#username").focus(function(){
        console.log(fcs)
    })
    $("#username").focus(function(){
        console.log(bl)
    })
```
###绑定事件
```
    //为窗口绑定事件
    $(window).keydown(function(){})
    //为body绑定事件
    $("body").keydown(function(){})
```
###执行xx事件所有操作
```
    $("div").trigger("click")
```
###滚动条
```
    $(window).scrool(function(){
        console.log("滚动条事件")
    }
```
###去除不匹配部分
```
    $(li>a:not(.return)).click() //not不是这个选择器元素
```
