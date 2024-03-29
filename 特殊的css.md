#### 1、hsl()函数使用色相、饱和度、亮度来定义颜色

HSL 即：色相（Hue）、饱和度（Saturation）、亮度（Lightness）。

色相（H）是色彩的基本属性，就是平常所说的颜色名称，如红色、黄色等。
饱和度（S）是指色彩的纯度，越高色彩越纯，低则逐渐变灰，取0 ~ 100%的数值。
亮度（L），取0 ~ 100%，增加亮度，颜色会向白色变化；减少亮度，颜色会像黑色变化。
HSL是一种将 RGB 色彩模型中的点在圆柱坐标系中的表示法，这两种表示法试图做到比基于笛卡尔坐标系的几何结构 RGB更加直观，通过HSL 的值的逐渐变化，可以得到非常相近的颜色。

| 值                | 描述                                                      |
| ----------------- | --------------------------------------------------------- |
| hue-色相          | 定义色相（0到360）-0（或360）为红色，120为绿色，240为蓝色 |
| saturation-饱和度 | 定义饱和度；0%为灰色，100%全白                            |
| lightness-亮度    | 定义亮度0%为暗，50%为普通，100%为白                       |

```css
.test{
	background-color:hsl(360,50%,50%);
}
```

#### 2、hsla()函数使用色相、饱和度、亮度、透明度来定义颜色

HSLA 即：色相、饱和度、亮度、透明度（英语：Hue, Saturation, Lightness, Alpha ）。

色相（H）是色彩的基本属性，就是平常所说的颜色名称，如红色、黄色等。
饱和度（S）是指色彩的纯度，越高色彩越纯，低则逐渐变灰，取 0-100% 的数值。
亮度（L） 取 0-100%，增加亮度，颜色会向白色变化；减少亮度，颜色会向黑色变化。
透明度（A） 取值 0~1 之间， 代表透明度。

| 值                | 描述                                                      |
| ----------------- | --------------------------------------------------------- |
| hue-色相          | 定义色相（0到360）-0（或360）为红色，120为绿色，240为蓝色 |
| saturation-饱和度 | 定义饱和度；0%为灰色，100%全白                            |
| lightness-亮度    | 定义亮度0%为暗，50%为普通，100%为白                       |
| alpha - 透明度    | 定义透明度 0（透完全明） ~ 1（完全不透明）                |

原文地址：https://blog.csdn.net/weixin_44296929/article/details/102950055

#### 3、关于文本保留两行，溢出隐藏用点点点显示

```css
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  display: -moz-box;
  -moz-line-clamp: 2;
  -moz-box-orient: vertical;
  overflow: hidden;
  white-space: normal;

  word-wrap: break-word;
  word-break: break-all;
```

#### 4、backdrop-filter毛玻璃

#### 5、颜色收集

- 1、取至nestjs官网：

```css
background-color: hsl(204, 25%, 60%);
background-image: radial-gradient(ellipse at center 115%, rgba(255, 255, 255, 0.9), transparent);
```

效果图:

<img src="C:\Users\19979357151\AppData\Roaming\Typora\typora-user-images\image-20230512165058354.png" alt="image-20230512165058354" style="zoom:50%;" />



