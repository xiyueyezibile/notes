[TOC]



# HTML大全

这是我学习html的笔记，如果有看不懂的上网搜索

## 10-DOCTYPE和lang以及字符集的作用

<!DOCTYPE>文本类型声明，作用是告诉浏览器使用哪种HTML版本来显示网页，必须写到最前面
<!DOCTTPE html> 意思是当前页面采用HTML5版本来显示网页
lang 语言种类      用来定义当前文档显示的语言：
en 为英语
zh-CN 为中文
fr 为法语
主要是告诉浏览器是什么网站，定义为英文也可以写中文
```
<head>标签内，可通过<meta>的charset属性来规定HTML文档应该使用哪种字符编码
常用的值有：GB2312（简体中文）,BIG5（繁体中文）,GBK（简体加繁体中文）,UTF-8（万国码）
```

## 语法规范

<html></html>一般成对出现
开始标签，结束标签
<br />
单标签
标签关系：包含关系，并列关系

## emmet语法

生成标签:直接按tab键，输入div，再按tab
生成多个，div*3，再按tab，生成3个div
父子级关系，ul > li，用tab键，生成ul里包含li
兄弟关系，用➕加tab
用.加类名，自动生成div class="类名"
标签.类名，则生成其他，#同理
后面类名用顺序的，后面加$符号，从1开始添加

css：
输入首字母简写➕tab，自动生成

## 浏览器内核

IE Trident
firefox Gecko
Safari Webkit
chrome/Opera Blink

## 特殊字符

```
特殊字符      描述      字符代码
			空格符		&nbsp;
<			小于号		&it;
>			大于号		&gt;
&			和号		&amp;
?			人民币		&yen;
?			版权		&copy;
?			注册商标	&reg;
?			摄氏度		&deg;
?			正负号		&plusmn;
x			乘号		&times;
?			除号		&divide;
?			平方2（上标2）	&sup2;
?			平方3（上标3）	&sup3;
```

## 常用标签

### div和span标签

没有语义，只是一个盒子，用来装内容，可以写文字，可以放图片
1.div独占一行，是个大盒子，其他内容不会和div同一行

```
<div>这是div</div>
```

2.span可以在一行放多个，是个小盒子

```
<span>这是span</span>
```

### html基本结构标签

```
标签名            定义                     说明
<html></html>     HTML标签               页面中最大的标签，称为根标签
<head></head>    文档的头部               注意在head标签中我们必须设置的标签是title
<title></title>  文档的标题               让页面拥有一个属于自己的网页标题
<body></body>    文档的主题               元素包含文档的所有内容，页面内容 基本都是放到body里										  面的
```

### 标题标签

```
<h1> - <h6>(重要程度递减)
<h1>我是一级标题</h1>
1.加了标题的的文字会变粗，字号也会变大
2.一个标题独占一行
```

### 段落标签和换行标签

```
<p>定义段落
只有用段落标签才能分段，无论打几个空格都只显示一个空格。
1.文本会根据浏览器的大小自动换行
2.段落和段落之间保有大的空隙
<br />换行标签
1.单标签
2.只是简单的换了一行，段落之间不会有较大的空隙
```

### 图像标签和路径

```图像标签的属性要写到标签名的后面，属性之间不分先后顺序，属性和属性之间由空格进行分割
<img>定义图形
<img src="图像URL" />
src是<img>的必须属性，用于指定图像文件的路径和文件名
属性：简单理解为属于这个图像标签的特性
src  图片路径    必须属性
alt   文本          替换文本，图像不能显示的文字
title  文本           提示文本，鼠标放到图像上显示的文字
width  像素         设置图像的宽度
height  像素          设置图像的高度
border  像素        设置图像的边框粗细
```

图像标签的属性要写到标签名的后面，属性之间不分先后顺序，属性和属性之间由空格进行分割

### 文本格式化标签

```
文本格式化标签为文字设置粗体，斜体，下划线
加粗   <strong></strong> <b></b>
倾斜   <em></em>   <i></i>
删除线   <dei></dei>   <s></s>
下划线  <ins></ins>      <u></u>
```

前面的语义更强烈 

### 注释标签

如果需要添加一些便于阅读和理解但又不需要显示在页面中的注释文字，需要使用注释标签

```
<!--                  -->    快捷键ctrl+ /
```

## 表格标签

### 基本语法

```
<table>(定义表格）
	<tr>（行）
	<td>单元格中文字</td>（单元格）
	...
	</tr>
	...
</table>
```

### 表格标题标签

```
带有标题的表格：

<table border="1">
  <caption>Monthly savings</caption>
  <tr>
    <th>Month</th>
    <th>Savings</th>
  </tr>
  <tr>
    <td>January</td>
    <td>$100</td>
  </tr>
</table>
<caption> 标签定义表格的标题。

<caption> 标签必须直接放置到 <table> 标签之后。

```

