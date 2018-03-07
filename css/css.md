
### css盒子模型
> IE盒子模型/W3C盒子模型
> 盒子模型组成:内容(content)/填充(padding)/边界(margin)/边框(border)
> 区别:IE的内容部分反border和padding计算进去


### css选择器
```
/*id选择器*/
#id{}

/*类选择器*/
.classname{}

/*标签选择器*/
div,b{}

/*相邻选择器*/
h1+p{}

/*子选择器*/
ul<li{}

/*后代选择器*/
li>a{}

/*通配符选择器*/
*{}

/*属性选择器*/
a[rel="external"]{}

/*伪类选择器*/
a:hover{}
```

### 边距
    1. margin: 外边距
    2. padding: 内边距
    两个不相关的盒子之间用margin
    1. margin有时会解析到父级上此时给父级加上overflow:hidden
    2. 给大盒子写padding有时会有一个副作用->撑大父级盒子,如果不想变大例子,要送去相应值,或box-sizing:border-box
### 行元素 块元素
    行元素 inline
        (a,span等）不可设置大小,不独立成行
    块元素 block
        (div,h1-h6,p,ul,li) 可设置大小 独立成行
    行级块元素 inline-block
        (img) 可设置大小 不独立成行
### 块元素水平居中
```
    margin:0 auto; /*上下0,左右自动*/
```
### 圆角
```
    border-radius:1px;
```
### font-size:字号
### font-family:字体
    font-family: "微软雅黑" （中文字体加引号)
    font-family: arial (英文字体不加引号)
