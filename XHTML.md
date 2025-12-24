# XHTML

## 	XHTML简介	

​       <u>**XHTML 是以 XML 格式编写的 HTML**</u>

​		**<u>HTML 会被 XHTML 取代。</u>**

​		<u>**XHTML 是一个 Web 标准。**</u>

### 	什么是 XHTML

- XHTML 指的是可扩展超文本标记语言
- XHTML 与 HTML 4.01 几乎是相同的
- XHTML 是更严格更纯净的 HTML 版本
- XHTML 是以 XML 应用的方式定义的 HTML
- XHTML 是 [2001 年 1 月](https://www.w3school.com.cn/w3c/w3c_xhtml.asp)发布的 W3C 推荐标准
- XHTML 得到所有主流浏览器的支持

---

### 	为什么使用 XHTML

​		因特网上的很多页面包含了“糟糕”的 HTML

​		XML 是一种必须正确标记且格式良好的标记语言

​		所以 - 通过结合 XML 和 HTML 的长处，开发出了 XHTML。XHTML 是作为 		XML 被重新设计的 HTML

---

### 	与HTML的区别

### 		文档结构

- XHTML DOCTYPE 是*强制性的*
- `<html>` 中的 XML namespace 属性是*强制性的*
- `<html>、<head>、<title> 以及 <body>` 也是*强制性的*

### 		元素语法

- XHTML 元素必须*正确嵌套*
- XHTML 元素必须始终*关闭*
- XHTML 元素必须*小写*
- XHTML 文档必须有*一个根元素*

### 		属性语法

- XHTML 属性必须使用*小写*
- XHTML 属性值必须用*引号包围*
- XHTML 属性最小化也是*禁止的*

---

### 	`<!DOCTYPE ....>` 是强制性的

​			`<html>、<head>、<title>` 以及 `<body>` 元素也必须存在，并且必须使用     			`<html>` 中的 xmlns 属性为文档规定 xml 命名空间。

​			<u>**DOCTYPE 没有关闭标签。**</u>

---

### 	如何从 HTML 转换到 XHTML

1. 向每张页面的第一行添加 XHTML <!DOCTYPE>
2. 向每张页面的 html 元素添加 xmlns 属性
3. 把所有元素名改为小写
4. 关闭所有空元素
5. 把所有属性名改为小写
6. 为所有属性值加引号

---

---

---

## XHTML元素

### 	元素语法规则

- XHTML 元素必须*正确嵌套*
- XHTML 元素必须始终*关闭*
- XHTML 元素必须*小写*
- XHTML 文档必须有*一个根元素*

---

### 	元素必须正确嵌套

​		在 HTML 中，某些元素可以不正确地彼此嵌套在一起，就像这样：	

```
<b><i>This text is bold and italic</b></i>
```

​		在 XHTML 中，所有元素必须正确地彼此嵌套，就像这样：

```
<b><i>This text is bold and italic</i></b>
```

---

### 	元素必须始终关闭

```
A break: <br />
A horizontal rule: <hr />
An image: <img src="happy.gif" alt="Happy face" />
```

---

### 	元素必须小写

```
<body>
<p>This is a paragraph</p>
</body>
```

---

---

---

## XHTML属性

### 	属性 - 语法规则

- XHTML 属性必须使用*小写*
- XHTML 属性值必须用*引号包围*
- XHTML 属性最小化也是*禁止的*

---

### 	属性必须使用小写

​		`<table width="100%">`

---

### 	属性值必须用引号包围

​		`<table width="100%">`

---

### 	禁止属性简写

```
<input checked="checked" />
<input readonly="readonly" />
<input disabled="disabled" />
<option selected="selected" />
```

---

---

---