您只能对每个表格定义一个标题。

提示：通常这个标题会被居中于表格之上。然而，CSS 属性 "text-align" 和 "caption-side" 能用来设置标题的对齐方式和显示位置。

### 表格结构标签

```
<thead>表示表格头部区域，里面一定有<tr>标签
<tbody>表示表格主体区域
```

### 表格属性（了解）

一般通过css设置

```
属性名       属性值               描述
align      left,center,right   规定对齐方式
border       1或“”		规定是否有边框，默认“”表示没有边框
cellpadding  像素值          规定单元边沿与内容的空白，默认1像素
cellspacing   像素值         规定单元格之间的空白 默认2像素
width         像素值或百分比    规定宽度
height       像素值或百分比     规定高度
```

### 表头单元格标签

```
<th>姓名</th>  表头标签，会加粗居中显示
```

### 合并单元格

```
可以把多个单元格合并为一个单元格
合并单元格的方式：
跨行合并:rowspan="合并单元格个数" ,  最上侧单元格作为目标单元格写合并代码
跨列合并:colspan="合并单元格个数"，最左侧单元格作为目标单元格写合并代码 
boder-collapse:collapse 合并相邻边框
```

## 表单标签

### 表单域

一个完整的表单由表单域，表单控件和提示信息构成

```
<form>定义表单域
<form>会把它范围内表单元素信息提交给服务器
<form action="url地址" method="提交方式" name="表单域名称">
</form>
属性		属性值	作用
action		url地址	用于指定接收并处理表单数据的服务器程序的url地址
method	get/post	用于设置表单数据的提交方式
name		名称		用于指定表单的名称，以区分同一页面的多个表单域
```



### input表单元素

```
<input type="属性值" />
属性值
button 定义可点击按钮（通常和js搭配使用）
checkbox 定义复选框
file 定义输入字段和“浏览”按钮，供文件上传
hidden 定义隐藏的输入字段
image 定义图像形式的提交按钮
password 定义密码字段，该段字符被掩码
radio 定义单选按钮
reset 定义重置按钮，重置会清除表单所有数据
submit 定义提交按钮，会把表单数据发送到服务器
text 定义单行输入字段，用户可输入文本，默认宽度为20个字符

email 必须输入email类型
url 必须输入URL类型
date 必须输入日期类型
time 必须输入时间类型
month 必须输入月类型
week 必须输入周类型
number 必须输入数字类型
tel 手机号码
search 搜索框
color 生成一个颜色选择表单

属性         属性值        描述
name                    定义input的名称
value                    规定input的值
checked    checked   规定此input元素首次加载时应当被选中
maxlength  正整数     规定输入字段的字符的最大长度

required  required     内容不能为空，必填
placeholder  提示文本  表单的提示信息，存在默认值将不显示
autofocus   autofocus  页面加载完成自动聚焦到指定表单
autocomplete  off/on   当用户在字段上开始键入时，基于之前键入过得值，应该显示出在字段中填写的选							项，默认打开（需要放在表单内，要有name属性）
multiple  multiple      可多选文件提交
```

### label标签

```
<label>标签可以用于绑定一个表单元素，当点击<label>标签内的文本时，浏览器就会自动将焦点转到或选择对应的表单元素上，用来增加用户体验
语法：
<label for="sex">男</label>
<input type="radio" name="sex" id="sex" />
```

### select下拉列表

```
<select>
<option>选项</option>
</select>
在<option>中设定selected="selected"，设定当前选项为默认选项
```

### textarea文本域表单元素

```
<textarea>
输入内容较多可以用。
可以定义多行文本输入。
语法：
<textarea rows="3" cols="20">
</textarea>
```

resize:none;可去除右下角拉伸框

## 超链接标签

```
<a>用于定义超链接
<a href="跳转目标" target="目标窗口的弹出方式">文本或图像</a>
href（必须标签） 用于指定链接目标的url地址（必须以http://开头）；
target 用于指定链接页面的打开方式 _self为默认值,_blank为在新窗口中打开
链接分类：
1.外部链接
2.内部链接（直接写文件名称）
3.空链接：没有确定目标时,<a href="#"></a>
4.下载链接：href里面是安装包或者压缩包
5.网页元素链接：网页中各种元素都可以做超链接
6.锚点链接：我们点击链接，快速定位到页面中的某个位置
* 在链接文本的href属性中，设置属性值为#名字的形式，如<a href="#two">第二集</a>
*找到目标位置标签，里面添加一个id属性=刚才的名字，如：<h3 id="two">第二集介绍</j3>
```

