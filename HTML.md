[[HTML pro]]
## <u>JavaScript</u>

**<u>设置button</u>**

​	`<button type=""onclick=""></button>`

​	e.g  获取时间		``onclick="document.getElementById('demo').innerHTML=Date()"`

​	`<p id="demo"></p>`**注意添加id**

​	**button内添加文字显示在button内**

------------------------------------------

### <u>**更改样式**</u>

<script>
    function myFunction(){
        document.getElementById("demo").style.fontSize="25px"
        document.getElementById("demo").style.color = "red";
        document.getElementById("demo").style.backgroundColor = "yellow";   
    }
</script>

---

### **<u>更改图像属性</u>**

<script>
    function light(sw) {
  var pic;
  if (sw == 0) {
    pic = "/i/eg_bulboff.gif"
  } else {
    pic = "/i/eg_bulbon.gif"
  }
  document.getElementById('myImage').src = pic;
}
</script>
    <img id="myImage" src="/i/eg_bulboff.gif" width="109" 
         height="180">
<p>
<button type="button" onclick="light(1)">开灯</button>
<button type="button" onclick="light(0)">关灯</button>
</p>

---

### **<u>noscript标签</u>**

`<noscript>抱歉浏览器不支持Javascript</noscript>`

---

----

----

---

## <u>HTML文件路径</u>

### 绝对文件路径

​		指向一个因特网的完整URL

​		e.g 	`<img src="https://www.w3school.com.cn/images/picture.jpg" alt="flower">`

### 相对路径

​		指向相对于当前页面的文件

​		e.g	`<img src="/images/picture.jpg" alt="flower">`

​				当前文件夹中 images 文件夹里的一个文件

​		e.g `<img src="images/picture.jpg" alt="flower">`

​				于当前文件夹的上一级文件夹中 images 文件夹里的一个文件

​		<u>注意“/”</u>

**注意**：使用相对路径是个好习惯（如果可能）。

如果使用了相对路径，那么您的网页就不会与当前的基准 URL 进行绑定。所有链接在您的电脑上 (localhost) 或未来的公共域中均可正常工作

---

---

---

---

## <u>HTML头部元素</u>

### `<head>`

​		是所有头部元素的容器

​		可包含脚本，指示浏览器在何处可以找到样式表，提供元信息

​		以下标签都可以添加到 head 部分：

### `<title>`

​		作用：

- 定义浏览器工具栏中的标题
- 提供页面被添加到收藏夹时显示的标题
- 显示在搜索引擎结果中的页面标题

### `<link>`

​		定义文档与外部资源之间的关系，如css

### `<style>`

-----

### `<meta>`

		<meta>(metadata)是关于数据的信息
		</meta>

​		提供HTML的元数据，不显示在页面上，对于机器可读

​		如规定页面描述，关键词，作者，修改时间等

​		<u>记得位于head中</u>

​		e.g `<meta name="description" content="Free Web tutorials on HTML, CSS, XML" />`

​			 `<meta name="keywords" content="HTML, CSS, XML" />`

---

### `<script>`

​		用于定义客户端脚本,如JavaScript

---

---

---

---

---

## **<u>HTML布局</u>**

### `<div>`

​		常用作布局工具，能够轻松地通过 CSS 对其进行定位

---

### HTML5网站布局

| header  | 定义文档或节的页眉             |
| :-----: | ------------------------------ |
|   nav   | 定义导航链接的容器             |
| section | 定义文档中的节                 |
| article | 定义独立的自包含文章           |
|  aside  | 定义内容之外的内容（比如侧栏） |
| footer  | 定义文档或节的页脚             |
| details | 定义额外的细节                 |
| summary | 定义 details 元素的标题        |

---

### `<table>`

​		作用是显示表格化的数据。

​		能够取得布局效果，因为能够通过 CSS 设置表格元素的样式

---

---

---

---

---

## <u>HTML响应式web设计</u>

### **定义**

- RWD 指的是响应式 Web 设计（Responsive Web Design）
- RWD 能够以可变尺寸传递网页
- RWD 对于平板和移动设备是必需的

---

### 	`bootstrap`

​			Bootstrap 是最流行的开发响应式 web 的 HTML, CSS, 和 JS 框架。

​			Bootstrap 帮助开发在任何尺寸都外观出众的站点：显示器、笔记本电脑、平板电脑或手机。

---

---

---

---

## <u>HTML计算机代码元素</u>

### **格式**

​	通常，HTML 使用*可变*的字母尺寸，以及可变的字母间距。

​    在显示*计算机代码*示例时，并不需要如此。

​	*<kbd>*, *<samp>*, 以及 *<code>* 元素全都支持固定的字母尺寸和间距

----

### **键盘格式**

​	`<kbd>`

​		定义键盘输入

​		e.g	`<p><kbd>File | Open...</kbd></p>`

---

### 样本格式

​	`<samp>`

​		定义计算机输出示例

​		e.g ``

```
<samp>
demo.example.com login: Apr 12 09:10:17
Linux 2.6.10-grsec+gg3+e+fhs6b+nfs+gr0501+++p3+c4a+gr2b-reslog-v6.189
</samp>
```

### 代码格式	

​	`	<code>`

​		定义编程代码示例

​		e.g  ``

```
<code>
var person = { firstName:"Bill", lastName:"Gates", age:50, eyeColor:"blue" }
</code>
```

​		<u>不保留多余的空格和折行</u>

​		可使用`<pre>`解决

### 	 HTML变量格式化

​		定义数学变量

​		e.g  

```
<p>Einstein wrote:</p>

