# Canvas 笔记


## 获取画布上下文
const canvas = document.getElementById('canvas')
const ctx = canvas.getContext('2d')  // webgl webgl1 etc.



## 绘制文本
fillText(text: string, x: number, y: number, maxWidth: number) 在(x, y)位置绘制（填充）文本
strokeText(text: string, x: number, y: number, maxWidth: number) 在(x, y)位置绘制（描边）文本
measureText(text: string) 测量文本，返回 TextMetrics 对象



## 线型
lineWidth 线的宽度。默认 1.0
lineCap 线末端的类型。 允许的值： butt (默认), round, square.
lineJoin 定义两线相交拐点的类型。允许的值：round, bevel, miter(默认)。
miterLimit 斜接面限制比例。默认 10。
getLineDash() 返回当前线段样式的数组，数组包含一组数量为偶数的非负数数字。
setLineDash() 设置当前的线段样式。
lineDashOffset 描述在哪里开始绘制线段。



## 文本样式
font 字体设置。 默认值 10px sans-serif。
textAlign 文本对齐设置。 允许的值： start (默认), end, left, right 或 center.
textBaseline 基线对齐设置。 允许的值： top, hanging, middle, alphabetic (默认),ideographic, bottom.
direction 文本的方向。 允许的值： ltr, rtl, inherit (默认).



## 填充和描边样式
fillStyle 填充的颜色和样式。 默认 #000 (黑色)
strokeStyle 描边的颜色和样式。 默认 #000 (黑色)



## 路径
beginPath() 开始一个新路径 清空子路径列表开始一个新的路径。当你想创建一个新的路径时，调用此方法

closePath() 结束一个路径 使笔点返回到当前子路径的起始点。它尝试从当前点到起始点绘制一条直线。如果图形已经是封闭的或者只有一个点，那么此方法不会做任何操作

moveTo(x: number, y: number) 画笔移动到指定点(x, y)

lineTo(x: number, y: number) 连线至(x, y)点

quadraticCurveTo(x1: number, y1: number, x2: number, y2: number) 二次贝塞尔曲线 当前画笔所在点为起点, (x1, y1)为控制点 (x2, y2)为终点

bezierCurveTo(x1: number, y1: number, x2: number, y2: number, x3: number, y3: number) 三次贝塞尔曲线 当前画笔所在点为起点, (x1, y1)为控制点1 (x2, y2)为控制点2, (x3, y3)为终点

rect(x: number, y: number, width: number, height: number) 绘制矩形路径

ellipse(x: number, y: number, radiusX: number, radiusY: number, rotation: number, startAngle: number, endAngle: number, anticlockwise: number) 绘制椭圆路径
x 椭圆圆心的 x 轴坐标。
y 椭圆圆心的 y 轴坐标。
radiusX 椭圆长轴的半径。
radiusY 椭圆短轴的半径。
rotation 椭圆的旋转角度，以弧度表示(非角度度数)。
startAngle 将要绘制的起始点角度，从 x 轴测量，以弧度表示(非角度度数)。
endAngle 椭圆将要绘制的结束点角度，以弧度表示(非角度度数)。
anticlockwise 可选 Boolean 选项，如果为 true，逆时针方向绘制椭圆 （逆时针）， 反之顺时针方向绘制。

arc(x: number, y: number, r: number, startAngle: number, endAngle: number, anticlockwise: boolean) 绘制圆路径
绘制一段圆弧路径， 圆弧路径的圆心在 (x, y) 位置，半径为 r ，根据anticlockwise （默认为顺时针）指定的方向从 startAngle 开始绘制，到 endAngle 结束。
arcTo(x1: number, y1: number, x2: number, y2: number) 绘制圆路径 当前画笔所在点为起点, (x1, y1)为控制点 (x2, y2)为终点 
根据控制点和半径绘制圆弧路径，使用当前的描点(前一个moveTo或lineTo等函数的止点)。根据当前描点与给定的控制点1连接的直线，和控制点1与控制点2连接的直线，作为使用指定半径的圆的切线，画出两条切线之间的弧线路径。



## 绘制路径
fill() 填充当前路径

stroke() 描边当前路径

剪裁 Cliping
clip() 将当前正在构建的路径转换为当前的裁剪路径

fillRect(x: number, y: number, width: number, height: number) 绘制一个填充的矩形

strokeRect(x: number, y: number, width: number, height: number) 绘制一个描边的矩形

clearRect(x: number, y: number, width: number, height: number) 清空绘制的所有内容



## 绘制图像
drawImage(image: Image|Canvas|Video|SVG, x: number, y: number)
drawImage(image: Image|Canvas|Video|SVG, x: number, y: number, width: number, height: number)
drawImage(image: Image|Canvas|Video|SVG, sx: number, sy: number, sWidth: number, sHeight: number, dx: number, dy: number, dWidth: number, dHeight: number)