## 多媒体标签

### 音频标签

```
<audio>支持MP3 wav ogg
<audio src="文件地址" controls="controls"></audio>
src 歌曲的路径
preload 是否在页面加载后立即加载（设置 autoplay 后无效）
controls 显示 audio 自带的播放控件
loop 音频循环
autoplay 音频加载后自动播放
currentTime 音频当前播放时间
duration 音频总长度
ended 音频是否结束
muted 音频静音为 true
volume 当前音频音量 [0, 1] 最小值 0 最大值 1
readyState 音频当前的就绪状态
playbackRate: 播放速度

只读属性: 

paused: 音乐是否暂停播放 true--暂停 false--播放

ended: 音乐是否结束播放 true--结束 false--没有结束 设置了loop 音频重复循环播放 不会结束()

方法
load: 重新加载音频

pause: 暂停播放

play: 播放音乐

事件
oncanplay: 音频可以播放事件(缓冲已足够开始时)

oncanplaythrough: 音频可以不缓冲直接从头执行到尾

ondurationchange: 当媒体时长被改变

ontimeupdate: 播放时间更新的事件

onended: 当音频结束播放事件

onpause: 当音频播放暂停事件

onvolumechange: 当音量发生改变时触发
```

### 视频标签

```
<video>仅支持MP4，webm，ogg格式的视频，尽量用MP4。
<video src="文件地址" controls="controls"></video>
属性		值		描述
autoplay 	autoplay	视频就绪自动播放（谷歌需要加入muted解决自动播放问题）
controls	controls 	向用户显示播放控件
width 	pixels(像素)	设置播放器宽度
height			实在播放器高度
loop		loop		是否循环播放
preload	auto(预先加载视频)
		none		如果有autoplay，自动忽略此属性
src		url		视频url地址
poster	lmgurl	加载等待的画面图片
muted	muted	静音播放
```

## 列表标签

列表是用来布局的

### 无序列表

```
<ul>标签表示无序列表，而列表项用<li>标签定义
<ul>
<li></li>
</ul>
无序列表各个列表项之前没有先后之分
<ul>里面只允许放<li>标签
但<li>里面可以放任何元素
```

### 有序列表

```
<ol>定义有序列表
用<li>定义列表
```

### 自定义列表

```
<dl>定义列表
<dt>定义项目（大哥）
<dd>项目分支1（小弟）
```

## 路径

### 绝对路径

目录下的绝对位置，通常从盘符开始的路径

### 相对路径

以引用文件所在位置为参考，建立出的目录路径
分类           符号		说明
同一级路径 			同一级
下一级		/
上一级		../

### 目录文件夹以及根目录

目录文件夹：一个普通文件夹，用来存放网站相关素材
根目录：打开目录文件夹的第一层叫做根目录

## 语义化标签

```
<header>头部标签
<nav>导航标签
<article>内容标签
<section>定义文档某个区域
<aside>侧边栏标签
<footer>尾部标签
```

# Canvas

## canvas必须的属性

id,width,height

## 获取canvas语法提示

加上这段注释在js里面

```
/** @type {HTMLCanvasElement} */
```

## 第一个canvas

```
//1.找到画布
  const root = document.getElementById('root')
  //2.找到画笔
  const ctx = root.getContext('2d')
  //绘制图形
  //矩形illRect(x,y,width,height)
  ctx.fillRect(100,100,100,100)
```

## 获取画笔

```
canvas.getContext('2d')
```

## 一.矩形绘制

### 1.填充模式

```
fillRect(x,y,width,height)
```

### 2.路径模式

```
strokeRect(x,y,width,height)
```

### 3.清除模式

```
clearRect(x,y,width,height)
```

### 4.拆开写法

```
beginPath()//落笔(开始)
rect(x,y,width,height)
fill() || stroke() || clear()
closePath()//抬起笔(结束)
```

## 二.圆弧绘制

```
arc(x,y,半径r,开始角度startDeg，结束角度endDeg,顺逆时针true 0r false)//绘制圆弧
fill()//填充起始点和结束点直接闭合的区域，0度起始点x轴
stroke()//绘制圆弧
```

注意：开始角度和结束角度看的是圆周率，3.14159...表示180度

​			可以用Math.PI(3.1415926...)获取

### arcTo绘制圆弧

```
arcTo(第一个点x,第一个点y,第二个点x,第二个点y,圆弧半径)//起点和两个点构成的两条切线和半径来画圆弧
```



### moveTo移动画笔位置

moveTo(x,y)移动画笔而且不会落在画布上

## 三.线段绘制

```
lineTo(x,y)//从笔当前的位置移动到目标位置
```

## 四.贝塞尔曲线

