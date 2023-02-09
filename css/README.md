[TOC]

# CSS大全

## 引入方式

```
内部样式表：写到html内部
行内样式表：<div style="color: red; " > </div>
外部样式表：<link rel="stylesheet" href="css文件路径">
```

## 元素转换方式

```
display:block 转换为块级元素
display:inline 转换为行内元素
display: inline-block 转换为行内块元素
```

## SEO优化

```
<title>里网站名+网站介绍（小于30字）
<meta>里加name="description" content="内容"
	加name="keywords" content="关键词1,关键词2...."
```

## 制作favicon图片

```
把后缀改为.ico，显示在浏览器标题前面
在<head></head>之间引入<link rel="shortcut icon" href="favicon.ico" type="image/x-icon"/>
```

## css三大特性

### 层叠性

冲突的代码执行就近原则，不冲突的不执行

### 继承性

子级会继承父级的某些样式

### 优先级

选择器相同，执行层叠性
选择性不同，根据选择器权重执行

## 单位

### %

50% 相对单位 相对于父元素

### px

像素 绝对单位，不管父元素怎么变换，它不变

### em

em  相对于父元素字体大小

### rem

rem  相对于根元素html的字体大小

### vw,vh

1vw = 100%
50vw = 50%
相对于视口宽度
vh就是相对于视口高度

## 背景

### 背景图片

background-image：url(图片地址);

### 背景颜色

background-color:transparent(透明,默认)/color;

### 背景固定

background-attachment:scroll（滚动）/fixed 设定背景图像是否固定还是随着页面其余部分滚动
local	背景图片会随着元素内容的滚动而滚动。

### 背景平铺

background-repeat:repeat(默认)/no-repeat/repeat-x(沿着x轴平铺)/repeat-y

### 背景方位

background-position: x y;改变图片位置
可以跟方位名词(top,center,bottom,left,center,right)或精确单位

### 背景色半透明

background: rgba(0,0,0,0.3);
						红，绿，蓝
最后一个是alpha透明度，值在0-1之间，0.5就是半透明

### 复合写法

background:背景颜色 背景图片地址 背景平铺 背景滚动 背景图片位置

## 定位

### 定位组成

定位＝定位模式+边偏移
定位模式：position
属性值：
static 静态定位（了解，默认，无定位）
relative 相对定位：移动位置时根据原来的位置来说的。原来的位置继续保留，不脱标。

**absolute** 绝对定位，移动位置相对于他的祖先元素，
1.如果没有祖先元素或者祖先元素没有定位，以浏览器文档为准对齐。
2.父元素有定位，以最近一级有定位父级元素为参考点移动位置。
3.绝对定位不再占用原来的位置，脱离标准流。

**fixed** 固定定位，固定浏览器的可视位置。
1.以浏览器的可视窗口为参照点来移动位置。
2.跟父元素没有任何关系。
3.不会随滚动条滚动。
4.固定定位不占用原来的位置
固定小技巧：固定到版心右侧
left:50%;
margen-left:版心一半宽度;

**sticky** 粘性定位
1.以浏览器可视窗口为参照点移动元素。
2.占用原来位置。
3.必须添加一个边偏移。
边偏移：top:值; bottom left right

### 定位的特性

1，行内元素加入定位，可以添加宽度和高度
2，块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小。
3.浮动只会压住盒子，但不会压住盒子的文字。绝对定位（固定定位）会压住整个盒子

### 定位的叠放次序

z-index：1；
数值越大越靠上

### 绝对定位的盒子居中算法

加了绝对定位的不能通过margen: 0 auto；进行居中
left:50%
margin-left: -（盒子宽度的一般）
top:50%
margin-top:-(盒子高度的一半)

## 浮动

### 浮动语法

```
语法:
选择器{
	float:属性值;
}
属性值：
none 元素不浮动（默认）
left 元素向左浮动
right 元素向右浮动

float用于创建浮动框，将其移动到一边，直到左边缘或者右边缘触及包含块或者另一个浮动框的边缘
```

### 浮动特性

浮动元素会脱离标准流
浮动的元素会在一行内显示并在元素顶部对齐
浮动元素具有行内块元素特点

### 清除浮动

清除浮动之后，父级会根据浮动的子盒子自动检测高度。父级拥有高度，就不会影响下面的标准流了。