### font-weight:加粗
    normal （正常字体)
    bold (加粗）
    bolder (更粗)
    lighter (细)
    100-900值 100->200->300->400->500->...->900正整数数值
### color:字体颜色
    #ffffff
    rgb(0,0,0)
    rgba(0,0,0,0.9)
### font-style:字型
    italic (斜体)
    normal (正常)
    oblique (倾斜文字,用于不支持斜体字体的文字)
### line-height:行高
    通常行高为1.5-2.0倍字体高
    纯数字值表示几倍行高
    其它值为所写行高值
### text-decoration:下划线
    none (无下划线)
    underline (下划线)
    line-through (中划线)
### box-shadow 盒子阴影
	box-shadow:inset 0 0 10px #ccc;
    /* 
    	inset    内阴影,可选项,不写此属性默认外
        0 0      水平偏移/垂直偏移
        10px     模糊半径
        #ccc     颜色
    */
### overflow:auto (超出盒子)
    使DIV里出现滚动条
### text-align:文字水平居中形式
    right
    center
    left
### line-height:50px (文字垂直居中)
    盒子高与line-height相同则居中
### text-indent:首行缩进
```
    10px
```
### 背景图
    特点:默认平铺
    分类:
        1.纯色背景色
        2.非纯色背景图 (比如图片，渐变)
    技巧:
        渐变:切一整条1px宽的图片,利用平铺作渐变图形
### background-size:背景图大小
```
    值可以是auto
    background-size:90px 100px; (高90px,宽100px)
    background-size:cover; (缩放纵横比)
    background-size:contain; (保持纵横比)        
```
### background-origin:背景相对定位位置
    padding-box:相对内边距框
    border-box:相对边框盒
    content-box:相对内容框架
### background-clip:背景相对绘制区域
    padding-box:相对内边距框
    border-box:相对边框盒
    content-box:相对内容框架
### background-image:背景图
    background-image:url(); (url为路径)
### background-repeat:背景图平铺
    no-repeat (不平铺)
    repeat-x (水平重复)
    repeat-y (垂直重复)
### border:边框
    线型:dotted点状,solid实线,double双线,dashed虚线
    1px solid red (一像素宽,实线,颜色)
    border-top
    border-bottom
    border-left
    border-right
### background-position:背景图位置
```
    background-position:0,1px; /*水平 垂直*/
    值:center/left/right/top/bottom/px
    
```
### transform:2d转换
```
    translate(50px,100px) /*位移 水平50px,垂直100px*/
    rotate(4deg) /*顺时针旋转 deg:角度 允许负值*/
    scale(2,1) /*元素缩放尺寸 以中心缩放 同时缩放字体*/
    skew(9deg,1deg) /*翻转角度 根据x y*/
    transform:translate() scale() /*转换多个选项*/
```
### transition:过渡
    transition-property: /*规定过渡的css属性名称*/
              -duration: /*规定过渡时间*/
```
    transition:width 10s; /*过渡属性名称 过渡经过时间*/
```
              -timing-function: /*规定过渡效果的时间曲线 默认ease*/
                linear /*匀速*/
                ease /*慢->快->慢*/
                ease-in /*开始慢*/
                ease-out /*结束慢*/
                ease-in-out /*慢速开始慢速结束*/
              -delay /*规定过渡效何时开始 默认0*/
```
    transition:width 0.1s ease;
```
### animation:动画
    animation-name:规定@keyframes动画名称
             -duration:花费时间
             -timing-function:速度曲线 默认ease
             -delay:动画何时开始
             -iteration-count:动画播放次数 默认1 无限次数infinite
             -direction:逆向播放 默认normal 反向alternate
             -play-state:规定是否正在运行或暂停 默认running 暂停pause
             -fill-made:规定对象动画时间之外的状态
                        none:不改变默认行为
                        forwards:动画完成之后保持最后一个属性值
                        backwards:在animation-delay所指定的一段时间内,在动画显示之前应用开始属性值(第一帧)
                        both:向前和向后填充模式都被应用
### @keyframes:动画的规则
#### 定义
```
    /*method 1:单个动画*/
    @keyframes name{ /*@keyframes规则放前面 name自定义名称*/
        from{
            transfrom:... /*开始*/
        }to{
            transform:... /*结束*/
        }
    }
    /*method 2:多个动画*/
    @keyframes name{
        0%{transform:...}
        15%{transform:...}
        ...
        100%{transform:...}
    }
```
#### 使用
```
    animation:name 8s linear 2s infinite alternate
```
### cursor:光标类型
    pointer:手指
    default:箭头
    auto:浏览器规则
### vertical-align:设置行内元素垂直对齐方式 默认baseline
    baseline:父元素基线
    sub:垂直文本下标
    super:垂直文本上标
    text-top:元素顶端与父元素顶端对齐
    top:元素顶端与行中最高元素顶端对齐
    middle:元素放在父元素中间
    bottom:元素顶端与行中最低元素顶端对齐
    text-bottom:元素底端与父元素字体底端对齐
    %:百分比
    inherit:从父元素继承vertical-align属性
### list-style-type:列表样式
    square /*正方形*/
    circle /*空心圆*/
    disc /*圆*/
    none /*无*/
### list-style-image:图片替代列表符号
    url() /*图片位置不可控制*/
### list-style-position:列表符号位置
    inside /*列表符号在列表里*/
### max-width:最大宽度
### 响应式
#### 字体
    @font-face{
        font-family:name /*自定义名字*/
        src:url() /*路径*/
    }
    div{
        font-family:name /*使用*/
    }
#### 媒体查询设备类型
    断点
```
    @media screen and (min-width:768px) and (max-width:992px)
```
    在某个分辨率范围将ul变成select
```
    @media screen and (...){
        ul{ 
            display:none;
        }
        section{ 
            display:block; 
        }
    }
```
### 手机端meta
```
    <meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1.0,maximum-scale=1,user=scaleable=no"/>
    /*
        其中initial-scale=1缩放比例
    */
```
### 字体格式
    ttf
    eot
    otf
    woff
    svg
    svgz
### 布局形式
#### 固定布局
#### 自适应布局
#### 弹性布局
### 单位
    em:相对浏览器字体单位
### 选择器
```
	:focus /*选择获得焦点的*/
```
### overflow超出部分省略号
```
	text-overflow:ellipsis; //溢出用省略号显示
    white-space:nowrap; //溢出不换行

```
### textarea禁止调节大小-固定大小
    resize:none;
    
### select隐藏三角
    appearance:none;