<p><var>E = m c<sup>2</sup></var></p>
```

---

---

---

## <u>HTML5语义元素</u>

​	**语义学（源自古希腊）可定义为对语言意义的研究。**

​    语义元素是拥有语义的元素

### 	定义

​		 语义元素清楚地向浏览器和开发者描述其意义。

​		 非语义元素的例子：<div> 和 <span> - 无法提供关于其内容的信息。

​         语义元素的例子：<form>、<table> 以及 <img> - 清晰地定义其内容。

-----

### 	HTML5 新的语义元素

- '<article>'
- '<aside>'
- '<details>'
- '<figcaption>'
- '<figure>'
- '<footer>'
- '<header>'
- '<main>'
- '<mark>'
- '<nav>'
- '<section>'
- '<summary>'
- '<time>'

​			![HTML5 语义元素](https://www.w3school.com.cn/i/ct_sem_elements.png)

----

### 	`<section>`

​		定义文档中的节

​		“节（section）是有主题的内容组，通常具有标题

​		可以将网站首页划分为简介、内容、联系信息等节

​		e.g	

```
<section>
   <h1>WWF</h1>
   <p>The World Wide Fund for Nature (WWF) is....</p>
</section>
```

----

### 	`<article>`

​		<article> 元素规定独立的自包含内容。

​		文档有其自身的意义，并且可以独立于网站其他内容进行阅读。

​		<article> 元素的应用场景：

- 论坛
- 博客
- 新闻

---

### 	**嵌套语义元素**

​		在因特网上，会发现 <section> 元素包含 <article> 元素的 HTML 页		   		面，还有 <article> 元素包含 <sections> 元素的页面。

​		还会发现 <section> 元素包含 <section> 元素，同时 <article> 元素		包含 <article> 元素。

----

### 	`<figure>和<figcaption`

​		在书籍和报纸中，与图片搭配的标题很常见。

​		标题（caption）的作用是为图片添加可见的解释。

​		通过 HTML5，图片和标题能够被组合在 *<figure>* 元素中

​		<img> 元素定义图像，<figcaption> 元素定义标题

​		e.g	

```
<figure>
   <img src="pic_mountain.jpg" alt="The Pulpit Rock" width="304" height="228">
   <figcaption>Fig1. - The Pulpit Pock, Norway.</figcaption>