```
语法：
选择器{
	clear:属性值;
}
属性值：
left 不允许左侧有浮动元素
right 不允许右侧有浮动元素
both 同时清除左右两侧浮动的影响

清除浮动的方法：
额外标签法：在浮动元素的末尾（一行最后一个浮动的盒子）加一个新的标签（必须是块级元素 ）
父级添加overfloat，将属性设置为hidden,auto或scroll等,缺点，无法显示溢出的部分
after伪元素法
.类名:after{
	content:"";
	display:block;
	height:0;
	clear:both;
	visibility:hidden;
}
父元素添加双伪元素清除浮动
.类名:before,.类名:after{
	content:"";
	display:table;
}
.类名:after{
	clear:both;
}
```

### 文字围绕浮动元素

浮动元素不会压住文字
于是可以达成浮动元素在左侧，文字会在右边

## 盒子模型

### border

```
border-width 边框粗细，单位px
border-style 边框样式｛
none（默认）
hidden 隐藏
solid 实线边框
dashed 虚线边框
dotted 点线边框
｝
border-color 边框颜色
```

### box-sizing

box-sizing:content-box(默认，盒子大小等于width+padding+border)
		border-box(盒子大小为width)

### padding and margin

padding-left 左内边距
padding-right 右内边距
padding-top 上内边距
padding-bottom 下内边距
margin同理

margin负值可以防止两个边框1+1=2；

### 盒子阴影

box-shadow: h-shadow v-shadow blur spread color inset
h-shadow:必须，水平阴影的位置，允许负值
v-shadow:必须，垂直阴影的位置，允许负值
blur:模糊距离
spread: 阴影的尺寸
color: 阴影的颜色
inset: 将外部阴影改为内部阴影

### 块级盒子水平居中

1.块级盒子必须指定宽度
2.左右外边距设置为auto

### 行内元素水平居中

给父亲添加text-align: center

### 圆角边框

语法：
border-radius:length;

### 文字阴影

text-shadow: h-shadow v-shadow blur color;

## 渐变

### linear-gradient

```
线性渐变
默认to bottom 从上到下渐变
to right
to bottom right对角线方向
to left
to top
语法
background-image:linear-gradient(to right,red,yellow)起点红色过渡到黄色
第一个值也可以用deg，0deg从下到上，deg箭头指向上，表示渐变方向
它也支持透明度transparent
background-image:linear-gradient(to right,rgba(0,0,0,1),rgba(255,0,0,0.1))
不均匀渐变：
background-image:linear-gradient(to right,red 10%,yellow 75%)
repeating-linear-gradient定义重复渐变
background: repeating-linear-gradient(to right,red 0%, green 20%, blue 30%) ；
```

### radial-gradient

```
径向渐变
语法
	background-image: radial-gradient(shape size at position, start-color, ..., last-color);
position：渐变起点的位置，可以为百分比，默认是图形的正中心
shape：渐变的形状，ellipse表示椭圆形，circle表示圆形。默认为ellipse，如果元素形状为正方形的元素，则ellipse和circle显示一样。
size：渐变的大小，即渐变到哪里停止，它有四个值。
closest-side：最近边； farthest-side：最远边；
closest-corner：最近角； farthest-corner：最远角
background-image: radial-gradient(closest-side at 60%(x) 55%(y), red, yellow, black);

repeating-radial-gradient() 函数用于重复径向渐变：（与线性相同）
background-image: repeating-radial-gradient(red, yellow 10%, green 15%);

与线性渐变一样也可以使用百分比实现颜色的不均匀渐变。
```

## 文本属性

### 文本对齐

text-align 设置水平对齐方式
属性值：center,right,left(默认)

### 文本缩进

text-indent 指定文本的第一行缩进，通常是段落首行缩进
长度甚至可以是负值
p{
text-indent: 2px/em;
}
单位：em（一个em是一个文字的大小）

### 文本颜色

语法
color: red;

### 文本阴影

```
text-shadow: offset-x offset-y blur-raduis color;
color：
可选项，设置文本内容的阴影颜色。
offset-x：
必选项，设置文本内容的阴影在水平方向的偏移量。
1、如果值小于 0 的话，则表示向左偏移。
2、如果值等于 0 的话，则表示水平方向不发生任何偏移。
3、如果值大于 0 的话，则表示向右偏移。
offset-y：
必选项，设置文本内容的阴影在垂直方向的偏移量。
1、如果值小于 0 的话，则表示向上偏移。
2、如果值等于 0 的话，则表示垂直方向不发生任何偏移。
3、如果值大于 0 的话，则表示向下偏移。
blur-raduis：
1、可选项，设置文本内容的阴影模糊半径。
2、如果没有指定，则默认为 0。值越大，模糊半径越大，阴影也就越大越淡。
设置多重阴影效果需要设置多个阴影值，这些值之间需要使用逗号（,）分隔。
```