```
quadraticCurveTo(x,y,x2,y2)
bezierCurveTo(x,y,x2,y2,x3,y3)//三次贝塞尔曲线
```

## 五.path2d

path2d用来封装对象

```
//爱心绘制
  const Path = new Path2D()
  Path.moveTo(300,200)
  Path.bezierCurveTo(350,170,400,200,300,300)
  Path.bezierCurveTo(200,200,250,170,300,200)
  ctx.stroke(Path)
```

## 六.样式和颜色控制

### 颜色

```
fillStyle = color
strokeStyle = color
```

### 全局透明度

```
globalAlpha = [0~1]
```

## 七.线性渐变和径向渐变

```
线性渐变
let line = ctx.createLinearGradient(起点x,起点y,终点x,终点y)
line.addColorStop(0~1,color)
ctx.fillStyle = line
例子:
let line = ctx.createLinearGradient(0,0,600,300)
  line.addColorStop(0,"red")
  line.addColorStop(1,"blue")
  ctx.fillStyle= line
径向渐变
let radia = ctx.createRadialGradient(圆1x，圆1y，圆1r，圆2x，圆2y，圆2r)
radia.addColorStop(0~1,color)
ctx.fillStyle = radia
```

## 八.圆锥渐变

```
let cone = ctx.createConicGradient(角度,x,y)
cone.addColorStop(0~1,color)
ctx.fillStyle = cone
例子：
let cone = ctx.createConicGradient(0,300,200)
  cone.addColorStop(0,'red')
  cone.addColorStop(1,"blue")
  ctx.fillStyle = cone
  ctx.fillRect(0,0,600,400)
```

## 九.pattern模式

```
const img = new Image()
img.src = ...
img.onload = () => {
	//创建图案对象
	let pattern = ctx.createPattern(图片对象img,重复方式"repeat")
	ctx.fillStyle = pattern
}
```

## 十.线段和虚线样式

```
lineWidth = value//线条粗细
lineCap = "butt"默认 || "round"半圆 || square正方形//设置端点样式
lineJoin = "mitter"默认 || "round"磨圆 || "bevel"折平//设置两个线段连接处的样式
设置虚线
setLineDash([实线长度,虚线长度])
lineDashOffset = value //偏移
```

## 十一.阴影

```
ctx.shadowOffsetX = value
ctx.shadowOffsetY = value
ctx.shadowBlur = value
ctx.shadowColor = color
```

## 十二.绘制图片

```
const img = new Image()
img.src = ...
img.onload = () => {
//第一种绘制图片的方式
ctx.drawImage(img,x,y,width,height)
ctx.drawImage(img,裁剪x轴,裁剪y轴,裁剪宽度width,裁剪高度heigt,x,y,width,height)
}
```

## 十三.绘制视频

```
const video = document.createElement('video')
video.src = ...
//requestAnimationFrame()请求动画帧,video每过一帧执行一次
function render() {
ctx.drawImage(video,x,y,width,height)
requestAnimationFrame(render)
}
```

## 十四.绘制文字

```
ctx.font = "100px Microsoft Yahei"
ctx.fillText(内容,x,y,最大像素)
ctx.strokeText(内容,x,y,最大像素)
//文本对齐选项
ctx.textAlign = "center"水平居中 || "end"末尾(right) || "start"默认(left)
ctx.textBaseline = "middle"垂直居中 || "center"水平垂直居中 || "top" || "bottom" || alphabetic(默认)基线对齐
//文本方向
ctx.direction = "rtl"从右到左 //一般不用
//预测量文本宽度
let text = ctx.measureText(内容)//返回一个对象，包含所占宽度的信息
```

## 十五.位移,缩放,旋转

```
位移
ctx.translate(x,y)//移动的是坐标系
缩放
ctx.scale(水平缩放倍数，竖直缩放倍数)//缩放的是坐标系
旋转
ctx.rotate(度数)
```

## 十六.合成图像模式

globalCompositeOperation = value

![image-20230205223634680](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230205223634680.png)

属性很多翻文档

destination-out:之前内容存在于与新图像不重叠的部分，可用来使图片透明

## 十七.裁剪

```
ctx.clip(path2d对象或不写)
```

## 十八.状态的保存和恢复

```
save()//保存画布状态
restore()//恢复画布状态
```

## 十九.像素操作

```
let imageData = ctx.getImageData(startX,startY,endX,endY)//返回一个数组
imageData.data[i]每四个是每一个像素点
imageData.data[0 + 4i] r
imageData.data[1 + 4i] g
imageData.data[2 + 4i] b
imageData.data[3 + 4i] a
ctx.putImageData(imageData,放置x,放置y,clipStartX,clipStartY,clipEndX,clipEndY)
```