</figure> 
```

-------

---

---

---

---

## <u>HTML5样式指南和代码约定</u>

​	HTML5 在代码验证时会更宽松一点。

​	通过 HTML5，您必须创建属于自己的最佳实践、样式指南和代码约定

​	请始终在文档的首行声明文档类型：

```
<!DOCTYPE html>
```

​	如果一贯坚持小写标签，那么可以使用：

```
<!doctype html>
```

---

### 	使用小写元素名	 

​		HTML5 允许在元素名中使用混合大小写字母。

​			我们推荐使用小写元素名：

- 混合大小写名称并不好
- 开发者习惯使用小写名（比如在 XHTML 中）
- 小写更起来更纯净
- 小写更易书写

---

### 关闭元素

​	在 HTML5 中，您不必关闭所有元素（例如 <p> 元素）

​	在 HTML5 中，关闭空元素是可选的。

​	允许这样：

```
<meta charset="utf-8">
```

​	也允许这样：

```
<meta charset="utf-8" />
```

​	斜杠（/）在 XHTML 和 XML 中是必需的

---

### 使用小写属性名

​	HTML5 允许大小写混合的属性名。

​	我们建议使用小写属性名

---

### 必要属性

​	请始终对图像使用 *alt* 属性。当图像无法显示时该属性很重要

​	请始终定义图像尺寸。这样做会减少闪烁，因为浏览器会在图像加载之前为图像	预留空间

---

### 空格和等号

​	等号两边的空格是合法的，但是精简空格更易阅读

---

### 避免长代码

​	当使用 HTML 编辑器时，通过左右滚动来阅读 HTML 代码很不方便。

​	请尽量避免代码行超过 80 个字符

---

### 空行和缩进

​	为了提高可读性,请增加空行来分隔大型或逻辑代码块

​	为了提高可读性，请增加两个空格的缩进，请勿使用TAB

---

### 省略 <html> 和 <body>？

​	在 HTML5 标准中，能够省略 <html> 标签和 <body> 标签

​	**我们不推荐省略 <html> 和 <body> 标签**

​		对于可访问应用程序（屏幕阅读器）和搜索引擎，声明语言很重要。

​		省略 <html> 或 <body> c可令 DOM 和 XML 软件崩溃。

​		省略 <body> 会在老式浏览器（IE9）中产生错误

---

### 省略 <head>？

​	在 HTML5 标准中，<head> 标签也能够被省略。

​	默认地，浏览器会把 <body> 之前的所有元素添加到默认的 <head> 元素。

​	通过省略 <head> 标签，您能够降低 HTML 的复杂性

​	**注意**：对于 web 开发者，省略标签的做法是陌生的。建立规则需要时间

---

### 元数据

	<title> 元素在 HTML5 中是必需的。请尽可能制作有意义的标题

​		为了确保恰当的解释，以及正确的搜索引擎索引，在文档中对语言和字符编码		的定义越早越好

---

### HTML 注释

​	`<!-- This is a comment -->`

```HTML
<!-- 
  This is a long comment example. This is a long comment example. This is a long comment example.
  This is a long comment example. This is a long comment example. This is a long comment example.
-->
```

​		长注释更易观察，如果它们被缩进两个空格的话

---

### 样式表

- 开括号与选择器位于同一行
- 在开括号之前用一个空格
- 使用两个字符的缩进
- 在每个属性与其值之间使用冒号加一个空格
- 在每个逗号或分号之后使用空格
- 在每个属性值对（包括最后一个）之后使用分号
- 只在值包含空格时使用引号来包围值
- 把闭括号放在新的一行，之前不用空格
- 避免每行超过 80 个字符

**注释：**在逗号或分号之后添加空格，是所有书写类型的通用规则

---

### 在 HTML 中加载 JavaScript

​	请使用简单的语法来加载外部脚本（type 属性不是必需的）：

```html
<script src="myscript.js">
```

---

### 通过 JavaScript 访问 HTML 元素

​	`var obj = getElementById("demo")`

---

### 使用小写文件名

​	大多数 web 服务器（Apache、Unix）对文件名的大小写敏感：

​			不能以 london.jpg 访问 London.jpg

​	其他 web 服务器（微软，IIS）对大小写不敏感：

​			能够以 london.jpg 或 London.jpg 访问 London.jpg

​	如果您从对大小写不敏感的服务器转到一台对大小写敏感的服务器上，这些小错	误将破坏您的网站。

​	为了避免这些问题，请始终使用小写文件名（如果可以的话）

---

### 文件扩展名

​	HTML 文件名应该使用扩展名 *.html*（而不是 .htm）。

​	CSS 文件应该使用扩展名 *.css*。

​	JavaScript 文件应该使用扩展名 *.js*

---

---

---

---

## <u>HTML 字符实体</u>

​	在 HTML 中不能使用小于号（<）和大于号（>），这是因为浏览器会误认为它	们是标签

### 	不间断空格（non-breaking space）

​		`不间断空格(&nbsp;)`

### 	HTML 中有用的字符实体

​	**注释：**实体名称对大小写敏感！

| 显示结果 |        描述         |      实体名称       | 实体编号  |
| :------: | :-----------------: | :-----------------: | :-------: |
|          |        空格         |       &nbsp;        |  &#160;   |
|    <     |       小于号        |       `&lt;`        |  `&#60;`  |
|   `>`    |      `大于号`       |       `&gt;`        |  `&#62;`  |
|   `&`    |       `和号`        |       `&amp;`       |  `&#38;`  |
|   `"`    |       `引号`        |      `&quot;`       |  `&#34;`  |
|   `'`    |       `撇号`        | `&apos; (IE不支持)` |  `&#39;`  |
|   `￠`   |    `分（cent）`     |      `&cent;`       | `&#162;`  |
|   `£`    |    `镑（pound）`    |      `&pound;`      | `&#163;`  |
|   `¥`    |     `元（yen）`     |       `&yen;`       | `&#165;`  |
|   `€`    |   `欧元（euro）`    |      `&euro;`       | `&#8364;` |
|   `§`    |       `小节`        |      `&sect;`       | `&#167;`  |
|   `©`    | `版权（copyright）` |      `&copy;`       | `&#169;`  |
|   `®`    |     `注册商标`      |       `&reg;`       | `&#174;`  |
|   `™`    |       `商标`        |      `&trade;`      | `&#8482;` |
|    ×     |       `乘号`        |      `&times;`      | `&#215;`  |
|   `÷`    |       `除号`        |     `&divide;`      |  &#247;   |

