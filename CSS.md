# CSS基础

- CSS 是一种描述 HTML 文档样式的语言。

- CSS 描述应该如何显示 HTML 元素。


## CSS简介

- *CSS* 指的是**层叠样式表* (*C*ascading *S*tyle *S*heets**)
- CSS 描述了*如何在屏幕、纸张或其他媒体上显示 HTML 元素*
- CSS *节省了大量工作*。它可以同时控制多张网页的布局
- 外部样式表存储在 *CSS 文件*中

​		***：**也称**级联样式表**。

### 		CSS 解决了一个大问题

- HTML 从未打算包含用于格式化网页的标签！


- CSS 从 HTML 页面中删除了样式格式！


### 		CSS 节省了大量工作！

- 样式定义通常保存在外部 .css 文件中。

- 通过使用外部样式表文件,只需更改一个文件即可更改整个网站的外观！


---

---

---

## CSS 语法

​	CSS 规则集（rule-set）由选择器和声明块组成：

![CSS 选择器](https://www.w3school.com.cn/i/css/selector.gif)

​	以冒号分隔，声明块用花括号括起来

---

---

---

## CSS 选择器

​	CSS 选择器用于“查找”（或选取）要设置样式的 HTML 元素。

​	我们可以将 CSS 选择器分为五类：

- 简单选择器（根据名称、id、类来选取元素）
- [组合器选择器](https://www.w3school.com.cn/css/css_combinators.asp)（根据它们之间的特定关系来选取元素）
- [伪类选择器](https://www.w3school.com.cn/css/css_pseudo_classes.asp)（根据特定状态选取元素）
- [伪元素选择器](https://www.w3school.com.cn/css/css_pseudo_elements.asp)（选取元素的一部分并设置其样式）
- [属性选择器](https://www.w3school.com.cn/css/css_attribute_selectors.asp)（根据属性或属性值来选取元素）

### 	元素选择器

​		元素选择器根据元素名称来选择 HTML 元素

```css
p {
  text-align: center;
  color: red;
}
```

​		就这样直接写元素名 + 花括号

---

- id选择器 (id是唯一的，前面加#)
- 类选择器(前面加.    ，不能以数字开头)
- 通用选择器（*）选择页面上的所有的 HTML 元素
- 分组选择器

```css
h1, h2, p {
  text-align: center;
  color: red;}
```

​		h1,h2,p 的样式都一样就写到一块 以缩减代码

---

---

---

## 如何添加 CSS

- 外部 CSS
- 内部 CSS
- 行内 CSS

---

### 	外部CSS

​		HTML 页面必须在 head 部分的 `<link>` 元素内包含对外部样式表文件的引用

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

- **注意**：外部 .css 文件不应包含任何 HTML 标签！！！
- **注意：**请勿在属性值和单位之间添加空格！！！

---

### 	内部CSS

​		如果一张 HTML 页面拥有唯一的样式，那么可以使用内部样式表。

​		内部样式是在 head 部分的 `<style>` 元素中进行定义

```html
<head>
<style>
body {
  background-color: linen;}
h1 {
  color: maroon;
  margin-left: 40px;} 
</style>
</head>
```

---

### 	行内 CSS

- 行内样式（也称内联样式）可用于为单个元素应用唯一的样式。

- 如需使用行内样式，请将 style 属性添加到相关元素。style 属性可包含任何 CSS 属性


​		**提示：**行内样式失去了样式表的许多优点（通过将内容与呈现混合在一起）

---

### 	多个样式表

​		如果在不同样式表中为同一选择器（元素）定义了一些属性，则将使用最后读		取的样式表中的值

---

### 	层叠顺序

​		页面中的所有样式将按照以下规则“层叠”为新的“虚拟”样式表，其中第一优先		级最高：

1. 行内样式（在 HTML 元素中）
2. 外部和内部样式表（在 head 部分）
3. 浏览器默认样式

​		因此，行内样式具有最高优先级，并且将覆盖外部和内部样式以及浏览器默认		样式。

---

---

---

## 注释

​	位于 `<style>` 元素内的 CSS 注释，以 `/*` 开始，以 `*/` 结束

---

---

---

## 颜色

​	指定颜色是通过使用预定义的颜色名称，或 RGB、HEX、HSL、RGBA、HSLA 值

- `"background-color:Tomato;`颜色名
- `color:Tomato;`文本颜色
- `border:2px solid Tomato;`边框颜色
- `background-color:rgba(255, 99, 71, 0.5);`颜色值

---

---

---

## RGB 颜色

### 	RGB 值

- 在 CSS 中，可以使用下面的公式将颜色指定为 RGB 值：

- rgb(*red*, *green*, *blue*)

- 黑色就是  rgb(0,0,0)

- 白色	rgb(255,255,255)


---

### 	RGBA 值

- RGBA 颜色值是具有 alpha 通道的 RGB 颜色值的扩展 - 它指定了颜色的不透明度。

- RGBA 颜色值指定为：

- rgba(*red*, *green*, *blue*, *alpha*)


---

---

---

## HEX 颜色

​	HEX 值

​	在 CSS 中，可以使用以下格式的十六进制值指定颜色：

​	#*rrggbb*

​	其中 rr（红色）、gg（绿色）和 bb（蓝色）是介于 00 和 ff 之间的十六进制值	         	（与十进制 0-255 相同）

​	\#ff0000 显示为红色，因为红色设置为最大值（ff），其他设置为最小值（00）

![image-20231203171455367](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231203171455367.png)

​	根据样例记忆

---

---

---

## HSL 颜色

### 		HSL 值

- 在 CSS 中,可以使用色相,饱和度和明度（HSL）来指定颜色，格式如下：

- hsla(*hue*, *saturation*, *lightness*)

- 色相(hue)是色轮上从 0 到 360 的度数.0 是红色,120 是绿色,240 是蓝色。

- 饱和度(saturation)是一个百分比值,0％ 表示灰色阴影,而 100％ 是全色。

- 亮度(lightness)也是百分比,0％是黑色,50％ 是既不明也不暗,100％是白色


![image-20231203171650722](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231203171650722.png)

---

### 	饱和度可以描述为颜色的强度。

- ​		100％ 是纯色，没有灰色阴影

- ​		50％ 是 50％ 灰色，但是您仍然可以看到颜色。

- ​		0％ 是完全灰色，您无法再看到颜色

  ### 亮度

​		颜色的明暗度可以描述为要赋予颜色多少光，其中 0％ 表示不亮（黑色），		50％ 表示 50％ 亮（既不暗也不亮），100％ 表示全明（白）。

​		提醒：通常通过将色调和饱和度设置为 0 来定义灰色阴影，并将亮度从 0％ 到 					100％ 进行调整可以得到更深/更浅的阴影

---

### 	HSLA 值

​		HSLA 颜色值是带有 Alpha 通道的 HSL 颜色值的扩展 -指定了颜色不透明度。

​		HSLA 颜色值指定为：

​		hsla(*hue*, *saturation*, *lightness*, *alpha*)

​		*alpha* 参数是介于 0.0（完全透明）和 1.0（完全不透明）之间的数字

---

---

---

## 背景

### 	background-color	

​		指定元素的背景色

```css
body {
  background-color: lightblue;}
```

​		也可以用十六进制，RGB等等上节讲到的

---

### 	不透明度 / 透明度

​		opacity 属性指定元素不透明度.取值范围为 0.0 - 1.0.值越低,越透明

```css
div {
  background-color: green;
  opacity: 0.3;}
```

​		**注意：**使用 `opacity` 属性为元素的背景添加透明度时，其所有子元素都继承					相同的透明度。这可能会使完全透明的元素内的文本难以阅读。

---

### 	使用 RGBA 的透明度

​		如果不希望对子元素应用不透明度，例如上面的例子，使用 *RGBA* 颜色值

---

---

---

## 背景图像

### 		CSS 背景图像

- ​		`background-image` 属性指定用作元素背景的图像。

- ​		默认情况下，图像会重复，以覆盖整个元素。

- ​		还可以为特定元素设置背景图像，例如 <p> 元素


---

---

---

## 背景重复

- 默认情况下，`background-image` 属性在水平和垂直方向上都重复图像。

- 某些图像应只适合水平或垂直方向上重复，否则它们看起来会很奇怪

- 如果某些图像仅在水平方向重复 (`background-repeat: repeat-x;`)，则背景看	起来会更好

- 显而易见:如需垂直重复图像,设置 `background-repeat: repeat-y;`。

---

### 	background-repeat: no-repeat

​		指定只显示一次背景图像

---

### 	background-position

​		指定背景图像的位置

​		把背景图片放在右上角：

```css
body {
  background-image: url("tree.png");
  background-position: right top;
}
```

---

## 背景附着

### 	background-attachment

​		指定背景图像是应该滚动还是固定的（不会随页面的其余部分一起滚动）

​		  `background-attachment: fixed;`固定背景图像

​		  `background-attachment: scroll;`随页面一起滚动

---

## 背景简写

### 	 background - 简写属性

​		如需缩短代码，也可以在一个属性中指定所有背景属性。它被称为简写属性

```css
body {
  background: #ffffff url("tree.png") no-repeat right top;
}
```

​		在使用简写属性时，属性值的顺序为：

- `background-color`
- `background-image`
- `background-repeat`
- `background-attachment`
- `background-position`

​		属性值之一缺失并不要紧，只要按照此顺序设置其他值即可。请注意，在上面		的例子中，我们没有使用 background-attachment 属性，因为它没有值

​		注释：能记住你就用吧 -__-

----

## 边框

​	CSS `border` 属性允许您指定元素边框的样式、宽度和颜色。

### 	边框样式

​		`border-style` 属性指定要显示的边框类型。

- `dotted` - 定义点线边框
- `dashed` - 定义虚线边框
- `solid` - 定义实线边框
- `double` - 定义双边框
- `groove` - 定义 3D 坡口边框。效果取决于 border-color 值
- `ridge` - 定义 3D 脊线边框。效果取决于 border-color 值
- `inset` - 定义 3D inset 边框。效果取决于 border-color 值
- `outset` - 定义 3D outset 边框。效果取决于 border-color 值
- `none` - 定义无边框
- `hidden` - 定义隐藏边框

​			`border-style` 属性可以设置一到四个值（用于上边框、右边框、下边框			和左边框）。

​			p.mix {border-style: dotted dashed solid double;}**这叫混合边框**

---

## 边框宽度

### 	边框宽度

​		`border-width`指定四个边框的宽度

​		可以将宽度设置为特定大小（以 px、pt、cm、em 计），也可以使用以下三个		预定义值之一：thin、medium 或 thick

### 	特定边的宽度

​		`border-width` 属性可以设置一到四个值(用于上边框,右边框,下边框和左边框)

```css
p.three {
  border-style: solid;
  border-width: 25px 10px 4px 35px; /* 上边框 25px，右边框 10px，下边框 4px，左边框 35px */}
```

---

## 边框颜色

### 		边框颜色

​		`border-color` 属性用于设置四个边框的颜色。

- name - 指定颜色名，比如 "red"
- HEX - 指定十六进制值，比如 "#ff0000"
- RGB - 指定 RGB 值，比如 "rgb(255,0,0)"
- HSL - 指定 HSL 值，比如 "hsl(0, 100%, 50%)"
- transparent

​		**注释：**如果未设置 `border-color`，则它将继承元素的颜色

---

### 	特定边框的颜色

​		`border-color` 属性可以设置一到四个值（用于上边框、右边框、下边框和左		边框）

​		  `border-color: red green blue yellow; /* 上红、右绿、下蓝、左黄 */`

---

### 	HEX 值

​		边框的颜色也可以使用十六进制值（HEX）来指定

​		  border-color: #ff0000; /* 红色 */

---

### 	RGB 值（同下）

---

### 	HSL值（CSS颜色中已讲）

---

---

---

## 边框各边

### 	  单独的边

​		一些属性可用于指定每个边框（顶部、右侧、底部和左侧）

```css
p {
  border-top-style: dotted;
  border-right-style: solid;
  border-bottom-style: dotted;
  border-left-style: solid;}
```

### 	不同的边框样式

```css
p {
  border-style: dotted solid;}
```

​		它的工作原理是这样的：

​		如果 `border-style` 属性设置四个值：

#### 		border-style: dotted solid double dashed;

- 上边框是虚线
- 右边框是实线
- 下边框是双线
- 左边框是虚线

​			如果 `border-style` 属性设置三个值：

#### 		border-style: dotted solid double;

- 上边框是虚线
- 右和左边框是实线
- 下边框是双线

​			如果 `border-style` 属性设置两个值：

#### 		border-style: dotted solid;

- 上和下边框是虚线
- 右和左边框是实线

​			如果 `border-style` 属性设置一个值：

#### 		border-style: dotted;

- 四条边均为虚线

​		注意：`border-width` 和 `border-color` 也同样适用

---

---

---

## 简写边框属性

### 	Border - 简写属性

​		就像您在上一章中所见，处理边框时要考虑许多属性。

​		为了缩减代码，也可以在一个属性中指定所有单独的边框属性。

​		`border` 属性是以下各个边框属性的简写属性：

- `border-width`
- `border-style`（必需）
- `border-color`

---

---

---

## 圆角边框

​	圆角边框

​		`border-radius` 属性用于向元素添加圆角边框

​		`border-radius: 5px;`

---

---

---

## 外边距

### 	外边距

​		CSS `margin` 属性用于在任何定义的边框之外，为元素周围创建空间。

​		通过 CSS，您可以完全控制外边距。有一些属性可用于设置元素每侧（上、		右、下和左）的外边距

---

### 	Margin - 单独的边

​		CSS 拥有用于为元素的每一侧指定外边距的属性：

- `margin-top`
- `margin-right`
- `margin-bottom`
- `margin-left`

​		所有外边距属性都可以设置以下值：

- auto - 浏览器来计算外边距
- *length* - 以 px、pt、cm 等单位指定外边距
- % - 指定以包含元素宽度的百分比计的外边距
- inherit - 指定应从父元素继承外边距

​		**提示：**允许负值

---

### 	Margin - 简写属性

​		`margin` 属性是以下各外边距属性的简写属性：

- `margin-top`
- `margin-right`
- `margin-bottom`
- `margin-left`

#### 	工作原理：

​		如果 `margin` 属性有四个值：<u>(上右下左</u>好好记！！！)

- margin: 25px 50px 75px 100px;

- - 上外边距是 25px
  - 右外边距是 50px
  - 下外边距是 75px
  - 左外边距是 100px

​		三个值：

- margin: 25px 50px 75px;

- - 上外边距是 25px
  - 右和左外边距是 50px
  - 下外边距是 75px

​		两个值：

- margin: 25px 50px;

- - 上和下外边距是 25px
  - 右和左外边距是 50px

​		一个值：

- margin: 25px;

- 所有四个外边距都是 25px

---

### 	auto 值

​		您可以将 margin 属性设置为 `auto`，以使元素在其容器中水平居中。

​		然后，该元素将占据指定的宽度，并且剩余空间将在左右边界之间平均分配

### 	 inherit 值

​		本例使 `<p class="ex1">` 元素的左外边距继承自父元素（`<div>`）：

```css
div {
  border: 1px solid red;
  margin-left: 100px;
}

p.ex1 {
  margin-left: inherit;
}
```

---

---

---

## 外边距合并

​	**外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。**

​	**合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者**

<img src="https://www.w3school.com.cn/i/css/margin_collapsing_1.gif" alt="CSS 外边距合并实例 1" style="zoom:80%;" />

​	 **注释：**只有**普通文档流中块框**的垂直外边距才会发生外边距合并。行内框、浮				  动框或绝对定位之间的外边距不会合并

---

---

---

## 内边距

​	`padding` 属性用于在任何定义的边界内的元素内容周围生成空间。

​	通过 CSS，您可以完全控制内边距（填充）。有一些属性可以为元素的每一侧	   	(上、右、下和左侧)设置内边距

### 	Padding - 单独的边

​		CSS 拥有用于为元素的每一侧指定内边距的属性：

- `padding-top`
- `padding-right`
- `padding-bottom`
- `padding-left`

​		所有内边距属性都可以设置以下值：

- *length* - 以 px、pt、cm 等单位指定内边距
- % - 指定以包含元素宽度的百分比计的内边距
- inherit - 指定应从父元素继承内边距

​		**提示：**不允许负值

---

### 	简写属性

​		为了缩减代码，可以在一个属性中指定所有内边距属性。

​		`padding` 属性是以下各内边距属性的简写属性：

- `padding-top`
- `padding-right`
- `padding-bottom`
- `padding-left`

​		工作原理参考上文

### 	内边距和元素宽度

​		CSS `width` 属性<u>指定元素内容区域的宽度</u>。内容区域是元素（盒模型）的内边		距、边框和外边距内的部分。

​		因此，如果元素拥有<u>指定的宽度</u>，则添加到该元素的内边距<u>会添加到元素的总		宽度</u>中。这通常是不希望的结果

​		若要将宽度保持为 300px，无论填充量如何，那么您可以使用 `box-sizing` 属		性。这将导致元素<u>保持其宽度</u>。如果<u>增加内边距</u>，则可用的<u>内容空间会减少</u>

---

---

---

## 高度和宽度

​	`height` 和 `width` 属性用于设置元素的高度和宽度。

​	height 和 width 属性不包括内边距、边框或外边距。它设置的是元素内边距、边	框以及外边距内的区域的高度或宽度

### 	 高度和宽度值

​		`height` 和 `width` 属性可设置如下值：

- `auto` - 默认。浏览器计算高度和宽度。
- `*length*` - 以 px、cm 等定义高度/宽度。
- `%` - 以包含块的百分比定义高度/宽度。
- `initial` - 将高度/宽度设置为默认值。
- `inherit` - 从其父值继承高度/宽度

### 	max-width

​		用于设置元素的最大宽度。

​		可以用长度值（例如 px、cm 等）或包含块的百分比（％）来指定 max-width	   （最大宽度），也可以将其设置为 none（默认值。意味着没有最大宽度）。

​		当浏览器窗口小于元素的宽度（500px）时，会发生之前那个 `<div>` 的问题。		然后，浏览器会将水平滚动条添加到页面。

​		在这种情况下，使用 `max-width` 能够改善浏览器对小窗口的处理。

---

---

---

## 框模型

### 		框模型

​		所有 HTML 元素都可以视为方框

​		CSS 框模型实质上是一个包围每个 HTML 元素的框。它包括：外边距、边框、		内边距以及实际的内容

<img src="https://www.w3school.com.cn/i/css/boxmodel.gif" alt="CSS 框模型" style="zoom:67%;" />

- *内容* - 框的内容，其中显示文本和图像。
- *内边距* - 清除内容周围的区域。内边距是透明的。
- *边框* - 围绕内边距和内容的边框。
- *外边距* - 清除边界外的区域。外边距是透明的

​		注意：外边距默认是透明的，因此不会遮挡其后的任何元素

​					背景应用于由内容和内边距、边框组成的区域

​		**提示：**外边距可以是负值，而且在很多情况下都要使用负值的外边距

---

### 	宽度和高度

​		**重要提示：**使用 CSS 设置元素的 width 和 height 属性时，只需设置内容区域							 的宽度和高度。要计算元素的完整大小，还必须把内边距、边框和							 外边距加起来

元素总宽度 = 宽度 + 左内边距 + 右内边距 + 左边框 + 右边框 + 左外边距 + 右外边距

元素总高度 = 高度 + 上内边距 + 下内边距 + 上边框 + 下边框 + 上外边距 + 下外边距

---

---

---

## 轮廓

### 	轮廓

​		轮廓是在元素周围绘制的一条线，在边框之外，以凸显元素

- `outline-style`
- `outline-color`
- `outline-width`
- `outline-offset`
- `outline`

​		**注意：**轮廓与[边框](https://www.w3school.com.cn/css/css_border.asp)不同!!!

- 轮廓是在元素边框之外绘制的，并且可能与其他内容重叠
- 轮廓也不是元素尺寸的一部分
- 元素的总宽度和高度不受轮廓线宽度的影响

---

### 	轮廓样式

- `dotted` - 定义点状的轮廓。
- `dashed` - 定义虚线的轮廓。
- `solid` - 定义实线的轮廓。
- `double` - 定义双线的轮廓。
- `groove` - 定义 3D 凹槽轮廓。
- `ridge` - 定义 3D 凸槽轮廓。
- `inset` - 定义 3D 凹边轮廓。
- `outset` - 定义 3D 凸边轮廓。
- `none` - 定义无轮廓。
- `hidden` - 定义隐藏的轮廓

---

---

---

## 轮廓宽度

### 	轮廓宽度

​		`outline-width` 属性指定轮廓的宽度，并可设置如下值之一：

- thin（通常为 1px）
- medium（通常为 3px）
- thick （通常为 5px）
- 特定尺寸（以 px、pt、cm、em 计）

---

---

---

## 轮廓颜色

### 	轮廓颜色

​		`outline-color` 属性用于设置轮廓的颜色

- *name* - 指定颜色名，比如 "red"
- HEX - 指定十六进制值，比如 "#ff0000"
- RGB - 指定 RGB 值，比如 "rgb(255,0,0)"
- HSL - 指定 HSL 值，比如 "hsl(0, 100%, 50%)"
- invert - 执行颜色反转（确保轮廓可见，无论是什么颜色背景）

### 	反转颜色

​		使用 `outline-color: invert`，执行了颜色反转。这样可以确保无论颜色背		景如何，轮廓都是可见的.

---

---

---

## 轮廓简写

### 	Outline - 简写属性

​		`outline` 属性是用于设置以下各个轮廓属性的简写属性：

- `outline-width`
- `outline-style`（必需）
- `outline-color`

​		注释：可指定一个、两个或三个值。值的顺序无关紧要

---

---

---

## 轮廓偏移

### 		轮廓偏移

​		`outline-offset` 属性在元素的轮廓与边框之间添加空间。元素及其轮廓之		间的空间是透明的

---

---

---

## 文本

### 		文本颜色

​		`color` 属性用于设置文本的颜色。颜色由以下值指定：

- 颜色名 - 比如 "red"
- 十六进制值 - 比如 "#ff0000"
- RGB 值 - 比如 "rgb(255,0,0)"

​		提示：如果您定义了 `color` 属性，则还必须定义 `background-color` 属性

---

---

---

## 文本对齐

​	文本对齐

​		`text-align` 属性用于设置文本的水平对齐方式

#### 	justify

​		 `text-align: justify;`

​		将拉伸每一行，以使每一行具有相等的宽度，并且左右边距是直的(如报纸)

---

### 	文本方向

​		`direction` 和 `unicode-bidi` 属性可用于更改元素的文本方向

![image-20231207231137714](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207231137714.png)

​		注释：direction:rtl; 使文本靠右

​					 unicode-bidi:bidi-override; 使字母自右向左

---

### 	垂直对齐

​		`vertical-align` 属性设置元素的垂直对齐方式

![image-20231207231351554](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207231351554.png)

---

---

---

## 文字装饰

### 	文字装饰

​		`text-decoration` 属性用于设置或删除文本装饰。

​		`text-decoration: none;` 通常用于从链接上删除下划线

![image-20231207231449694](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207231449694.png)

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207231516515.png" alt="image-20231207231516515" style="zoom: 67%;" />

---

---

---

## 文本转换

### 	文本转换

​		`text-transform` 属性用于指定文本中的大写和小写字母

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207231637894.png" alt="image-20231207231637894" style="zoom:67%;" />

---

---

---

## 文字间距

### 	文字缩进

​		`text-indent` 属性用于指定文本第一行的缩进

​		`text-indent: 50px;`

---

### 	字母间距

​		`letter-spacing` 属性用于指定文本中字符之间的间距

![image-20231207231830912](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207231830912.png)

---

### 	行高

​		`line-height` 属性用于指定行之间的间距

​		提示：默认的多是1.1-1.2；

​		`line-height:1.2;`

---

### 	字间距

​		`word-spacing` 属性用于指定文本中单词之间的间距

​		提示：正常 `0px` 就可以

---

### 	空白

​		`white-space` 属性指定元素内部空白的处理方式

​		 `white-space: nowrap;`能禁用元素内的文本换行

---

---

---

## 文本阴影

### 	文本阴影

​		`text-shadow` 属性为文本添加阴影

​		`text-shadow: 2px 2px 5px red;`

​		<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207232443431.png" alt="image-20231207232443431" style="zoom:50%;" />

​		注释：2px为水平阴影和垂直阴影

​					5px为模糊效果

​					red为阴影颜色

---

---

---

## 字体

### 	通用字体族

​		在 CSS 中，有五个通用字体族：

- 衬线字体（Serif）- 在每个字母的边缘都有一个小的笔触。它们营造出一种形式感和优雅感。
- 无衬线字体（Sans-serif）- 字体线条简洁（没有小笔画）。它们营造出现代而简约的外观。
- 等宽字体（Monospace）- 这里所有字母都有相同的固定宽度。它们创造出机械式的外观。
- 草书字体（Cursive）- 模仿了人类的笔迹。
- 幻想字体（Fantasy）- 是装饰性/俏皮的字体

### 	font-family 属性

​		注意：font-family 属性应包含多个字体名称作为“后备”系统，以确保浏览器/					操作系统之间的最大兼容性

​		e.g	` font-family: Arial, Helvetica, sans-serif;`

---

---

---

## 字体样式

### 	字体样式

​		`font-style` 属性主要用于指定斜体文本

- normal - 文字正常显示
- italic - 文本以斜体显示
- oblique - 文本为“倾斜”（倾斜与斜体非常相似，但支持较少）

​		e.g	`font-style: italic;`

---

### 	字体粗细

​		`font-weight` 属性指定字体的粗细

- normal
- bold
- lighter
- 具体数值（bold == 900）（没有单位！！！）

---

### 	字体变体

​		`font-variant` 属性指定是否以 small-caps 字体（小型大写字母）显示文本

![image-20231207233119627](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207233119627.png)

---

---

---

## 字体大小

### 	字体大小

​		`font-size` 属性设置文本的大小

​		font-size 值可以是**<u>绝对或相对大小</u>**

​		绝对尺寸：

- 将文本设置为指定大小
- 不允许用户在所有浏览器中更改文本大小（可访问性不佳）
- 当输出的物理尺寸已知时，绝对尺寸很有用

​		相对尺寸：

- 设置相对于周围元素的大小
- 允许用户在浏览器中更改文本大小

​		**注释：**如果您没有指定字体大小，则普通文本（如段落）的默认大小为 16px					（16px = 1em）

---

### 		像素设置字体大小

​		font-size:40px; 标题1

​		font-size:30px; 标题2

​		font-size:14px; 段落

---

### 	em 设置字体大小

​		使用方法同像素，根据上文公式换算大小

---

### 	百分比

​		`font-size: 100%;`百分比会等比例缩小所有大小的文本

​		100%为正常

---

---

---

## 谷歌字体

​	可以使用 Google Fonts API 向页面添加数百种其他字体。

​	只需添加一个样式表链接并引用您选择的字体系列

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Sofia">
<style>
body {
  font-family: "Sofia";
  font-size: 22px;
}
</style>
</head>
```

---

---

---

## 字体属性

​	`font` 属性是以下属性的简写属性：

- `font-style`
- `font-variant`
- `font-weight`
- `font-size/line-height`(必须)
- `font-family`(必须)

---

---

---

## 图标

​	如何添加图标

​	向 HTML 页面添加图标的最简单方法是使用图标库，比如 Font Awesome。

​	将指定的图标类的名称添加到任何行内 HTML 元素（如 `<i>` 或 `<span>`）

### 	Font Awesome 图标

​		请访问 fontawesome.com

```html
<head>
<script src="https://kit.fontawesome.com/a076d05399.js"></script>
</head>
<body>

<i class="fas fa-cloud"></i>
<i class="fas fa-heart"></i>
<i class="fas fa-car"></i>
<i class="fas fa-file"></i>
<i class="fas fa-bars"></i>

</body>
```

![image-20231207234538917](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207234538917.png)

---

### 	Bootstrap 图标

​		`<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">`

​		`<i class="glyphicon glyphicon-cloud"></i>`

---

### 	Google 图标

​	`<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">`

---

---

---

## 链接

### 	设置链接样式

​		链接可以使用任何 CSS 属性（例如 `color`、`font-family`、`background` 等）		来设置样式

- `a:link` - 正常的，未访问的链接
- `a:visited` - 用户访问过的链接
- `a:hover` - 用户将鼠标悬停在链接上时
- `a:active` - 链接被点击时

1. ​	a:hover 必须 a:link 和 a:visited 之后
2. ​    a:active 必须在 a:hover 之后

---

### 	链接按钮

​		<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207235401587.png" alt="image-20231207235401587" style="zoom:50%;" />

---

---

---

## 列表

```css
<style>
ul.a {
  list-style-type: circle;
}
</style>
<ul class="a">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Coca Cola</li>
</ul>
```
---

### 	图像作为列表项标记

​		`list-style-image` 属性将图像指定为列表项标记

![image-20231207235641225](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207235641225.png)

---

### 	定位列表项标记

​		`list-style-position` 属性指定列表项标记（项目符号）的位置

![image-20231207235739111](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231207235739111.png)

---

### 	删除默认设置

​		`list-style-type:none` 属性也可以用于删除标记/项目符号

​		注意：列表还拥有默认的外边距和内边距。要删除此内容，请在 <ul> 或 					 `<ol>` 中添加 `margin:0` 和 `padding:0`

---

### 	简写属性

​		`list-style` 属性是一种简写属性。它用于在一条声明中设置所有列表属性

```css
ul {
  list-style: square inside url("sqpurple.gif");
}
```

​		属性值的顺序为：

- `list-style-type`（如果指定了 list-style-image，那么在由于某种原因而无法显示图像时，会显示这个属性的值）
- `list-style-position`（指定列表项标记应显示在内容流的内部还是外部）
- `list-style-image`（将图像指定为列表项标记）

---

### 	列表的颜色样式

​		注意：会影响整个列表

```css
ol {
  background: #ff9999;
  padding: 20px;
}
ul li {
  background: #cce5ff;
  margin: 5px;
}
```

---

---

---

## 表格

### 	边框

​		如需在 CSS 中设置表格边框，请使用 `border` 属性

```css
table, th, td {
  border: 1px solid black;
}
```

​		**注意：**上例中的表格拥有双边框。这是因为 table 和 <th> 和 <td> 元素都有					 单独的边框

---

### 	全宽表格

​		需要一个可以覆盖整个屏幕（全宽）的表格，请为 `<table>` 元素添加 

​		width: 100%

---

### 	合并表格边框

​		`border-collapse` 属性设置是否将表格边框折叠为单一边框

```css
table {
  border-collapse: collapse;
}
```

![image-20231208000603450](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231208000603450.png)

​		如果只希望表格周围有边框，则仅需为 `<table>` 指定 `border` 属性：

```css
table {
  border: 1px solid black;
}
```

---

### 		样式

-  `width` 和 `height` 属性定义宽度高度(百分比，像素，em)
- `text-align`水平对齐
- `vertical-align`垂直对齐
- `padding`内边距
- `border-bottom: 1px solid #ddd;`内边距
- `tr:hover {background-color: #f5f5f5;}`可悬停表格
- `nth-child()`条状表格(`为偶数行添加background-color`)

---

### 	响应式表格

​		如果屏幕太小而无法显示全部内容，则响应式表格会显示水平滚动条

​		在 <table> 元素周围添加带有 `overflow-x:auto` 的容器元素（例如 				<div>），以实现响应式效果

```html
<div style="overflow-x:auto;">
<table>
... table content ...
</table>
</div>
```

---

---

---

# CSS中级教程

## display 属性

​	`display` 属性是用于控制布局的最重要的 CSS 属性

### 	display 属性

​		`display` 属性规定是否/如何显示元素

​		HTML都有一个默认的 display 值，具体取决于它的元素类型。大多数元素的		默认 display 值为 `block` 或 `inline`

### 	块级元素（block element）

​		总是从新行开始，并占据可用的全部宽度

- `<div>`
- `<h1> - <h6>`
- `<p>`
- `<form>`
- `<header>`
- `<footer>`
- `<section>`

---

### 	行内元素（inline element）

​		不从新行开始，仅占用所需的宽度。

​		行内元素的一些例子：

- `<span>`
- `<a>`
- `<img>`

---

### 	Display: none;

​		通常与 JavaScript 一起使用，以隐藏和显示元素，而无需删除和重新创建它们

---

### 	覆盖默认的 Display 值

​		  `display: inline;`	实现水平菜单

​		  `display: block;`		使行元素变成块元素

---

### 	隐藏元素

​		`display:none;`	隐藏元素，并且页面删除该元素的位置

​		`visibility: hidden;`	正如其名，保留位置，视觉隐藏

---

---

---

##  max-width

### 	width、max-width 和 margin: auto

- 设置块级元素的 `width` 将防止其延伸到其容器的边缘

- 外边距设置为 auto，以将元素在其容器中水平居中

​		**注意：**当浏览器窗口小于元素的宽度时，上面这个 `<div>` 会发生问题。<u>浏览					器会将水平滚动条添加到页面</u>

​		在这种情况下，使用 `max-width` 可以改善浏览器对小窗口的处理

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231208173135768.png" alt="image-20231208173135768" style="zoom:50%;" />

---

---

---

## position

​	规定应用于元素的定位方法的类型(static、relative、fixed、absolute 或 sticky)

- static(静态)
- relative(相对)
- fixed(固定)
- absolute(定位最近元素，好用)
- sticky(滚动到哪里他都在)

​	  注意:必须至少指定 `top`、`right`、`bottom` 或 `left` 之一，以便粘性定位起作用

---

### 	重叠元素

​		`z-index` 属性指定元素的堆栈顺序

```css
img {
  position: absolute;
  z-index: -1;}
```

​		注意:如果两个定位的元素重叠而未指定 `z-index`，则位于 HTML 代码中最后				  的元素将显示在顶部。

---

### 	定位图像中的文本

​		<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231208175122338.png" alt="image-20231208175122338" style="zoom:67%;" />

---

---

---

## 溢出

​	 **overflow 属性控制对太大而区域无法容纳的内容的处理方式**

​	overflow指定在元素内容太大而无法放入指定区域时是剪裁内容还是添加滚动条

​	`overflow` 属性可设置以下值：

- `visible` - 默认。溢出没有被剪裁。内容在元素框外渲染
- `hidden` - 溢出被剪裁，其余内容将不可见
- `scroll` - 溢出被剪裁，同时添加滚动条以查看其余内容
- `auto` - 与 `scroll` 类似，但仅在必要时添加滚动条

​		**注释：**`overflow` 属性仅适用于具有指定高度的块元素

---

### 	overflow-x 和 overflow-y

​		规定是仅水平还是垂直地（或同时）更改内容的溢出：

- `overflow-x` 指定如何处理内容的左/右边缘。
- `overflow-y` 指定如何处理内容的上/下边缘

```css
div {
  overflow-x: hidden; /* 隐藏水平滚动栏 */
  overflow-y: scroll; /* 添加垂直滚动栏 */}
```

---

---

---

## 浮动和清除

​		CSS `float` 属性规定元素如何浮动。

​		CSS `clear` 属性规定哪些元素可以在清除的元素旁边以及在哪一侧浮动

---

### 	float 属性

​	`float` 属性用于定位和格式化内容，例如让图像向左浮动到容器中的文本那里。

- left - 元素浮动到其容器的左侧
- right - 元素浮动在其容器的右侧
- none - 元素不会浮动（将显示在文本中刚出现的位置）。默认值。
- inherit - 元素继承其父级的 float 值

​	最简单的用法是，`float` 属性可实现（报纸上）文字包围图片的效果

---

---

---

## clear 和 clearfix

### 	clear 属性

​		`clear` 属性指定哪些元素可以浮动于被清除元素的旁边以及哪一侧

- none - 允许两侧都有浮动元素。默认值
- left - 左侧不允许浮动元素
- right- 右侧不允许浮动元素
- both - 左侧或右侧均不允许浮动元素
- inherit - 元素继承其父级的 clear 值

​		注释：就是浮动的元素不能在有clear的元素内浮动

---

### 	clearfix Hack

​		如果一个元素比包含它的元素高，并且它是浮动的，它将“溢出”到其容器之外

​		 `overflow: auto;`可以使其不溢出

---

---

---

## display: inline-block

- 与 `display: inline` 相比，主要区别在于 `display: inline-block` 允许在元	素上设置宽度和高度

- 与 display: block 相比，主要区别在于 display：inline-block 在元素之后不添加	换行符，因此该元素可以位于其他元素旁边

---

---

---

## 对齐

- `margin:auto`居中对齐
- `position:absolute`左右对齐
- `float`左右对齐
- `padding`垂直对齐
- `line-height`垂直对齐
- `display: flex;`垂直对齐

---

### 	垂直对齐 - 使用 position 和 transform

```css
.center { 
  height: 200px;
  position: relative;
}
.center p {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

---

---

---

## 组合器

​	组合器解释选择器之间关系的某种机制

​	选择器可以包含多个简单选择器

- 后代选择器 (空格)
- 子选择器 (`>`)
- 相邻兄弟选择器 (`+`)
- 通用兄弟选择器 (`~`)

---

---

---

## 伪类

### 	  什么是伪类？

​		伪类用于定义元素的特殊状态

- 设置鼠标悬停在元素上时的样式
- 为已访问和未访问链接设置不同的样式
- 设置元素获得焦点时的样式

---

### 	语法

```css
selector:pseudo-class {
  property: value;}
```

---

### 	锚伪类

​		链接能够以不同的方式显示：

```css
a:link {/* 未访问的链接 */
  color: #FF0000;}
a:visited {/* 已访问的链接 */
  color: #00FF00;}
a:hover {/* 鼠标悬停链接 */
  color: #FF00FF;}
a:active {/* 已选择的链接 */
  color: #0000FF;}
```

​		**注意：**`a:hover` 必须在 CSS 定义中的 `a:link` 和 `a:visited` 之后，才能生					效！`a:active` 必须在 CSS 定义中的 `a:hover` 之后才能生效！伪类名称					对大小写不敏感

---

### 	first-child 伪类

​		`:first-child` 伪类与指定的元素匹配：该元素是另一个元素的第一个子元素

​		注释：就是某个元素中或整个代码中的第一个该元素生效；

```css
p:first-child {
  color: blue;}
```

#### 	匹配所有 `<p>` 元素中的首个 `<i>` 元素

```css
p i:first-child {
  color: blue;}
```

#### 	匹配所有首个 `<p>` 元素中的所有 `<i>` 元素

```css
p:first-child i {
  color: blue;}
```

​		**<u>注释：注意区别！！！</u>**

#### 	lang 伪类

​		`:lang` 伪类允许您为不同的语言定义特殊的规则

```css
q:lang(en) {
  quotes: "~" "~";
}
<p>Some text <q lang="no">A quote in a paragraph</q> Some text.</p>
```

![image-20231209002130827](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231209002130827.png)

---

---

---

## 伪元素

### 	什么是伪元素？

​		CSS 伪元素用于设置元素指定部分的样式

- 设置元素的首字母、首行的样式
- 在元素的内容之前或之后插入内容

---

### 	语法

```css
selector::pseudo-element {
  property: value;}
```

---

### 	::first-line 伪元素

​		用于向文本的首行添加特殊样式

​		**注意：**`::first-line` 伪元素只能应用于块级元素

​					伪元素可以与 CSS 类结合使用

- 字体属性
- 颜色属性
- 背景属性
- word-spacing
- letter-spacing
- text-decoration
- vertical-align
- text-transform
- line-height
- clear

​		拓展：CSS3 中，双冒号取代了伪元素的单冒号表示法

​					注意区分*伪类*和*伪元素*的尝试

---

### 	::first-letter 伪元素

​		`::first-letter` 伪元素用于向文本的首字母添加特殊样式

​		**注意：**`::first-letter` 伪元素只能应用于块级元素

---

### 	多个伪元素

​		也可以组合几个伪元素

---

### 	::before 伪元素

​		`::before` 伪元素可用于在元素内容之前插入一些内容

---

### 	::after 伪元素

​		`::after` 伪元素可用于在元素内容之后插入一些内容

---

### 	::selection 伪元素

​		`::selection` 伪元素匹配用户选择的元素部分。

​		以下 CSS 属性可以应用于 `::selection`：

- `color`
- `background`
- `cursor`
- `outline`

---

---

---

## 不透明度 / 透明度

​	`opacity` 属性指定元素的不透明度

### 	透明图像

​		`opacity` 属性的取值范围为 0.0-1.0。值越低，越透明

---

### 	透明悬停效果

​		`opacity` 属性通常与 `:hover` 选择器一同使用，这样就可以在鼠标悬停时更改不透明度

---

### 	透明盒

​		使用 `opacity` 属性为元素的背景添加透明度时，其所有子元素都继承相同的透明度

```css
div {
  opacity: 0.3;
}
```

---

### 	使用 RGBA 的透明度

---

---

---

## 导航栏

### 	导航栏 = 链接列表

​		导航栏需要标准 HTML 作为基础

​		导航栏基本上就是链接列表，因此使用 <ul> 和 <li> 元素会很有意义

---

## 垂直导航栏

​		创建背景色为灰色的基础垂直导航栏，并在用户将鼠标移到链接上时改变链接		的背景色：

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  width: 200px;
  background-color: #f1f1f1;}
li a {
  display: block;
  color: #000;
  padding: 8px 16px;
  text-decoration: none;}/* 鼠标悬停时改变链接颜色 */
li a:hover {
  background-color: #555;
  color: white;}
```

---

### 	活动/当前导航链接

​		向当前链接添加 "active" 类，以使用户知道他/她在哪个页面上

```css
.active {
  background-color: #4CAF50;
  color: white;}
```

---

### 	居中链接以及添加边框

​		把 `text-align:center` 添加到 `<li> 或 <a>`，使链接居中

---

### 	全高固定垂直导航栏

​		创建全高的“粘性”侧面导航

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  width: 25%;
  background-color: #f1f1f1;
  height: 100%; /* 全高 */
  position: fixed; /* 使它产生粘性，即使在滚动时 */
  overflow: auto; /* 如果侧栏的内容太多，则启用滚动条 */}
```

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231210174637902.png" alt="image-20231210174637902" style="zoom: 67%;" />

---

---

---

## 水平导航栏

​	有两种创建水平导航栏的方法：使用*行内*或*浮动*列表项（inline或float）

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231210174821278.png" alt="image-20231210174821278" style="zoom:67%;" />

---

### 粘性导航栏

​		为 `<ul>` 添加 `position: sticky;`，以创建粘性导航栏

---

---

----

## 下拉菜单

​	创建可悬停的下拉列表

### 	  HTML

​		使用任何元素打开下拉菜单内容，例如 `<span>` 或 `<button>` 元素。

​		使用容器元素（如 `<div>`）创建下拉内容，并在其中添加任何内容。

​		用 `<div>` 元素包围这些元素，使用 CSS 正确定位下拉内容

---

### 	CSS

​		`.dropdown` 类使用 `position:relative`，当我们希望将下拉内容放置在下拉按钮的正下方（使用 `position:absolute`）时，需		要使用该类

​		提示：如果您希望下拉内容的宽度与下拉按钮的宽度一样，请将宽度设置为 100％（设置 `overflow:auto` 可实现在小屏幕上滚动

​		我们用了 CSS `box-shadow` 属性，而不是边框，这样下拉菜单看起来像一张“卡片”

​		`box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);`

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231211173409193.png" alt="image-20231211173409193" style="zoom:50%;" />

---

### 	右对齐的下拉菜单内容

```css
.dropdown-content {
  right: 0;}
```

---

### 	下拉式图像

```html
<div class="dropdown">
  <img src="/i/photo/coffee.jpg" alt="Coffee" width="100">
  <div class="dropdown-content">
  <img src="/i/photo/coffee.jpg" alt="Coffee" width="300" height="200">
  <div class="desc">Coffee</div>
  </div>
</div>
```
<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231211173754996.png" alt="image-20231211173754996" style="zoom:50%;" />

---

### 	下拉式导航

```html
	<ul>
	  <li><a href="#home">Home</a></li>
  <li><a href="#news">News</a></li>
  <li class="dropdown">
    <a href="javascript:void(0)" class="dropbtn">Dropdown</a>
    <div class="dropdown-content">
      <a href="#">Link 1</a>
      <a href="#">Link 2</a>
      <a href="#">Link 3</a>
    </div>
  </li>
</ul>
```
<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231211174259154.png" alt="image-20231211174259154" style="zoom:50%;" />

---

---

---

## 图片库

​	一堆图片排列

---

---

---

## 图像精灵

​	图像精灵是单个图像中包含的图像集合。

​	包含许多图像的网页可能需要很长时间才能加载，同时会生成多个服务器请求。

​	使用图像精灵将**减少服务器请求的数量并节约带宽**

​	通过使用 CSS，我们可以仅显示所需图像的某个部分

```css
#home {
  width: 46px;
  height: 44px;
  background: url(navsprites.gif) 0 0;}
```

---

### 	创建导航列表

​		创建表单类的导航：

```html
	<ul id="navlist">
	  <li id="home"><a href="/css/index.asp"></a></li>
```

​		css中用图像精灵设置背景：

```css
#home {
  left: 0px;
  width: 43px;
  background: url('/i/css/navsprites.gif') 0 0;}
```
---

### 	悬停效果

```css
#home a:hover {
  background: url('navsprites_hover.gif') 0 -45px;}
```

---

---

---

## 属性选择器

​	为带有特定属性的 HTML 元素设置样式

### 	   [attribute] 选择器

```css
a[target] {
  background-color: yellow;}
```

​		注释：带有 target 属性的链接获得颜色背景

---

### 	  [attribute="value"] 选择器

```css
a[target="_blank"] { 
  background-color: yellow;}
```

---

### 	   [attribute~="value"] 选择器

​		选取属性值包含指定词的元素，其他同上

---

### 	  [attribute|="value"] 选择器

​		选取指定属性以**<u>指定值开头</u>**的元素

​		**注释：**值必须是完整或单独的单词

---

### 	  [attribute^="value"] 选择器

​		作用同上

​		**提示：**值不必是完整单词！

---

### 	  [attribute$="value"] 选择器

​		选取指定属性以指定值结尾的元素

​		**提示：**值不必是完整单词！

---

### 	  [attribute*="value"] 选择器

​		选取属性值包含指定词的元素

​		**提示：**值不必是完整单词！

---

### 	  设置表单样式

​		若需为不带 class 或 id 的表单设置样式，属性选择器会很有用

```css
input[type="text"]
```

---

---

---

## 表单

### 	设置输入字段的样式

​		使用 `width` 属性来确定输入字段的宽度

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231211180419206.png" alt="image-20231211180419206" style="zoom:50%;" />

---

### 	填充输入框

​		使用 `padding` 属性在文本字段内添加空间。

​		**提示：**若有很多输入，那么您可能还需要添加外边距，以便在它们之外添				 	加更多空间

---

### 	带边框的输入框

​		请使用 `border` 属性更改边框的粗细和颜色(下边框好看)

---

### 	彩色的输入框

​		请使用 `background-color` 属性为输入添加背景色(记得修改文字颜色)

---

### 	获得焦点的输入框

​	    默认情况下，某些浏览器在获得焦点（单击）时会在输入框周围添加蓝色轮廓

```css
input[type=text]:focus {
  background-color: lightblue;
  border: 3px solid #555;/*边框焦点*/}
```

---

### 	带有图标/图像的输入框

​		如果希望在输入框中包含图标，请使用 `background-image` 属性，并将其与 		`background-position` 属性一起设置，留出图片位置

```css
input[type=text] {
  background-image: url('searchicon.png');
  padding-left: 40px;}
```

---

### 	带动画效果的搜索输入框

```css
input[type=text] {
  transition: width 0.4s ease-in-out;}
input[type=text]:focus {
  width: 100%;}
```

​		注释：记得先设置宽度width

---

### 	设置文本域的样式

​		**提示：**使用 `resize` 属性可防止对 textareas 调整大小(禁用右下角的“抓取器”)

---

### 	设置选择菜单的样式

```css
select {
  width: 100%;
  padding: 16px 20px;
  border: none;
  border-radius: 4px;
  background-color: #f1f1f1;}
```
---

---

---

## 计数器

### 	带计数器的自动编号

- `counter-reset` - 创建或重置计数器
- `counter-increment` - 递增计数器值
- `content` - 插入生成的内容
- `counter()` 或 `counters()` 函数 - 将计数器的值添加到元素

```css
body {
  counter-reset: section;}
h2::before {
  counter-increment: section;
  content: "Section " counter(section) ": ";}
```

---

### 	嵌套计数器

​		为页面（section）创建一个计数器，为每个 <h1> 元素（subsection）创建一		个计数器

```css
h1 {
  counter-reset: subsection;}
```

---

---

---

## 网站布局

​	通常分为页眉、菜单、内容和页脚

### 	页眉

​		页眉（header）通常位于网站顶部（或顶部导航菜单的正下方）。它通常包含		徽标（logo）或网站名称

---

### 	导航栏

---

### 	内容

​		使用哪种布局通常取决于您的目标用户。最常见的布局是以下布局之一（或将		它们组合在一起）：

- *1-列*布局（通常用于移动浏览器）
- *2-列*布局（通常用于平板电脑和笔记本电脑）
- *3-列*布局 （仅用于台式机）

---

### 	不相等的栏

​		主要内容（main content）是您网站上最大、最重要的部分

​		可以随意更改宽度，只要记住它的总和应为 100％

---

### 	页脚

​		页脚位于页面底部。它通常包含诸如版权和联系方式之类的信息

---

---

---

## 单位

### 	绝对长度

 		绝对长度单位是固定的，用任何一个绝对长度表示的长度都将恰好显示为这个		尺寸(如果已知输出介质，则可以使用它们)

---

### 	相对长度

​		相对长度单位规定相对于另一个长度属性的长度

| 单位 | 描述                                                         |
| :--- | :----------------------------------------------------------- |
| em   | 相对于元素的字体大小（font-size）（2em 表示当前字体大小的 2 倍） |
| ex   | 相对于当前字体的 x-height(极少使用)                          |
| ch   | 相对于 "0"（零）的宽度                                       |
| rem  | 相对于根元素的字体大小（font-size）                          |
| vw   | 相对于视口*宽度的 1%                                         |
| vh   | 相对于视口*高度的 1%                                         |
| vmin | 相对于视口*较小尺寸的 1％                                    |
| vmax | 相对于视口*较大尺寸的 1％                                    |
| %    | 相对于父元素                                                 |

​		**提示：**em 和 rem 单元可用于创建完美的可扩展布局！

​		视口(Viewport)= 浏览器窗口的尺寸.如果视口为 50 厘米宽，则 1vw = 0.5 厘米

---

---

---

## 特异性

### 	什么是特异性？

​	将特异性(specificity)视为得分/等级,能够确定最终将哪些样式声明应用于元素。

​	通用选择器（*）具有较低的特异性，而 ID 选择器具有较高的特异性！

---

### 	计算特异性？

​		从 0 开始，为 style 属性添加 1000，为每个 ID 添加 100，为每个属性、类或		伪类添加 10，为每个元素名称或伪元素添加 1

---

### 	特异性规则 

1. 在特异性相同的情况下：最新的规则很重要
2. *ID 选择器比属性选择器拥有更高的特异性*
3. *上下文选择器比单一元素选择器更具体*
4. *类选择器会击败任意数量的元素选择器*

---

---

---

# CSS高级教程

## 	圆角

​		`border-radius` 属性，可以实现任何元素的“圆角”样式

```css
border-radius: 25px;
```

​		**提示：**`border-radius` 属性实际上是以下属性的简写属性:(可分别设置)

- `border-top-left-radius`
- `border-top-right-radius`
- `border-bottom-right-radius`
- `border-bottom-left-radius`

​		`border-radius: 50px / 15px;`	//椭圆边框

---

---

---

## 边框图像

​	`border-image` 属性，可以设置图像用作围绕元素的边框

​	允许您指定要使用的图像，而不是包围普通边框(记得设置border)

- 用作边框的图像
- 在哪里裁切图像
- 定义中间部分应重复还是拉伸

​	注释：接受图像，并将其切成九部分

​	`border-image: url(border.png) 30 stretch;`

​	`strech 或者 round 或者 repeat`//strech拉伸,round普通圆角,repeat重复

​	注释：`30`是slice(剪切值)

​	提示：border-image是以下属性的简写

- `border-image-source`
- `border-image-slice`
- `border-image-width`
- `border-image-outset`
- `border-image-repeat`

---

---

---

## 多重背景

​	`background-image` 属性为一个元素添加多幅背景图像

​	不同的背景图像用逗号隔开,且图像会彼此堆叠,其中的第一幅图像最靠近观看者

```css
  background-image: url(flower.gif), url(paper.gif);
  background-position: right bottom, left top;
  background-repeat: no-repeat, repeat;
```

---

### 	背景尺寸

​		`background-size` 属性允许您指定背景图像的大小

​		通过长度,百分比或使用以下两个关键字(contain,cover)来指定背景图像的大小

#### 		contain` 和 `cover

- ​			`contain` 关键字将让图片完整放在区域中

- ​			`cover` 关键字会让区域完全被背景覆盖


#### 		定义多个背景图像尺寸

​			用逗号分隔

---

### 	全尺寸背景图像

- 用图像填充整个页面（无空白）
- 根据需要缩放图像
- 在页面上居中图像
- 不引发滚动条

```css
html {
  background: url(img_man.jpg) no-repeat center fixed; 
  background-size: cover;}
```

---

### 	Hero Image

​		您还可以在 `<div>` 上使用不同的背景属性来创建 Hero Image（带有文本的大		图像）

---

### 	background-origin 属性

​		指定背景图像的位置

- border-box - 背景图片从边框的左上角开始
- padding-box -背景图像从内边距边缘的左上角开始（默认）
- content-box - 背景图片从内容的左上角开始

---

### 	background-clip 属性

​		属性指定背景的**绘制区域**

​		可用值同上

---

---

---

## 渐变

- *线性渐变*（向下/向上/向左/向右/对角线）
- *径向渐变*（由其中心定义）

### 	 线性渐变

​		创建线性渐变，必须定义至少两个色标

​		色标是要呈现平滑过渡的颜色.可以设置起点和方向(或角度)以及渐变效果。

​		background-image: linear-gradient(direction, color-stop1, color-stop2, ...);

- `background-image: linear-gradient(red, yellow);`从上到下(fault)
- `background-image:linear-gradient(to right,red,yellow);`(左右)
- `background-image:linear-gradient(to bottom right,red,yellow);`(对角线)

### 	使用角度

​			如果希望对渐变角度做更多的控制，您可以定义一个角度，来取代预定义的			方向（向下、向上、向右、向左、向右下等等）。值 0deg 等于向上（to 			top）。值 90deg 等于向右（to right）。值 180deg 等于向下（to bottom）

​			background-image: linear-gradient(angle, color-stop1, color-stop2);

---

### 	使用多个色标

​		 background-image: linear-gradient(red, yellow, green);

---

### 	使用透明度

​		 `background-image: linear-gradient(to right, rgba(255,0,0,0),gba(255,0,0,1));`

---

### 	重复线性渐变

```css
repeating-linear-gradient()
background-image: repeating-linear-gradient(red, yellow 10%, green 20%);
```

​		注释：百分比表示颜色占比

---

---

---

## 径向渐变

​	background-image: radial-gradient(shape size at position, start-color, ..., last-color);

​	默认：shape为椭圆，size为最远角，position为中心

​	size参数使用关键字

- *closest-side*
- *farthest-side*
- *closest-corner*
- *farthest-corner*

---

### 	重复径向渐变

```css
repeating-radial-gradient()
```

---

---

---

## 阴影效果

​	多个阴影`text-shadow: 0 0 3px #FF0000, 0 0 5px #0000FF;`

---

---

---

## Box Shadow

### 	应用阴影于元素	

​		box-shadow: 10px 10px 5px grey;

​		注释：10px(水平垂直)，5px(模糊)，grey(颜色)

---

### 	卡片

```css
div.polaroid {
  width: 250px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0   rgba(0, 0, 0, 0.8);
  text-align: center;}
```
---

---

---

## 文本效果

### 		文字溢出

​		 `text-overflow` 属性规定应如何向用户呈现未显示的溢出内容

- `clip`剪裁
- `ellipsis`省略号

​		鼠标悬停时显示

```css
div.test:hover {
  overflow: visible;}
```

---

###  	字换行

​		`word-wrap` 属性使长文字能够被折断并换到下一行

​		`word-wrap: break-word;`

---

### 	换行规则

​		`word-break` 属性指定换行规则

- `word-break:keep-all`打断连字符
- `word-break:break-all`任何处打断

---

### 	书写模式

​		`writing-mode` 属性规定文本行是水平放置还是垂直放置

- `horizontal-tb`横向
- `vertical-rl`纵向

---

---

---

## Web 字体

### 	常见字体

- ​		TrueType 字体 (TTF)

- ​		OpenType 字体 (OTF)

- ​		Web 开放字体格式 (WOFF)

- ​		Web 开放字体格式 (WOFF 2.0)

- ​		SVG 字体/形状

- ​		嵌入式 OpenType 字体 (EOT)


---

### 	自选字体

```css
@font-face{ 
font-family: myFirstFont;
    src: url(sansation_light.woff);}
```

---

---

---

## 2D 转换

​	`transform`允许您移动、旋转、缩放和倾斜元素

- `transform: translate(50px,100px);`右移动50像素,下移动100像素
- `transform:rotate(20deg);`顺时针旋转20度(逆时针是负的)
- `transform:scaleX(2);`增大为原始两倍宽度
- `scaleY()`两倍高度
- `transform:scale(2,3);`增大为原始的二倍宽度和三倍高度
- `skewX()`延X轴倾斜20度
- `skewY()`延y轴
- `skew()`
- `matrix(scaleX(),skewY(),skewX(),scaleY(),translateX(),translateY())`可接受六个参数，其中包括数学函数

---

---

---

## 3D 转换

- `rotateX()`
- `rotateY()`
- `rotateZ()`//z轴垂直于屏幕向里

---

---

---

## 过渡

​	允许您在给定的时间内平滑地改变属性值

### 	必须明确两件事：

- 您要添加效果的 CSS 属性
- 效果的持续时间

### 	transition

```css
div {
  width: 100px;
  height: 100px;
  background: red;
  transition: width 2s;}
div:hover {
  width: 300px;}
```

​		提示：当光标从元素上移开时，它将逐渐变回其原始样式

#### 		改变若干属性值

​		`transition: width 2s, height 4s;`

---

### 	指定过渡的速度曲线

​		`transition-timing-function` 属性规定过渡效果的速度曲线

- `ease` - 规定过渡效果，先缓慢地开始，然后加速，然后缓慢地结束（默认）
- `linear` - 规定从开始到结束具有相同速度的过渡效果
- `ease-in` -规定缓慢开始的过渡效果
- `ease-out` - 规定缓慢结束的过渡效果
- `ease-in-out` - 规定开始和结束较慢的过渡效果
- `cubic-bezier(n,n,n,n)` - 允许您在三次贝塞尔函数中定义自己的值

---

### 	延迟过渡效果

​		`transition-delay` 属性规定过渡效果的延迟（以秒计）

```css
  transition-delay: 1s;
```

---

### 	  过渡 + 转换

​		 `transition: width 2s, height 2s, transform 2s;`

---

---

---

## 动画

### 	什么是 CSS 动画？

- 动画使元素逐渐从一种样式变为另一种样式。

- 您可以随意更改任意数量的 CSS 属性

- 如需使用 CSS 动画，您必须首先为动画指定一些关键帧。

- 关键帧包含元素在特定时间所拥有的样式


---

### 	@keyframes 规则

​		如果您在 `@keyframes` 规则中指定了 CSS 样式，动画将在特定时间逐渐从当前		样式更改为新样式

```css
@keyframes example {
  from {background-color: red;}
  to {background-color: yellow;}}
div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 4s;}
```

​		可以使用百分比值。通过使用百分比，您可以根据需要添加任意多个样式更改

```css
0%   {background-color:red; left:0px; top:0px;}
  25%  {background-color:yellow; left:200px; top:0px;}
  50%  {background-color:blue; left:200px; top:200px;}
  75%  {background-color:green; left:0px; top:200px;}
  100% {background-color:red; left:0px; top:0px;}
```

---

### 	延迟动画

​		`animation-delay` 属性规定动画开始的延迟时间

```css
animation-delay: 2s;
```

​		负值也是允许的。如果使用负值，则动画将开始播放，如同已播放 N 秒

---

### 	设置动画应运行多少次

​		`animation-iteration-count` 属性指定动画应运行的次数

​		`animation-iteration-count: 3;`停止前运行三次

​		` animation-iteration-count: infinite;`永远持续

---

### 	反向或交替运行动画

​		`animation-direction` 属性指定是向前播放、向后播放还是交替播放动画

- `normal` - 动画正常播放（向前）。默认值
- `reverse` - 动画以反方向播放（向后）
- `alternate` - 动画先向前播放，然后向后
- `alternate-reverse` - 动画先向后播放，然后向前

---

### 	指定动画的填充模式

​		CSS 动画不会在第一个关键帧播放之前或在最后一个关键帧播放之后影响元素

​		`animation-fill-mode` 属性能够覆盖这种行为

- `none` - 默认值。动画在执行之前或之后不会对元素应用任何样式。
- `forwards` - 元素将保留由最后一个关键帧设置的样式值（依赖 animation-direction 和 animation-iteration-count）。
- `backwards` - 元素将获取由第一个关键帧设置的样式值（取决于 animation-direction），并在动画延迟期间保留该值。
- `both` - 动画会同时遵循向前和向后的规则，从而在两个方向上扩展动画属性。

---

### 	指定动画的速度曲线

`animation-timing-function` 属性规定动画的速度曲线。

`animation-timing-function` 属性可接受以下值：

- `ease` - 指定从慢速开始，然后加快，然后缓慢结束的动画（默认）
- `linear` - 规定从开始到结束的速度相同的动画
- `ease-in` - 规定慢速开始的动画
- `ease-out` - 规定慢速结束的动画
- `ease-in-out` - 指定开始和结束较慢的动画
- `cubic-bezier(*n*,*n*,*n*,*n*)` - 运行您在三次贝塞尔函数中定义自己的值

---

---

---

## 工具提示

```css
.tooltip .tooltiptext {
  width: 120px;
  bottom: 100%;
  left: 50%; 
  margin-left: -60px; /* Use half of the width (120/2 = 60), to center the tooltip */}
```

---

---

---

## object-fit 属性

​	规定应如何调整 `<img> 或 <video>` 的大小来适应其容器

​	 `object-fit: cover;`

- `fill` - 默认值。调整替换后的内容大小，以填充元素的内容框。如有必要，将拉伸或挤压物体以适应该对象。
- `contain` - 缩放替换后的内容以保持其纵横比，同时将其放入元素的内容框。
- `cover` - 调整替换内容的大小，以在填充元素的整个内容框时保持其长宽比。该对象将被裁剪以适应。
- `none` - 不对替换的内容调整大小。
- `scale-down` - 调整内容大小就像没有指定内容或包含内容一样（将导致较小的具体对象尺寸）

---

---

---

## 按钮

```html
<button>默认按钮</button>
<a href="#" class="button">链接按钮</a>
<button class="button">按钮</button>
<input type="button" class="button" value="输入按钮">
```
​		三种按钮`<button>`自定义化最高

## 	可悬停按钮

```css
.button {
  transition-duration: 0.4s;}
.button:hover {
  background-color: #4CAF50; /* Green */
  color: white;}
```

---

### 	阴影按钮

```css
.button1 {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);}
.button2:hover {
  box-shadow: 0 12px 16px 0 rgba(0,0,0,0.24), 0 17px 50px 0 rgba(0,0,0,0.19);}
```

---

-  `cursor: not-allowed;`禁用的按钮
-  `float:left`水平按钮分组
-  `display:block`垂直按钮组

---

---

---

## 分页实例

### 		简单的分页

```css
.pagination {
  display: inline-block;}
.pagination a {
  color: black;
  float: left;
  padding: 8px 16px;
  text-decoration: none;}
<div class="pagination">
  <a href="#">«</a>
  <a href="#">1</a>
  <a href="#">»</a>
</div>
```

---

### 	活动的可悬停分页

​		用 `.active` 类突出显示当前页面，并在鼠标移到它们上方时使用 `:hover` 选		择器更改每个页面链接的颜色

```css
.pagination a.active {
  background-color: #4CAF50;
  color: white;}
.pagination a:hover:not(.active) {background-color: #ddd;}
```

---

- `transition: background-color .3s;`过渡效果
-  `border: 1px solid #ddd; /* Gray */`带边框的分页
- `margin: 0 4px;`链接之间的空间
- `text-align: center;`居中

---

### 	面包屑分页

```css
<ul class="breadcrumb">
  <li><a href="#">Home</a></li>
  <li><a href="#">Pictures</a></li>
  <li><a href="#">Summer 15</a></li>
  <li>Italy</li>
</ul>
```
---

---

---

## 多列

- `column-count`创建
- `column-gap`间隙
- `column-rule-style`列之间样式
- `column-rule-width`列之间宽度
- `column-rule-color`列之间颜色
- `column-width`指定列宽度(最佳100px)

---

---

---

## 用户界面

### 	调整大小

​		`resize` 属性规定元素是否应（以及如何）被用户调整大小

- `realize:horizonal;`只能调整宽度
- `realize:vertical;`只能调整高度
- `realize:both`都可以调整

---

### 	轮廓偏移

​		`outline-offset` 属性在轮廓与元素的边缘边框之间添加空间

```css
outline-offset: 15px;
outline: 4px solid red;
```

![image-20231212131804237](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231212131804237.png)

---

---

---

## 变量

### 	变量

- `var()` 函数用于插入 CSS 变量的值
- 变量可以访问 DOM

- 可以创建具有局部或全局范围的变量，使用 JavaScript 来修改变量，以及基于媒体查询来修改变量


---

### 	var() 函数的语法

​		var() 函数用于插入 CSS 变量的值。

```
var(name, value)
```

- `name`必须，变量名(以两条破折号开头,区分大小写！！！)
- `value`可选，回退值(未找到变量时使用)

---

### 	var() 如何工作

​		首先：CSS 变量可以有全局或局部作用域。

​		全局变量可以在整个文档中进行访问/使用，而局部变量只能在声明它的选择		器内部使用

- `:root`声明<u>全局变量</u>(选择器匹配文档的根元素)
- <u>局部变量</u>所使用的选择器中声明

```css
:root {
  --blue: #1e90ff;
  --white: #ffffff;}
h2 { border-bottom: 2px solid var(--blue); }
```

---

### 	var() 优势：

- 使代码更易于阅读（更容易理解）
- 使修改颜色值更加容易

---

---

---

## 覆盖变量

​	用局部变量覆盖全局变量

```css
:root {
  --blue: #1e90ff;
  --white: #ffffff;}
button {
  --blue: #0000ff;}
```

​		注释：button中的--blue覆盖root中的

---

### 	添加一个新的局部变量

​		如果只在一个地方使用一个变量，我们也可以声明一个新的局部变量

```css
button {
  --button-blue: #0000ff;}
```

---

---

---

## JavaScript 更改变量

```css
<script>// 获取根元素
var r = document.querySelector(':root');
function myFunction_get() {
  var rs = getComputedStyle(r);
  alert("The value of --blue is: " +     			     rs.getPropertyValue('--blue'));}
function myFunction_set() {
  r.style.setProperty('--blue', 'lightblue');}
</script>
```

---

---

---

## 媒体查询中使用变量

​	媒体查询旨在为不同的设备（显示器、平板电脑、手机等）定义不同的样式规则

```css
@media screen and (min-width: 450px) {
  .container {
    --fontsize: 50px;}}
.container {
  font-size: var(--fontsize);}
.container {
  --fontsize: 25px;}
```

​		注释：当浏览器宽度大于450px时，将fontsize原来的25px改为50px

---

---

---

## Box Sizing

​	`box-sizing` 属性允许在元素的总宽度和高度中包括内边距（填充）和边框

​	默认情况下，元素的宽度和高度是这样计算的：

- width + padding + border = 元素的实际宽度
- height + padding + border = 元素的实际高度

​	注释：当width和height相等时,用了`box-sizeing`只要padding或margin小于				 width和height，元素总尺寸还是不变

---

---

---

## Flexbox

### 	lexbox 布局模块

​		在 Flexbox 布局模块（问世）之前，可用的布局模式有以下四种：

- 块（Block），用于网页中的部分（节）
- 行内（Inline），用于文本
- 表，用于二维表数据
- 定位，用于元素的明确位置

​		弹性框布局模块，可以更轻松地设计灵活的响应式布局结构，而无需使用浮动		或定位

---

### 	父元素（容器）

​		通过将 `display` 属性设置为 `flex`，flex 容器将可伸缩

1. `flex-direction:column;`垂直堆叠
2. `flex-direction:column-reverse;`从下到上垂直堆叠
3. `flex-direction:row;`从左到右水平
4. `flex-direction:row-reverse;`从右到左水平
5. `flex-wrap:wrap;`必要时换行
6. `flex-wrap:nowrap;`不换行
7. `flex-flow:row wrap;`同时设置
8. `justify-content:center;`中心对齐
9. `justify-content:flex-start;`开头对齐
10. `justify-content:flex-end;`末端对齐
11. `justify-content:space-around;`行之前之间之后带有空格
12. `justify-content:between;`行之间有空格
13. `align-items:center;`中间对齐
14. `align-items:flex-start;`顶部对齐
15. `align-items:flex-end;`底部对齐
16. `align-items:strech;`拉伸以填充容器
17. `align-items:baseline;`基线对齐
18. `align-content:space-between;`线之间有相等间距
19. `align-content:space-around;`线之前之中之后有空格
20. `align-content:strech;`拉伸占据剩余空间
21. `align-content:center;`容器中间显示线
22. `align-content:flex-start;`开头显示线
23. `align-content:flex-end;`末尾显示线

---

### 	子元素（项目）

​		flex 容器的直接子元素会自动成为弹性（flex）项目

用于弹性项目的属性有：`<div style="关键字">数字</div>`

1. `order`规定项目顺序(必须是数字，默认0)
2. `flex-grow`规定某个项目相对于其余项目增长多少(同上)
3. `flex-shrink`规定收缩(同上)
4. `flex-basis`规定初始长度
5. `flex`grow，shrink，basis的简写
6. `align-self`规定对齐方式(center,flex-start,flex-end……)

---

---

---

## 媒体查询

### 	媒体查询可用于检查：

- 视口的宽度和高度
- 设备的宽度和高度
- 方向（平板电脑/手机处于横向还是纵向模式）
- 分辨率

---

### 	语法

```css
@media not|only mediatype and (expressions) {
  CSS-Code;}
```

​		您还可以针对不同的媒体使用不同的样式表：

```html
<link rel="stylesheet" media="mediatype and|not|only (expressions)" href="print.css">
```

---

### 	媒体类型

|   值   | 描述                                     |
| :----: | :--------------------------------------- |
|  all   | 用于所有媒体类型设备。                   |
| print  | 用于打印机。                             |
| screen | 用于计算机屏幕、平板电脑、智能手机等等。 |
| speech | 用于大声“读出”页面的屏幕阅读器。         |

---

### 	示例

```css
@media screen and (min-width: 480px) {
  body {
    background-color: lightgreen;}
}
```

​		注释：视口宽度为480px或更宽时背景颜色改为浅绿色

```css
@media screen and (min-width: 480px) {
  #leftsidebar {width: 200px; float: left;}
  #main {margin-left: 216px;}
}
```

​		注释：视口宽度为480px或更宽，菜单会浮动到页面左侧

---

---

---

# CSS响应式设计

## 视口	

### 	什么是视口？

​		视口（viewport）是用户在网页上的可见区域。

​		视口随设备而异，在移动电话上会比在计算机屏幕上更小

---

### 	设置视口

​		通过 `<meta>` 标签来控制视口

```css
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

​		`width=device-width` 部分将页面的宽度设置为跟随设备的屏幕宽度

​		`initial-scale=1.0` 部分设置初始缩放级别

---

---

---

## 网格视图

### 	什么是网格视图？

​		许多网页都基于网格视图（grid-view），这意味着页面被分割为几列

---

### 	构建响应式网格视图

1. 确保所有 HTML 元素的 `box-sizing` 属性设置为 `border-box`

```css
* {
  box-sizing: border-box;}
```

​			2.为 12 列中的每一列创建一个类，即 `class="col-"` 和一个数字，该数字				定义此节应跨越的列数

```css
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
```

​			3.清除流的样式

```css
.row::after {
  content: "";
  clear: both;
  display: table;}
```

​			4.添加一些样式和颜色，使更美观

---

---

---

## 媒体查询

### 	典型的设备断点

```css
/* 超小型设备（电话，600px 及以下） */
@media only screen and (max-width: 600px) {...} 
/* 小型设备（纵向平板电脑和大型手机，600 像素及以上） */
@media only screen and (min-width: 600px) {...} 
/* 中型设备（横向平板电脑，768 像素及以上） */
@media only screen and (min-width: 768px) {...} 
/* 大型设备（笔记本电脑/台式机，992px 及以上） */
@media only screen and (min-width: 992px) {...} 
/* 超大型设备（大型笔记本电脑和台式机，1200px 及以上） */
@media only screen and (min-width: 1200px) {...}
```

---

---

---

## 图像(同视频)

### 	width 属性

​		设置为百分比，且高度设置为 "auto"，则图像将进行响应来放大或缩小

### 	max-width 属性

​		设置为 100％，则图像将按需缩小，但绝不会放大到大于其原始大小

### 	背景图像

- `background-size` 属性设置为 "contain"，则背景图像将缩放，并尝试匹配内容区域
- `background-size` 属性设置为 "100% 100%"，则背景图像将拉伸以覆盖整个内容区域
- `background-size` 属性设置为 "cover"，则背景图像将缩放以覆盖整个内容区域

---

### 	 `<picture>` 元素

```css
<picture>
  <source srcset="img_smallflower.jpg" media="(max-width: 400px)">
  <source srcset="img_flowers.jpg">
  <img src="img_flowers.jpg" alt="Flowers">
</picture>
```

​		注意：`srcset` 属性是必需的，它定义图像的来源.`media` 属性是可选的

---

---

---

# 网格教程

### 	Display 属性

​		当 HTML 元素的 `display` 属性设置为 `grid` 或 `inline-grid` 时，它就会成为		网格容器

---

- 网格列(grid colunms)
- 网格行(grid rows)
- 网格间隙(grid gaps)
- 网格线(grid lines)

---

### 	调整间隙大小：

- `grid-column-gap`单位px
- `grid-row-gap`
- `grid-gap`

---

---

---

## 	grid-template-columns 属性

​		定义网格布局中的列数，并可定义每列的宽度

​		以空格分隔的列表，其中每个值定义相应列的长度

```css
grid-template-columns: auto auto auto auto;
```

---

### 	grid-template-rows 属性

- 定义每列的高度
- 以空格分隔的列表，其中每个值定义相应行的高度

​		`grid-template-rows: 80px 200px;`

---

### 	justify-content 属性

​		在容器内对齐整个网格

1. ` justify-content: space-evenly;`
2. `justify-content: space-around;`
3. `justify-content: space-between;`
4. ` justify-content: center;`
5. `justify-content: start;`
6. `justify-content: end;`

---

### 	align-content 属性

​		用于垂直对齐容器内的整个网格

1. `center`
2. `space-evenly`
3. `space-around`
4. `space-between`
5. `start`
6. `end`

---

---

---

## 网格项目

### 	子元素（项目）

​		网格容器包含网格项目

---

### 	grid-column 属性：

​		定义将项目放置在哪一列上

```css
 grid-column: 1 / 5;
```

​		注释：从第一列开始并在第五列之前结束

---

### 	grid-row 属性

​		定义了将项目放置在哪一行

```css
grid-row: 1 / 4;
```

​		注释：第一行开始，第四行结束

---

### 	grid-area 属性

​		`grid-area` 属性可以用作 grid-row-start、grid-column-start、grid-row-			end 和 grid-column-end 属性的简写属性

---

### 	命名网格项

​		`grid-area` 属性也可以用于为网格项目分配名称

​		可以通过网格容器的 `grid-template-areas` 属性来引用命名的网格项目

```
.item1 {
  grid-area: myArea;
}
.grid-container {
  grid-template-areas: 'myArea myArea myArea myArea myArea';
}
```

---

### 	项目的顺序

​		网格布局允许我们将项目放置在我们喜欢的任意位置

```css
.item1 { grid-area: 1 / 3 / 2 / 4; }
```

---

---

---

