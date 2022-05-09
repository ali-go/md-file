# canvas 笔记

发表于 2021-02-12|更新于 2021-08-24|[前端](https://liuxianl.com/categories/前端/)

 字数总计:2.6k|阅读时长:10 分钟 | 阅读量:920

# canvas 笔记

[canvas 教程](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API)

## 一。概述

长久以来，web 上的动画都是 Flash。比如动画广告、游戏等等，基本上都是 F1ash 实现的。Flash 是有缺点的，比如需要安装 Adobe Flash Player, 漏洞多，重量比较大。卡顿和不流畅等等

### 1.1 简介

HTML5 提出了一个新的 canvas 标签，彻底颠覆了 Flash 的主导地位。无论是广告、游戏都可以使用 canvas 实现了，Canvas 是一个轻量级的画布，我们使用 Canvas 进行 JavaScript 的编程，不需要增加额外的插件，性能也很好，不卡顿，在手机中也很流畅

## 二。基本使用

```
HTML
<canvas width="400" height="500" id="mycanvas">
       当前浏览器版本不支持，请升级浏览器
</canvas>
```

> canvas 的标签属性只有两个，width 和 height.。表示的是 canvas 画布的宽度和高度。注意 canvas 的 width 和 height 不要用 css 的样式来设置，如果使用 css 的样式来设置，画布会失真，会变形 标签对儿里面的文字是用来提示低版本浏览器 (IE6/7/8)

| 方法 / 属性                | 描述                                                    |
| -------------------------- | ------------------------------------------------------- |
| getContext()               | 得到画布上下文，上下文有两个，2d 的上下文和 3d 的上下文 |
| fillStyle                  | 设置颜色                                                |
| fillRect(x,y,width,height) | 方法绘制 “已填色” 的矩形。默认的填充颜色是黑色。        |

## 三.canvas 的编程思想

### 3.1 像素化

> 我们使用 canvas 绘制了一个图形，一旦绘制成功了，canvas 就像素化了他们。 canvas 没有能力，从画布上再次得到这个图形，也就是说我们没有能力去修改已经在画布上的内容。这个就是 canvas 比较轻量的原因，Flash 重的原因之一就有它可以通过对应的 api 得到已经上 “画布” 的内容然后再次绘制，如果我们想要让这个 canvas 图形移动，必须按照清屏 - 更新 - 渲染的逻辑进行编程，总之就是重新再画一次

### 3.2 动画思想

清屏 - 更新 - 渲染，这个思想就可以为 canvas 的动画思想

```
JAVASCRIPT
var canvas=document.getElementById("mycanvas");
var ctx=canvas.getContext("2d")
ctx.fillStyle="blue"
// 设置信号量
var left=10;
setInterval(()=>{
    //清除画布
    ctx.clearRect(0,0,700,600)
    // 更新信号量
    left++;
    ctx.fillRect(left,left,100,100)
    if(left==700){
        left=10
    }
},4)
```

> 实际上，动画的生存就是相关静态画面连续插放了，这个就是动画的过程。我们把每一次绘制的静态画面叫做 " **一帧** "，时间的间隔 (定时器的间隔) 就表示的是帧的间隔

### 3.3 面向对象实现 canvas 动画

因为 canvas 不能得到已经上屏的对象，所以我们要维持对象的状态。在 canvas 动画中，我们都使用面向对象来进行编程，因为我们可以使用面向对象的方式来维持 canvas 需要的属性和状态

```
JAVASCRIPT
// 获取画布
var can = document.getElementById("can")
var ctx = can.getContext("2d");
// 绘制方法
function Rect(x, y, w, h, color) {
    this.x = x;
    this.y = y;
    this.w = w;
    this.h = h;
    this.color = color
}
// 更新方法
Rect.prototype.update = function () {
    this.x++;
}
// 渲染
Rect.prototype.render = function () {
    // 设置颜色
    ctx.fillStyle = this.color;
    // 渲染
    ctx.fillRect(this.x, this.y, this.w, this.h);
}
// 实例化
var r1 = new Rect(100, 100, 50, 50, "#91d5ff")
// 动画过程
setInterval(() => {
    //清屏
    ctx.clearRect(0, 0, can.width, can.height)
    //更新
    r1.update()
    // 渲染
    r1.render()
}, 5)
```

>  动画过程在主定时器里面，每一帧都会调动实例的更新和渲染方法

## 四. canvas 绘制功能

| 方法 / 属性                  | 描述                                             |
| ---------------------------- | ------------------------------------------------ |
| fillStyle                    | 设置填充颜色                                     |
| fillRect(x,y,width,height)   | 方法绘制 “已填色” 的矩形。默认的填充颜色是黑色。 |
| strokeStyle                  | 设置边框颜色                                     |
| strokeRect(x,y,width,height) | 方法绘制矩形边框。默认的填充颜色是黑色。         |
| clearRect(x,y,width,height)  | 清除画布内容                                     |
| globalAlpha                  | 设置透明度 0-1                                   |

### 4.1 绘制路径

```
JAVASCRIPT
// 创建路径
ctx.beginPath()
// 移动绘制点
ctx.moveTo(100,100)
// 描述行进路径
ctx.lineTo(200,300);
ctx.lineTo(300,230);
ctx.lineTo(440,290);
ctx.lineTo(380,50);
// 封闭路径
ctx.closePath()
// 设置颜色
ctx.strokeStyle="#91d5ff"
// 绘制不规则图形
ctx.stroke()
// 填充不规则图形
ctx.fill()
```

[![绘制路径图](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/%E7%BB%98%E5%88%B6%E8%B7%AF%E5%BE%84%E5%9B%BE.png)](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/绘制路径图.png)

### 4.2 绘制圆弧

```
JAVASCRIPT
arc(x, y, radius, startAngle, endAngle, anticlockwise)
```

- `x,y` 为绘制圆弧所在圆上的圆心坐标。
- `radius` 为半径。
- `startAngle` 以及 `endAngle` 参数用弧度定义了开始以及结束的弧度。这些都是以 x 轴为基准。
- 参数 `anticlockwise` 为一个布尔值。为 true 时，是逆时针方向，否则顺时针方向。

> **注意：`arc()` 函数中表示角的单位是弧度，不是角度。角度与弧度的 js 表达式:**
>
> **弧度 =(Math.PI/180)\* 角度。**

```
JAVASCRIPT
// 创建路径
ctx.beginPath();
// 圆周长 2π 2*3.14≈7 2*Math.PI
ctx.arc(200,200,100,0,2*Math.PI,false)
//  ctx.arc(200,200,100,0,0.3,false)
// 绘制
ctx.stroke()
```

[canvas 实现鼠标跟随炫彩小球](https://liuxianl.com/demo/code/demo05.html)

[canvas 实现炫彩小球弹弹](https://liuxianl.com/demo/code/demo06.html)

### 4.3 线型

我们可以利用 `lineWidth` 设置线的粗细，属性值必须是数字，默认是 1.0。没有单位

```
JAVASCRIPT
ctx.beginPath();
ctx.moveTo(100,150)
ctx.lineTo(200,200)
ctx.lineTo(300,50)
ctx.lineWidth=10
ctx.stroke()
```

[线型教程](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)

### 4.4 文本

```
JAVASCRIPT
// 设置文字
ctx.font="30px 宋体"
// 设置文字对齐方式
ctx.textAlign="start"
ctx.fillText("Hello Canvas",100,100)
```

### 4.5 渐变

- 线型渐变

```
JAVASCRIPT
// 渐变
var linear=ctx.createLinearGradient(0, 0, 200, 200);
linear.addColorStop(0,"red");
linear.addColorStop(0.5,"#91d5ff");
linear.addColorStop(0.8,"#ffec3d");
linear.addColorStop(1,"blue")
ctx.fillStyle=linear
ctx.fillRect(10,10,200,100)
```

### 4.6 阴影

```
JAVASCRIPT
// 阴影
ctx.shadowOffsetX=10 // 左右偏移
ctx.shadowOffsetY=10 // 上下偏移
ctx.shadowBlur=3; // 模糊度
ctx.shadowColor="red"; // 颜色
// 设置文字
ctx.font="30px 宋体"
ctx.fillText("Hello Canvas",100,100)
```

## 五。图片使用

```
JAVASCRIPT
 // 创建image元素
var img=new Image();
// 设置src地址
img.src="https://tva3.sinaimg.cn/large/006djwNZgy1gmqxcekdm8j31hc0u0dln.jpg"
// 必须在onload 之后绘制图片
img.onload=function(){
    ctx.drawImage(img,100,100,200,100)
}
```

- 4 个参数

```
JAVASCRIPT
drawImage(img,x,y,width,height)
```

[![kfdjhgfkd9856745](https://liuxianl.com/img/loading.gif)](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/kfdjhgfkd9856745.png)

- 8 个参数 [切片 Slicing](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Using_images#slicing)

```
JAVASCRIPT
drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight)
```

1. 前 4 个参数指的是你在图片中设置切片的宽度和高度，以及切片位置
2. 后 4 个参数指的是切片在画布上的位置和切片的宽度和高度

[![image-20210213111523157](https://liuxianl.com/img/loading.gif)](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210213111523157.png)

## 六。资源管理器

```
JAVASCRIPT
 // 游戏类
function Game() {
    this.dom = document.querySelector("canvas");
    this.ctx = this.dom.getContext("2d");

    // 添加属性，保存需要的图片地址
    this.R = {
        "01": "https://tvax3.sinaimg.cn/large/006djwNZgy1gkyvxt1exaj33y8280b2c.jpg",
        "02": "https://tva1.sinaimg.cn/large/006djwNZgy1gkyzq80yobj31hc0u0n4r.jpg",
        "03": "https://tva3.sinaimg.cn/large/006djwNZgy1gmqxcekdm8j31hc0u0dln.jpg",
        "04": "https://tva4.sinaimg.cn/large/006djwNZgy1gmqxee8qo6j31hc0u0qcr.jpg"
    }
    // 获取资源图片的总数
    var allAmount = Object.keys(this.R).length
    // 计数器
    var count = 0
    // 遍历对象获取每一个地址
    for (k in this.R) {
        var src = this.R[k]
        // 创建图片
        this.R[k] = new Image()
        // 设置图片地址
        this.R[k].src = src;
        // 判断图片是否加载完成
        var self = this
        this.R[k].onload = function () {
            // 计数
            count++;
            // 清屏
            self.ctx.clearRect(0, 0, 600, 500)
            self.ctx.font = "16px Arial"
            // 设置资源加载文案
            self.ctx.fillText("图片已加载：" + count + "/" + allAmount, 10, 50)
        }
    }

}
console.log(new Game());
```

## 七。变形

### 7.1 概述

[`save()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/save)

保存画布 (canvas) 的所有状态

[`restore()`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/restore)

save 和 restore 方法是用来保存和恢复 canvas 状态的，都没有参数。Canvas 的状态就是当前画面应用的所有样式和变形的一个快照。

Canvas 状态存储在栈中，每当 `save()` 方法被调用后，当前的状态就被推送到栈中保存。一个绘画状态包括：

- 当前应用的变形（即移动，旋转和缩放，见下）
- 以及下面这些属性：[`strokeStyle`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/strokeStyle), [`fillStyle`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/fillStyle), [`globalAlpha`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/globalAlpha), [`lineWidth`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineWidth), [`lineCap`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineCap), [`lineJoin`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineJoin), [`miterLimit`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/miterLimit), [`lineDashOffset`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineDashOffset), [`shadowOffsetX`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/shadowOffsetX), [`shadowOffsetY`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/shadowOffsetY), [`shadowBlur`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/shadowBlur), [`shadowColor`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/shadowColor), [`globalCompositeOperation`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/globalCompositeOperation), [`font`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/font), [`textAlign`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/textAlign), [`textBaseline`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/textBaseline), [`direction`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/direction), [`imageSmoothingEnabled`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/imageSmoothingEnabled)

你可以调用任意多次 `save` 方法。每一次调用 `restore` 方法，上一个保存的状态就从栈中弹出，所有设定都恢复。

### 7.2 translate

- translate 和 CSS3 的 translate 属性一样也是发挥着空间平移作用

```
JAVASCRIPT
// 保存
ctx.save();
ctx.translate(50,50)
ctx.fillRect(0,0,120,120)
// 恢复
ctx.restore()
// 渲染位置是没有存档之前的位置
ctx.fillRect(0,200,120,120)
```

[![image-20210213124807029](https://liuxianl.com/img/loading.gif)](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210213124807029.png)

- 变形实际上都是将整个画布进行的变形，所以如果一旦变形操作多了，画布将变得不可控
- 如果使用到变形，一定记住下面的规律：变形之前要先备份，将世界和平的状态进行备份，然后再变形，变形完毕后一定要恢复到世界和平的样子，不要影响下一次的操作

### 7.3 rotate

```
JAVASCRIPT
// 保存
ctx.save();
ctx.translate(200,100)
ctx.rotate(1)
ctx.fillRect(0,0,120,120)
// 恢复
ctx.restore()
// 渲染位置是没有存档之前的位置
ctx.fillRect(0,200,120,120)
rotate(angle)
```

这个方法只接受一个参数：旋转的角度 (angle)，它是顺时针方向的，以弧度为单位的值。

旋转的中心点始终是 canvas 的原点，如果要改变它，我们需要用到 `translate` 方法。

### 7.4 scale

```
JAVASCRIPT
ctx.save();
ctx.translate(200,100)
ctx.scale(0.6,0.6)
ctx.fillRect(0,0,120,120)
// 恢复
ctx.restore()
// 渲染位置是没有存档之前的位置
ctx.fillRect(0,200,120,120)
```

`scale` 方法可以缩放画布的水平和垂直的单位。两个参数都是实数，可以为负数，x 为水平缩放因子，y 为垂直缩放因子，如果比 1 小，会缩小图形， 如果比 1 大会放大图形。默认值为 1， 为实际大小。

### 7.5 [Transforms](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Transformations#transforms)

最后一个方法允许对变形矩阵直接修改。

```
JAVASCRIPT
transform(a, b, c, d, e, f)
// 如果任意一个参数是`Infinity`，变形矩阵也必须被标记为无限大，否则会抛出异常。
```

这个函数的参数各自代表如下：

- `a(m11)` 水平方向的缩放
- `b(m12)` 竖直方向的倾斜偏移
- `c(m21)` 水平方向的倾斜偏移
- `d(m22)` 竖直方向的缩放
- `e(dx)` 水平方向的移动
- `f(dy)` 竖直方向的移动

## 八。合成

- 合成其实就是我们常见的蒙板状态，本质就是如何进行压盖，如何进行显示

```
JAVASCRIPT
ctx.fillStyle="#91d5ff"
ctx.fillRect(100,100,100,100)
ctx.fillStyle="#ffc069"
ctx.beginPath()
ctx.arc(200,200,60,0,7,false)
ctx.fill()
```

[![image-20210213190925696](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210213190925696.png)](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210213190925696.png)

- [`globalCompositeOperation`](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial/Compositing#globalcompositeoperation) 这个属性设定了在画新图形时采用的遮盖策略，其值是一个标识 12 种遮盖方式的字符串。
- [`globalCompositeOperation = type`](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/globalCompositeOperation)

```
JAVASCRIPT
ctx.globalCompositeOperation="destination-over"
```

[![image-20210213191252885](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210213191252885.png)](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/img/image-20210213191252885.png)

- [刮刮乐](https://liuxianl.com/demo/code/demo07.html)

**文章作者:** [橘子味雪糕](mailto:undefined)

**文章链接:** [https://liuxianl.com/2021/02/12/%E5%89%8D%E7%AB%AF/canvas/](https://liuxianl.com/2021/02/12/前端/canvas/)

**版权声明:** 本博客所有文章除特别声明外，均采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可协议。转载请注明来自 [橘子味雪糕](https://liuxianl.com/)！

[前端](https://liuxianl.com/tags/前端/)[动画](https://liuxianl.com/tags/动画/)

[![cover of previous post](https://tva1.sinaimg.cn/large/006djwNZgy1gkyzq80yobj31hc0u0n4r.jpg)上一篇Vue 3 学习笔记](https://liuxianl.com/2021/05/05/vue/vue3笔记/)

[![cover of next post](https://tvax4.sinaimg.cn/large/006djwNZgy1gp42cly4rdj30xc0irwme.jpg)下一篇SassScript](https://liuxianl.com/2021/02/11/前端/SassScript/)

 相关推荐

[![cover]() 2021-02-10CSS 动画](https://liuxianl.com/2021/02/10/前端/CSS动画/)

[![cover]() 2020-12-21ES6：promise、async 的理解](https://liuxianl.com/2020/12/21/前端/ES6：promise、async的理解/)

[![cover](https://tvax3.sinaimg.cn/large/006djwNZgy1gp42cm8a5aj30xc0irgvw.jpg) 2021-08-0549 个常用 JavaScript 方法封装](https://liuxianl.com/2021/08/05/前端/49个常用JavaScript方法封装/)

[![cover]() 2021-07-09正则](https://liuxianl.com/2021/07/09/前端/正则/)

[![cover]() 2021-02-11SassScript](https://liuxianl.com/2021/02/11/前端/SassScript/)

------

 评论





提交

2 评论

![img](https://gravatar.loli.net/avatar/d41d8cd98f00b204e9800998ecf8427e?d=monsterid&v=1.4.14)

Anonymous Chrome 91.0.4472.124 Windows 10.0

2021-07-04回复

哇，这做的也太漂亮了吧 ![thumb](https://img.t.sinajs.cn/t4/appstyle/expression/ext/normal/e6/2018new_zan_org.png)

![img](https://gravatar.loli.net/avatar/a3f0b00bd5b55d3646c3421a51184ee2?d=monsterid&v=1.4.14)

前端小菜鸡 Chrome 88.0.4324.190 Windows 10.0

2021-03-07回复

膜拜大佬 想要微信联系方式

![img](https://gravatar.loli.net/avatar/b85253bb4c66d1bc645081556dc9486f?d=monsterid&v=1.4.14)

[橘子味雪糕](https://liuxianl.com/) Edge 89.0.774.54 Windows 10.0

2021-03-17回复

[@前端小菜鸡](https://liuxianl.com/2021/02/12/前端/canvas/#6044c092f8ac3a24def277bb) , 不好意思啊 才看到 在关于页面有二维码

Powered By [Valine](https://valine.js.org/)
v1.4.14

![avatar](https://liu-markdown-img.oss-cn-hangzhou.aliyuncs.com/other-img/1610769993419-avatar.png)

橘子味雪糕

竟然选择了远方，便只顾风雨兼程

[文章17](https://liuxianl.com/archives/)

[标签14](https://liuxianl.com/tags/)

[分类8](https://liuxianl.com/categories/)

[Follow Me](https://github.com/liumuge)

公告

更换域名 https://liuxianl.com/

2021-08-30 MON☀️ 29 *C💧 84%

22:13:18

36.18.174.210HangzhouPM

那年今日

*A.D.2010*印度尼西亚[锡纳朋火山](http://baike.baidu.com/view/4202179.htm)沉睡 400 年后再次爆发

*A.D.1619*日本大名[岛津义弘](http://baike.baidu.com/view/388209.htm)逝世

*A.D.1785*民族英雄[林则徐](http://baike.baidu.com/subview/7659/4947309.htm)出生

*A.D.1797*英国作家[玛丽・雪莱](http://baike.baidu.com/view/249385.htm)出生

*A.D.1871*英国物理学家[卢瑟福](http://baike.baidu.com/view/601906.htm)出生

*A.D.1929*中国现代农民运动领袖[彭湃](http://baike.baidu.com/subview/88171/5086731.htm)逝世

*A.D.1930*“股神” [沃伦・巴菲特](http://baike.baidu.com/view/24880.htm)出生

*A.D.1935*法国作家[巴比塞](http://baike.baidu.com/view/260201.htm)逝世

*A.D.1940*电子的发现者[汤姆生](http://baike.baidu.com/view/608016.htm)在英格兰剑桥逝世

*A.D.1956*[毛泽东](http://baike.baidu.com/subview/1689/11849262.htm)发表 “球籍论”

*A.D.1958*中国第一座[原子反应堆](http://baike.baidu.com/view/22217.htm)[回旋加速器](http://baike.baidu.com/view/145454.htm)开始运转

*A.D.1972*世界足球先生[帕维尔・内德维德](http://baike.baidu.com/view/250647.htm)出生

*A.D.1982*苏联发射[核动力](http://baike.baidu.com/view/116141.htm)[海洋监视卫星](http://baike.baidu.com/view/381168.htm)

*A.D.1990*中国史学家[钱穆](http://baike.baidu.com/view/2036.htm)逝世

*A.D.1998*中国兴建首条跨海[铁路](http://baike.baidu.com/view/19293.htm)

*A.D.2010*印度尼西亚[锡纳朋火山](http://baike.baidu.com/view/4202179.htm)沉睡 400 年后再次爆发

*A.D.1619*日本大名[岛津义弘](http://baike.baidu.com/view/388209.htm)逝世

目录

1. \1. canvas 笔记
   1. 1.1. 一。概述
      1. [1.1.1. 1.1 简介](https://liuxianl.com/2021/02/12/前端/canvas/#11-简介)
   2. [1.2. 二。基本使用](https://liuxianl.com/2021/02/12/前端/canvas/#二-基本使用)
   3. 1.3. 三.canvas 的编程思想
      1. [1.3.1. 3.1 像素化](https://liuxianl.com/2021/02/12/前端/canvas/#31-像素化)
      2. [1.3.2. 3.2 动画思想](https://liuxianl.com/2021/02/12/前端/canvas/#32-动画思想)
      3. [1.3.3. 3.3 面向对象实现 canvas 动画](https://liuxianl.com/2021/02/12/前端/canvas/#33-面向对象实现-canvas-动画)
   4. 1.4. 四. canvas 绘制功能
      1. [1.4.1. 4.1 绘制路径](https://liuxianl.com/2021/02/12/前端/canvas/#41-绘制路径)
      2. [1.4.2. 4.2 绘制圆弧](https://liuxianl.com/2021/02/12/前端/canvas/#42-绘制圆弧)
      3. [1.4.3. 4.3 线型](https://liuxianl.com/2021/02/12/前端/canvas/#43-线型)
      4. [1.4.4. 4.4 文本](https://liuxianl.com/2021/02/12/前端/canvas/#44-文本)
      5. [1.4.5. 4.5 渐变](https://liuxianl.com/2021/02/12/前端/canvas/#45-渐变)
      6. [1.4.6. 4.6 阴影](https://liuxianl.com/2021/02/12/前端/canvas/#46-阴影)
   5. [1.5. 五。图片使用](https://liuxianl.com/2021/02/12/前端/canvas/#五-图片使用)
   6. [1.6. 六。资源管理器](https://liuxianl.com/2021/02/12/前端/canvas/#六资源管理器)
   7. 1.7. 七。变形
      1. [1.7.1. 7.1 概述](https://liuxianl.com/2021/02/12/前端/canvas/#71-概述)
      2. [1.7.2. 7.2 translate](https://liuxianl.com/2021/02/12/前端/canvas/#72-translate)
      3. [1.7.3. 7.3 rotate](https://liuxianl.com/2021/02/12/前端/canvas/#73-rotate)
      4. [1.7.4. 7.4 scale](https://liuxianl.com/2021/02/12/前端/canvas/#74-scale)
      5. [1.7.5. 7.5 Transforms](https://liuxianl.com/2021/02/12/前端/canvas/#75-transforms)
   8. [1.8. 八。合成](https://liuxianl.com/2021/02/12/前端/canvas/#八合成)

最新文章

[![49个常用JavaScript方法封装](https://tvax3.sinaimg.cn/large/006djwNZgy1gp42cm8a5aj30xc0irgvw.jpg)](https://liuxianl.com/2021/08/05/前端/49个常用JavaScript方法封装/)

[49 个常用 JavaScript 方法封装](https://liuxianl.com/2021/08/05/前端/49个常用JavaScript方法封装/)2021-08-05

[![正则]()](https://liuxianl.com/2021/07/09/前端/正则/)

[正则](https://liuxianl.com/2021/07/09/前端/正则/)2021-07-09

[![Vue 3 学习笔记]()](https://liuxianl.com/2021/05/05/vue/vue3笔记/)

[Vue 3 学习笔记](https://liuxianl.com/2021/05/05/vue/vue3笔记/)2021-05-05

[![canvas 笔记](https://tvax3.sinaimg.cn/large/006djwNZgy1gp42cm8a5aj30xc0irgvw.jpg)](https://liuxianl.com/2021/02/12/前端/canvas/)

[canvas 笔记](https://liuxianl.com/2021/02/12/前端/canvas/)2021-02-12

[![SassScript]()](https://liuxianl.com/2021/02/11/前端/SassScript/)

[SassScript](https://liuxianl.com/2021/02/11/前端/SassScript/)2021-02-11

©2019 - 2021 By 橘子味雪糕

A world that knows nothing will surprise you if you go on
[![img](https://liuxianl.com/img/ICP.png)湘 ICP 备 20001832 号 - 3](https://beian.miit.gov.cn/#/Integrated/index)
[本网站由![img](https://liuxianl.com/img/%E5%8F%88%E6%8B%8D%E4%BA%91_logo6.png) 提供 CDN 加速服务](https://www.upyun.com/?utm_source=lianmeng&utm_medium=referral)