# pixiJS

## 安装

```
npm i pixi.js
import * as PIXI from 'pixi.js'
```

## 创建舞台

```
const app = new PIXI.Application({
      width:window.innerWidth,
      height:window.innerHeight,
      backgroundColor:0x1099bb,
      resolution:window.devicePixelRatio || 1,
      antialias:true//抗锯齿
    })
```

## 绘制矩形

```
const rect = new PIXI.Graphics()//创建图形对象
rect.beginFill(color,透明度)//填充颜色
rect.drawRect(startX,startY,endX,endY)//绘制矩形
rect.endFill()//结束填充
app.stage.addChild(rect)//添加到舞台
```

## 缩放,位移和旋转

```
rect.scale.set(水平倍数,竖直倍数)
rect.position.set(translateX,translateY)
rect.rotation = value
//锚点
rect.pivot.set(x,y)//控制旋转的中心点
```

## 边框样式

```
rect.lineStyle(width,color,透明度)//线宽，线颜色，透明度
```

## 绘制圆形

```
const circle = new PIXI.Graphics()
circle.beginFill(color,透明度)
circle.drawCircle(x,y,r)//绘制圆
circle.endFill()
circle.position.set(x,y)
app.stage.addChild(circle)
```

## 绘制圆角矩形

```
const roundRect = new PIXI.Graphics()//创建图形对象
roundRect.beginFill(color,透明度)
roundRect.drawRoundedRect(startX,startY,endX,endY,圆角半径)
roundRect.endFill()
roundRect.position.set(x,y)
app.stage.addChild(roundRect)
```

## 绘制椭圆

```
const ellipse = new PIXI.Graphics()//创建图形对象
ellipse.beginFill(color,透明度)
ellipse.drawEllipse(x,y,水平半径，竖直半径)
ellipse.endFill()
ellipse.position.set(x,y)
app.stage.addChild(ellipse)
```

## 绘制多边形

```
const polygon = new PIXI.Graphics()//创建图形对象
polygon.beginFill(color,透明度)
polygon.drawPolygon([x1,y1,x2,y2...])//每两个元素是一个点的坐标
polygon.endFill()
polygon.position.set(x,y)
app.stage.addChild(polygon)
```

## 绘制圆弧

```
const arc = new PIXI.Graphics()//创建图形对象
arc.beginFill(color,透明度)
arc.arc(x,y,r,startDeg,endDeg,顺逆时针)
arc.endFill()
arc.position.set(x,y)
app.stage.addChild(arc)
```

## 绘制线段

```
const line = new PIXI.Graphics()//创建图形对象
line.lineStyle(width,color,透明度)
line.moveTo(x,y)//起始点
line.lineTo(x,y)//结束点
line.position.set(x,y)
app.stage.addChild(line)
```

## 纹理

### 创建纹理

```
//创建一个纹理
const texture = PIXI.Texture.from(url)
//创建一个精灵
const sprite = new PIXI.Sprite(texture)
//设置精灵锚点
sprite.anchor.set(百分比x,百分比y)
//旋转
sprite.rotation = value
//缩放
sprite.scale.set(水平倍数，竖直倍数)
//透明度
sprite.alpha = value
//位置
sprite.x = value
sprite.y = value
app.stage.addChild(sprite)
```

### ticker实现动画

```
app.ticker.add((delta)=>{
//delta 每一帧之间的时间
sprite.rotation += 0.01* delta
```

## 交互

```
//添加点击事件
sprite.interactive = true
sprite.on('click',()=>{
	console.log('111')
})
//添加鼠标进入事件
sprite.on('pointerenter',()=>{
sprite.alpha = 1
})
sprite.on('pointerout',()=>{
sprite.alpha = 0.5
})
```

## 资源管理

```
//添加资源
PIXI.Assets.add(名字,url)
//异步加载资源
const texturesPromise = PIXI.Assets.load([加载资源的名字],(progress)=>{
	//progress加载进度，1表示完成
})
//创建精灵
texturesPromise.then((textures)=>{
	const container = new PIXI.Container()
	const sprite2 = new PIXI.Sprite(textures.名字)
	sprite2.x = value
	sprite2.y = value
	container.addChild(sprite)
	container.addChild((sprite2)
	app.stage.addChild(container)
})
```

### 添加场景资源

```
//添加资源
PIXI.Assets.addBundle(场景名字,{
	名字:url
	...
})
//加载资源
const texturesPromise = PIXI.Assets.loadBundle(场景名字,(progress)=>{
	//progress加载进度，1表示完成
})
texturesPromise.then((textures)=>{
	const container = new PIXI.Container()
	const sprite2 = new PIXI.Sprite(textures.名字)
	sprite2.x = value
	sprite2.y = value
	container.addChild(sprite)
	container.addChild((sprite2)
	app.stage.addChild(container)
})
```

## 文字与遮罩

```
const text = new PIXI.Text(文字内容,{
	fontFamily:value,
	fontSize:value,
	fill:color,
	align:value,
})
text.x = value
text.y = value
text.anchor.set(x,y)
//遮罩
const bunny = PIXI.Sprite.from(url)
//让精灵铺满整个屏幕
bunny.width = value
bunny.height = value
//让文字作为精灵的遮罩
bunny.mark = text
app.stage.addChild(bunny)
```

## 滤镜

```
//创建模糊滤镜
const blurFilter = new PIXI.BlurFilter()
blurFilter.blur = value//设置模糊程度
//添加到精灵上
sprite.filters = [blurFilter]
//创建轮廓滤镜
//需要安装 npm i pixi-filters
import {OutlineFilter,GlowFilter} from 'pixi-filters'
const outlineFilter = new OutlineFilter(width,color)
sprite.filters = [outlineFilter]
//发光滤镜
const glowFilter = new GlowFilter({
	distance:value,
	outerStrength:value,
	innerStrength:value,
	color:color,
	quality:value,
})
```