---

----

---

---

## <u>HTML 符号</u>

​	**键盘上不存在的字符也可以由实体代替。**

### 	HTML 符号实体

​		如需将此类符号添加到 HTML 页面，您可以使用 HTML 实体名称（HTML 		entity name）。

​		如果不存在实体名称，则可使用实体编号，十进制或十六进制的引用

### 	HTML 支持的一些数学符号

​		

| 字符 | 数字    | 实体     | 描述                 |
| :--- | :------ | :------- | :------------------- |
| ∀    | &#8704; | &forall; | FOR ALL              |
| ∂    | &#8706; | &part;   | PARTIAL DIFFERENTIAL |
| ∃    | &#8707; | &exist;  | THERE EXISTS         |
| ∅    | &#8709; | &empty;  | EMPTY SETS           |
| ∇    | &#8711; | &nabla;  | NABLA                |
| ∈    | &#8712; | &isin;   | ELEMENT OF           |
| ∉    | &#8713; | &notin;  | NOT AN ELEMENT OF    |
| ∋    | &#8715; | &ni;     | CONTAINS AS MEMBER   |
| ∏    | &#8719; | &prod;   | N-ARY PRODUCT        |
| ∑    | &#8721; | &sum;    | N-ARY SUMMATION      |

---

---

---

---

###  HTML 中使用表情符号

​	表情符号（Emoji）类似图像或图标，但它们并不是。

​	它们是来自 UTF-8 (Unicode) 字符集的字母（字符）。

​	<u>**提示：**UTF-8 几乎涵盖世界上所有字符和符号</u>

---

### 	HTML charset 属性

​		为了正确显示 HTML 页面，Web 浏览器必须知道页面中使用的字符集。

​		这是在 `<meta>` 标签中规定的：

```html
<meta charset="UTF-8">
```

​		<u>**提示：**如果未规定，UTF-8 则是 HTML 中的默认字符集。</u>

---

### 	UTF-8 字符

​		很多 UTF-8 字符无法在键盘上键入，但始终可以使用数字（被称为实体编		号）来显示它们

​		e.g	`<p>我将显示 &#65; &#66; &#67;</p>`

---

### Emoji 字符

​	表情符号也是来自 UTF-8 字母的字符：

- 😄 是 128516

- 😍 是 128525

- 💗 是 128151

  由于表情符号是字符，因此可以像 HTML 中的其他任何字符一样复制、显示和调整它们的大小

---

---

---

----

## <u>HTML 编码（字符集）</u>

​	**ASCII 字符集**

​		ASCII 使用 0 到 31（以及 127）之间的值作为控制字符。

​		ASCII 使用 32 到 126 的值表示字母、数字和符号。

​		ASCII 不使用 128 到 255 之间的值。

### 	ANSI 字符集 (Windows-1252)

​		对于 0 到 127 的值，ANSI 与 ASCII 相同。