image 绘制到上下文的元素。允许任何的 canvas 图像源(CanvasImageSource)，例如：CSSImageValue，HTMLImageElement，SVGImageElement，HTMLVideoElement，HTMLCanvasElement，ImageBitmap 或者OffscreenCanvas。
sx 可选 需要绘制到目标上下文中的，image的矩形（裁剪）选择框的左上角 X 轴坐标。
sy 可选 需要绘制到目标上下文中的，image的矩形（裁剪）选择框的左上角 Y 轴坐标。
sWidth 可选 需要绘制到目标上下文中的，image的矩形（裁剪）选择框的宽度。如果不说明，整个矩形（裁剪）从坐标的sx和sy开始，到image的右下角结束。
sHeight 可选 需要绘制到目标上下文中的，image的矩形（裁剪）选择框的高度。
dx image的左上角在目标canvas上 X 轴坐标。
dy image的左上角在目标canvas上 Y 轴坐标。
dWidth 可选 image在目标canvas上绘制的宽度。 允许对绘制的image进行缩放。 如果不说明， 在绘制时image宽度不会缩放。
dHeight 可选 image在目标canvas上绘制的高度。 允许对绘制的image进行缩放。 如果不说明， 在绘制时image高度不会缩放。



## canvas 状态
save() 使用栈保存当前的绘画样式状态，你可以使用 restore() 恢复任何改变

restore() 恢复到最近的绘制样式状态，此状态是通过 save() 保存到”状态栈“中最新的元素
save 和 restore 方法是用来保存和恢复 canvas 状态的，都没有参数。canvas 的状态就是当前画面应用的所有样式和变形的一个快照。
canvas状态存储在栈中，每当save()方法被调用后，当前的状态就被推送到栈中保存。
一个绘画状态包括：
当前应用的变形（即移动，旋转和缩放，见下）
以及下面这些属性：strokeStyle, fillStyle, globalAlpha, lineWidth, lineCap, lineJoin, miterLimit, lineDashOffset, shadowOffsetX, shadowOffsetY, shadowBlur, shadowColor, globalCompositeOperation, font, textAlign, textBaseline, direction, imageSmoothingEnabled
当前的裁切路径（clipping path）



## 变换Transform
currentTransform 当前的变换矩阵 (SVGMatrix 对象)

translate(x: number, y: number) 原点x轴平移x, y轴平移y

rotate(deg: number) 以原点旋转deg弧度，它是顺时针方向的，以弧度为单位的值

scale(x: number, y: number) 方法可以缩放画布的水平和垂直的单位。两个参数都是实数，可以为负数，x 为水平缩放因子，y 为垂直缩放因子，如果比1小，会缩小图形， 如果比1大会放大图形。默认值为1， 为实际大小
如果参数为负实数， 相当于以x 或 y轴作为对称轴镜像反转
默认情况下，canvas 的 1 个单位为 1 个像素。举例说，如果我们设置缩放因子是 0.5，1 个单位就变成对应 0.5 个像素，这样绘制出来的形状就会是原先的一半。同理，设置为 2.0 时，1 个单位就对应变成了 2 像素，绘制的结果就是图形放大了 2 倍

transform(a: number, b: number, c: number, d: number, e: number, f: number) 矩阵变换
a (m11) 水平方向的缩放
b (m12) 竖直方向的倾斜偏移
c (m21) 水平方向的倾斜偏移
d (m22) 竖直方向的缩放
e (dx) 水平方向的移动
f (dy) 竖直方向的移动

setTransform(a: number, b: number, c: number, d: number, e: number, f: number) 将当前的变形矩阵重置为单位矩阵
resetTransform() 重置当前变形为单位矩阵 等于ctx.setTransform(1, 0, 0, 1, 0, 0)



## 合成
globalAlpha 在合成到 canvas 之前，设置图形和图像透明度的值。默认 1.0 (不透明)。
globalCompositeOperation 通过 globalAlpha 应用，设置如何在已经存在的位图上绘制图形和图像。



## 渐变和图案
createLinearGradient(x0: number, y0: number, x1: number, y1: number) 线性渐变
x0 起点的 x 轴坐标
y0 起点的 y 轴坐标
x1 终点的 x 轴坐标
y1 终点的 y 轴坐标

createRadialGradient(x0: number, y0: number, r0: number, x1: number, y1: number, r1: number)  放射性渐变
x0 开始圆形的 x 轴坐标
y0 开始圆形的 y 轴坐标
r0 开始圆形的半径
x1 结束圆形的 x 轴坐标
y1 结束圆形的 y 轴坐标
r1 结束圆形的半径

addColorStop(offset: number, color: string) Gradient增加颜色断点
offset 0到1之间的值，超出范围将抛出INDEX_SIZE_ERR错误
color CSS颜色值 <color>。如果颜色值不能被解析为有效的CSS颜色值 <color>，将抛出SYNTAX_ERR错误。

createPattern(image: Image|Canvas|Video|SVG, repetition: string)
image
作为重复图像源的 CanvasImageSource 对象。可以是下列之一：
HTMLImageElement (<img>),
HTMLVideoElement (<video>),
HTMLCanvasElement (<canvas>),
CanvasRenderingContext2D,
ImageBitmap,
ImageData,
Blob.
repetition
DOMString，指定如何重复图像。允许的值有：
"repeat" (both directions),
"repeat-x" (horizontal only),
"repeat-y" (vertical only), 
"no-repeat" (neither).
如果为空字符串 ('') 或 null (但不是 undefined)，repetition将被当作"repeat"