### 文本装饰

text-decoration 给文本添加下划线，上划线等
属性值：
none 默认，没有装饰线
underline 下划线
overline 上划线
line-through 删除线

### 行间距

line-height
设置行和行之间距离

### 文本区域可编辑

属性contenteditable默认false
为true时可以进行编辑

## 选择器

### focus伪类选择器

选取有光标的元素
input:focus{

}

### id选择器

语法：
#名字{
属性: 名;
}
<... id="名字">
一个id选择器只能被调用一次。

### 标签选择器

语法：
标签名 {
属性: 值;
}

### 并集选择器

可以选择多组标签，定义相同样式,任何形式的选择器都可作为并集选择器一部分
div,p{
color: pink;
}

### 后代选择器

需求：选出<ol>中的<li>
ol li {
color: pink ;
}

### 结构伪类选择器

E:first-child
E:last-child
E:nth-child(n) 匹配父元素中的第n个子元素，n可以数字，关键字，公式（n+5从第五个开始，-n+5前5个），even偶数，odd奇数
，看看和E是否匹配，匹配就执行
E:first-of-type
E:last-of-tyoe
E:nth-of-type(n) 指定类型E中

### 类选择器

```
语法：
.类名{
属性: 值;
}

.red {
color: red;
}

<li class="red">
```

### 链接伪类选择器

向某些元素添加特殊效果
最大特点用:表示
链接伪类选择器
为了确保生效，要按下列顺序进行声明
a:link 选择所有未被访问的链接
a:visited 选择所有已被访问的链接
a:hover 选择鼠标指针位于其上的链接
a:active 选择活动链接（鼠标按下未弹起的链接）

### 属性选择器

E[att]   选择具有att属性的E元素
E[att="val"] 选择具有att属性且值为val的E元素

### 通配符选择器

用*定义，选取所有标签
*{
属性: 值;
}

### 伪元素选择器

::before 元素内部的前面插入内容
::after  在元素内部的后面插入内容
其会创建一个元素，属于行内元素
新创建的元素在文档树中是找不到的，所以我们称为伪元素
其必须有content属性
权重为1

### 子代选择器

只能选择某元素最近一级子元素(儿子级)
div>a{

}

## 用户界面样式

### vertical-align

通常用于设置图片或者表单和文字对齐
只对行内元素和行内块元素有效
属性值:
baseline 默认，元素放在父元素基线上
top 把元素的顶端与行中最高元素的顶端对齐
middle 把此元素放置在父元素的中部
bottom 把元素的顶端与行中最低元素的顶端对齐

可以解决图片底部空白缝隙问题，bottom

### 防止拖拽文本域

resize
resize：none；

### 禁止选中文本

user-select

none
元素及其子元素的文本不可被选中

auto
伪元素计算属性为none，元素可编辑则contain，否则继承父元素的user-select，比如父元素all则all，父元素none则none，都不满足则计算值为text

text
这个理解很简单，用户可以选择文本

all
在HTML编辑器中，当双击子元素或者上下文时，包含该子元素的最顶层元素也会被选中

### 轮廓线

outline
给表单添加outline:0;或者outline:none;可以去掉默认的蓝色边

### 鼠标样式

cursor:  ;
属性值：
default    小白，默认
pointer  小手
move    移动
text      文本
not-allowed   禁止

### 溢出文字省略号

单行文本溢出显示省略号：
1.强制一行显示文本
white-space:nowrap(默认nomal，自动换行)
2.超出部分隐藏
overflow:hidden;
3.文字用省略号替代超出部分
text-overflow:ellipsis;

多行文本显示省略号：(了解)
overflow:hidden;
text-overflow:ellipsis;
弹性盒模型
display:-webkit-box;
第2行显示省略号
-webkit-line-clamp:2;
垂直居中
-webkit-box-orient:vertical;

## 元素的显示和隐藏

### display显示隐藏元素

display:none ;隐藏对象，不再占有原来的位置  
display:block;   还有显示元素的意思

### overflow溢出显示隐藏

