[[HTML]]

[[XHTML]]
[[CSS]]
[[微信小程序]]
# XML基础

## 简介

​	**XML 被设计用来传输和存储数据。**																																					 	**HTML 被设计用来显示数据**																																							 	 	**XML 被设计为传输和存储数据，其焦点是数据的内容.**																									 		 	 	**HTML 被设计用来显示数据，其焦点是数据的外观**

### 	什么是 XML?

- XML 指可扩展标记语言（*EX*tensible *M*arkup *L*anguage）
- XML 的设计宗旨是***<u>传输数据</u>***，而非显示数据
- XML 标签没有被预定义。您需要*自行定义标签*。
- XML 被设计为具有*自我描述性*。

### 	特点

- **XML 是不作为的**
- XML没有预定义标签
- *XML 是独立于软件和硬件的信息传输工具*

---

---

---

## 用途

​	通过 XML，数据能够存储在独立的 XML 文件中

​	通过使用几行 JavaScript，你就可以读取一个外部 XML 文件，然后更新 HTML 中的数据内容

​	就可以专注于使用 HTML 进行布局和显示，确保修改底层数据不再需要对 HTML 进行任何的改变

---

---

---

## 树结构

​	**XML 文档形成了一种树结构，它从“根部”开始，然后扩展到“枝叶”**

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<note>
<to>George</to>
<from>John</from>
<heading>Reminder</heading>
<body>Don't forget the meeting!</body>
</note>
```

​	注释

- 第一行是XML声明，定义版本(1.0)和所使用的编码(ISO-8859-1=Latin-1)
- `<note>`文档根元素
- 3-6行描述4个子元素
- 最后一行定义根元素结尾

<img src="https://www.w3school.com.cn/i/ct_nodetree1.gif" alt="img"  />

---

---

---

## 语法规则

1. 所有 XML 元素都须有关闭标签，在 XML 中，**省略关闭标签是非法的**。所有元素都*必须*有关闭标签
2. XML 标签对大小写敏感，**必须使用相同的大小写**来编写打开标签和关闭标签
3. 必须正确地嵌套
4. XML 文档必须有根元素
5. XML 的属性值须加引号
6. 实体引用

|  `&lt;`  | `<`  |  `小于`  |
| :------: | :--: | :------: |
|  `&gt;`  |  >   |  `大于`  |
| `&amp;`  |  &   |  `和号`  |
| `&apos;` | `'`  | `单引号` |
| `&quot;` |  "   |   引号   |

​	**注释：**在 XML 中，只有字符 "<" 和 "&" 确实是非法的。大于号是合法的，但是用实体引用来代替它是一个好习惯

​			7.XML 中的注释

​				在 XML 中编写注释的语法与 HTML 的语法很相似：

```xml
<!-- This is a comment -->
```

​			8.XML 中，空格会被保留

​			9.XML 以 LF 存储换行

---

---

---

## 元素

### 	什么是 XML 元素？

​		*XML 元素*指的是从（且包括）开始标签直到（且包括）结束标签的部分

---

### 	XML 命名规则

- 名称可以含字母、数字以及其他的字符
- 名称不能以数字或者标点符号开始
- 名称不能以字符 “xml”（或者 XML、Xml）开始
- 名称不能包含空格
- 可使用任何名称，没有保留的字词

---

### 	最佳命名习惯

​		使名称具有描述性。使用**下划线**的名称也很不错

- 避免	"-"  ,一些软件会认为你需要提取第一个单词
- 避免    "."  ,一些软件会认为后者是前者的属性
- 避免   ":"  ,冒号会被转换为命名空间来使用

---

### 	XML 元素是可扩展的

​		向已经创建好的应用程序添加额外的信息，应用程序不会中断

---

---

---

## 属性

​	**XML属性必须加引号！！！**(单引号或双引号都可以)

​	**注释：**如果属性值本身包含双引号，那么有必要使用单引号包围它

```xml
<gangster name='George "Shotgun" Ziegler'>
```