​		ANSI 有一组专有的字符，其值从 128 到 159。

​		对于 160 到 255 的值，ANSI 与 UTF-8 相同。

### 	ISO-8859-1 字符集

​		对于 0 到 127 的值，8859-1 与 ASCII 相同。

​		8859-1 不使用 128 到 159 之间的值。

​		对于从 160 到 255 的值，8859-1 与 UTF-8 相同。

### 	UTF-8 字符集

​		对于 0 到 127 的值，UTF-8 与 ASCII 相同。

​		UTF-8 不使用 12 8到 159 之间的值。

​		对于 160 到 255 之间的值，UTF-8 与 ANSI 和 8859-1 相同。

​		UTF-8 从值 256 继续，包含超过 10000 个不同字符

----

---

---

---

## <u>HTML 统一资源定位器</u>

​	URL - Uniform Resource Locator

----

### 	网址遵守的语法规则：

```
scheme://host.domain:port/path/filename
```

​	比如 http://www.w3school.com.cn/html/index.asp

​	解释：

- scheme - 定义因特网服务的类型。最常见的类型是 http
- host - 定义域主机（http 的默认主机是 www）
- domain - 定义因特网域名，比如 w3school.com.cn
- :port - 定义主机上的端口号（http 的默认端口号是 80）
- path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）。
- filename - 定义文档/资源的名称

---

### 	URL Schemes

| Scheme | 访问               | 用于...                             |
| :----- | :----------------- | :---------------------------------- |
| http   | 超文本传输协议     | 以 http:// 开头的普通网页。不加密。 |
| https  | 安全超文本传输协议 | 安全网页。加密所有信息交换。        |
| ftp    | 文件传输协议       | 用于将文件下载或上传至网站。        |
| file   |                    | 您计算机上的文件。                  |

----

---

----

----

## <u>HTML框架</u>

​	通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。每份HTML文	档称为一个框架，并且每个框架都独立于其他的框架。

​	使用框架的坏处：		 

- 开发人员必须同时跟踪更多的HTML文档	
- 很难打印整张页面

---

###  **框架结构标签（<frameset>）**

- 框架结构标签（<frameset>）定义如何将窗口分割为框架
- 每个 frameset 定义了一系列行*或*列
- rows/columns 的值规定了每行或每列占据屏幕的面积

---

### `<frame>`

​	在下面的这个例子中，我们设置了一个两列的框架集。第一列被设置为占据浏	览器窗口的 25%。第二列被设置为占据浏览器窗口的 75%。HTML 文档 "frame_a.htm" 被置于第一个列中，而 HTML 文档 "frame_b.htm" 被置于第二个列	中：

```html
<frameset cols="25%,75%">
   <frame src="frame_a.htm">
   <frame src="frame_b.htm">
</frameset>
```

---

NOTE:假如一个框架有可见边框，用户可以拖动边框来改变它的大小。为了避免			这种情况发生，可以在 <frame> 标签中加入：noresize="noresize"。

**<u>重要提示：</u>**不能将 `<body></body>` 标签与 `<frameset></frameset>` 标签同					 时使用！不过，假如你添加包含一段文本的 `<noframes>` 标签，就必					须将这段文字嵌套于 `<body></body>` 标签内。（在下面的第一个实					例中，可以查看它是如何实现的。）

---

---

---

---

## <u>HTML背景(bakcgrounds)</u>

​	<body> 拥有两个配置背景的标签。背景可以是颜色或者图像。

### 	背景颜色(Bgcolor)

​		背景颜色属性将背景设置为某种颜色。属性值可以是十六进制数、RGB 值或		颜色名。

```html
<body bgcolor="#000000">
<body bgcolor="rgb(0,0,0)">
<body bgcolor="black">
```

----

### 	背景（Background）

​		背景属性将背景设置为图像。属性值为图像的URL。如果图像尺寸小于浏览器		窗口，那么图像将在整个浏览器窗口进行复制。

```html
<body background="clouds.gif">
<body background="http://www.w3school.com.cn/clouds.gif">
```

​	**提示：**如果你打算使用背景图片，你需要紧记一下几点：

- 背景图像是否增加了页面的加载时间。小贴士：图像文件不应超过 10k。

---

---

---

---

## HTML URL 字符编码

​	**URL 编码会将字符转换为可通过因特网传输的格式。**

​	











