属性值：
visible 超出显示（默认）
hidden 不显示超出内容。
scroll 盒子内加滚动条显示（上下左右）
auto  需要时才添加滚动条

### visibility显示隐藏元素

visibility: ;
属性值：
visible  元素可视
hidden 元素隐藏，继续占有原来的位置

## calc

calc可以进行一些计算
width:calc(100%-300px);

## filter滤镜

filter:函数(); (blur函数，模糊处理，数值越大越模糊)
filter:blur(5px);

## 过渡

transition:要过渡的属性 花费时间（必须写单位） 运动时间（默认ease） 何时开始（必须写单位,默认0s）
transition width .5s,height .5s;
想要所有属性都变，写all

## flex

### 常见父项属性

f**lex-direction**设置主轴方向(row从左到右（默认） row-reverse 从右到左 column 从上到下 column-reverse 从下到上)

**justify-content** 设置主轴上子元素排列方式（flex-start 从头部开始（默认） flex-end从尾部开始 center 在主轴居中对齐 
**space-around** 平分剩余空间 space-between 先两边贴边再平分剩余空间）

**flex-wrap** 设置子元素是否换行（nowrap不换行（默认） wrap换行）

**align-content** 设置侧轴上子元素的排列方式（多行）（flex-start 从侧轴头部开始（默认） flex-end从侧轴尾部开始 center 在侧轴居中对齐 
**space-around** 平分侧轴剩余空间 space-between 先两边贴边再平分侧轴剩余空间 stretch设置子项元素高度平分父项元素）

**align-items** 设置侧轴上的子元素排列方式（单行）（flex-start 从上到下（默认） flex-end从下到上 center居中 stretch拉伸 ）

**flex-flow** 复合属性，相当于flex-direction和flex-wrap

### 常见子项属性

flex定义子项目剩余空间，用flex表示占多少份数
flex: (数字,默认0) ;

align-self 控制子项在侧轴的排列方式
nth-child()

order定义排列顺序，顺序数字小的排在前面

## grid

### 开启grid布局

属性：
display:grid(块级网格布局)/inline-grid(行内网格布局);  

### 边框线

template-row-start:行开始
template-row-end:行结束
简写grid-row:行开始/行结束
template-columns-start
template-columns-end

### 单元格内容对齐方式

justify-items:水平方向对齐方式
align-items:垂直方向对齐方式
简写
place-items:水平，垂直;
属性值：
start 对齐单元格起始边缘
end对齐单元格结束边缘
center内部居中
stretch拉伸，占单元格整个宽度

### 定义间距

grid-row-gap:定义行间距;
grid-columns-gap:定义列间距;

### 定义行和列

grid-template-columns:指定列高
grid-template-rows:指定行高
写几个行高就有几行，写几个列高就有几列
属性值：
具体值
百分比
fr
auto占满剩下的
repeat函数 repeat(重复次数，属性值);

### 整个内容区域在容器中的对齐方式

justify-content:水平对齐方式
align-content:垂直对齐方式
简写
place-content:水平 垂直;
属性值:
start
end
center
space-around左右两边距离相等
space-between两端对齐
space-evenly均匀对齐

### 指定区域

grid-temolate-areas:"a b c"
			"d e f"
			"g h i"
如果某些区域不需要利用，则用"."代替 "a . c"
grid-area:区域

## 2d转换

### rotate

旋转
transform:rotate(度数)
单位deg（度），正为顺时针，默认旋转中心点是元素中心点
transform-origin:x y;设置旋转中心点，x y可以设置像素或者方位名词

### scale

缩放
transform:scale(x,y);
		      1,1放大一倍，相当于没有放大
优势：不会影响其他盒子，而且可以设置中心点

### translate

移动
transform:translate(x,y);
不会影响其他元素位置
translate里面的百分比是以盒子自身宽度或高度来对比的
对行内标签没有效果

## 3d转换

### perspective

透视，单位是像素
透视写在被观察元素的父盒子上面
透视越小，图像越大

爷爷设置perspective、父亲设置transform-style: preserve-3d、孩子们设置绝对定位和3D偏移。

### rotate3d

rotateX:沿着x轴旋转
rotateY:沿着y轴旋转
rotateZ:沿着z轴旋转
rotate3d:(x,y,z,deg)

### transfrom-style

控制子元素是否开启三维立体空间
transform-style:flat(默认，不开启)/perserve-3d
代码写给父级

### translate3d