​	或者可以使用实体引用：

```xml
<gangster name="George &quot;Shotgun&quot; Ziegler">
```

---

### 	元素和属性

​		多种使用方法

```xml
<note date="08/08/2008">
    
<date>08/08/2008</date>
    
<date>
  <day>08</day>
  <month>08</month>
  <year>2008</year>
</date>
```

---

### 	避免XML属性

- 属性无法包含多重的值（元素可以）
- 属性无法描述树结构（元素可以）
- 属性不易扩展（为未来的变化）
- 属性难以阅读和维护

​		**请尽量使用元素来描述数据！！！**

---

### 	针对元数据的 XML 属性

​		有时候会向元素分配 ID 引用。这些 ID 索引可用于标识 XML 元素

> 元数据（有关数据的数据）应当存储为属性，而数据本身应当存储为元素

---

---

---

## 验证

​	**通过 DTD 验证的 XML 是“合法”的 XML**

### 	形式良好的 XML 文档

- XML 文档必须有根元素
- XML 文档必须有关闭标签
- XML 标签对大小写敏感
- XML 元素必须被正确的嵌套
- XML 属性必须加引号

---

### 	验证 XML 文档

```xml
	<!DOCTYPE note SYSTEM "Note.dtd">
```

​		DOCTYPE 声明是对外部 DTD 文件的引用

---

### 	XML DTD

​		DTD 的作用是定义 XML 文档的结构。它使用一系列合法的元素来定义文档结构

```xml
<!DOCTYPE note [
  <!ELEMENT note (to,from,heading,body)>
  <!ELEMENT to      (#PCDATA)>
  <!ELEMENT from    (#PCDATA)>
]> 
```

---

### 	XML Schema

​		W3C 支持一种基于 XML 的 DTD 代替者，它名为 XML Schema：

```xml
<xs:element name="note">

<xs:complexType>
  <xs:sequence>
    <xs:element name="to"      type="xs:string"/>
    <xs:element name="from"    type="xs:string"/>
  </xs:sequence>
</xs:complexType>
</xs:element> 
```

---

## 验证器

​	**XML 错误会终止您的程序**

> ​	W3C 的 XML 规范声明：如果 XML 文档存在错误，那么程序就不应当继续处理这个文档。
>
> ​	理由是：XML 软件应当轻巧，快速，具有良好的兼容性。

​	HTML浏览器相当臃肿，兼容性差，在XML中不应出现这种情况

---

### 	多种验证方式

- 对XML代码片段检查
- 对XML文件检查
- 在IE中用DTD检查

---

---

---

## 查看 XML 文件

​	**在所有现代浏览器中，均能够查看原始的 XML 文件。**

​	**不要指望 XML 文件会直接显示为 HTML 页面**

- 查看XML文件：如需查看不带有 + 和 - 符号的源代码，请从浏览器菜单中选择“查看源代码”。
- 查看无效的XML文件：如果浏览器打开了某个有错误的 XML 文件，那么它会报告这个错误

---

---

---

## 使用CSS显示XML	

### 	链接到CSS

```xml
<?xml-stylesheet type="text/css" href="cd_catalog.css"?>
```

> 使用 CSS 格式化 XML 不是常用的方法，更不能代表 XML 文档样式化的未来。W3C 推荐使用 XSLT

---

---

---

## 使用 XSLT 显示 XML

​	XSLT 是首选的 XML 样式表语言。

​	XSLT (eXtensible Stylesheet Language Transformations) 远比 CSS 更加完善

### 	链接到XSLT

```xml
<?xml-stylesheet type="text/xsl" href="simple.xsl"?>
```

### 	在服务器上通过 XSLT 转换 XML

​		在上例中，XSLT 转换是由浏览器完成的，浏览器读取的是 XML 文件

​		在使用 XSLT 来转换 XML 时,不同的浏览器可能会产生不同结果。为了减少这种问题,可以在服务器上进行 XSLT 转换

---

---

---

# XML JavaScript

## HTTP Request

​	