transform:translate3d(x,y,z);
走
translateZ一般用px

## font

### font-family

font-family定义字体系列
p { 
font-family:'微软雅黑';
}
如果有多个字体，用,分割

### font-size

p{
font-size: 20px;
}
标题标签比较特殊，需要单独指定文字大小

### font-style

属性值:
normal 正常显示
italic    斜体显示

### font-weight

设置文字粗细
属性值：normal(400),bold(粗体,700),bolder,number(通过数字进行加粗，数字后面不跟单位)

### 复合属性

body{
font: font-style font-weight font-size/line-height font-family;
}
font: italic 700 16px 'Microsoft yahei';
不能随意调换顺序
不要的属性可以省略，但font-size font-family不能省略

## 动画

### keyframes

```
定义动画
@keyframes 动画名称 {
	0%{

}
	100%{

}

}

0%是动画开始
100%动画结束

div{
animation-name:动画名称;
animation-duration:持续时间;
}
```

### 简写

animation:动画名称 持续时间 运动曲线 何时开始 播放次数 是否反方向 动画状态;

### 属性

animation-name:规定动画名称
animation-duration:规定持续时间
animation-timing-function:规定动画速度曲线 linear均速 ease慢快慢 ease-in慢快 ease-out快慢 ease-in-out 慢慢
 steps()指定时间函数中的间隔数量（步长）
animation-delay:规定动画何时开始
animation-iteration-count:规定动画播放次数，默认1，还有infinite
animation-direction:规定动画是否在下一周期逆向播放，alternate逆播放
animation-play-state:规定动画是否正在运行或暂停，默认normal，还有pause
animation-fill-mode:规定动画结束后状态，保持forwards回到起始backwards

## less

### less变量

```
@变量名:值;

选择器变量：
必须放在大括号中
@mySelector:#wrap;
@wrap:wrap;
@{mySelector} {
  color:red;
}
.@{wrap} {
  color: green;
}
```

### less嵌套

```
.header {
  width: 200px;
  height: 200px;
  background-color: pink;
  a {
    color: red;
  }
}

对应css：
.header {
  width: 200px;
  height: 200px;
  background-color: pink;
}
.header a {
  color: red;
}
如果遇见伪类伪元素选择器
如果有&符号就解析为伪类
.header {
  width: 200px;
  height: 200px;
  background-color: pink;
  a {
    color: red;
    &:hover {
      color: blue;
    }
  }
}
```

### less运算

除法/要用括号包起来
运算符两侧必须敲一个空格
两个数参与运算如果一个数有单位就以这个单位为准
两个都有单位且不一样以第一个为准

### less注释

//编译之后不会出现在css文件上
/*编译之后会出现在css文件上 */

## 移动端

### 移动端初始化文件

```
npm install normalize.css
```

### 清除移动端特殊样式

清除点击高亮
-webkit-tap-highlight-color:transparent;
ios中能给按钮和输入框自定义样式
-webkit-appearance:none;
禁用长按页面时弹出菜单
img,a {
-webkit-touch-callout:none;
}

### 视口

```
meta视口标签
让布局视口宽度和理想视口宽度一致（设备有多宽布局视口就有多宽）
<meta name="vierport" content="width=device=width, user-scalable=no,initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
属性      说明
width    宽度设置的是viewport宽度，可设置特殊值device-width
initial-scale  初始缩放比
maximum-scale minimum-scale 最大缩放比，最小缩放比
user-scalable    用户是否可以缩放，yes或no
```



### rem适配布局

rem相对于html元素的字体大小

### 媒体查询

使用@media查询可以针对不同媒体类型定义不同样式
语法:
@media mediatype and|not|only (media feature) {
	CSS-Code;
}

mediatype 媒体类型
	all 用于所有设备
	print 用于打印机和打印预览
	screen 用于电脑屏幕 平板电脑 手机等
关键字 and多个媒体特性连接到一起 not排除某个媒体类型，可以省略 only指定某个媒体类型，可以省略
media feature 媒体特性 必须有小括号
	width 定义输出设备页面可见区域的宽度
	min-width 定义输出设备中最小可见区域
	max-width 定义输出设备中页面最大可见区域

### 背景缩放

background-size:背景图片宽度 背景图片高度;
单位：长度，百分比，cover，contain
cover把背景图片扩展到足够大，以使背景图像完全覆盖背景区域
contain把图像扩展至最大尺寸，使其宽度和高度完全适应内容区域