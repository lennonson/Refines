# HTML 表单

​	**HTML 表单用于搜集不同类型的用户输入。**

## 基本概要

### 	`<form>` 元素

​		定义 HTML 表单

---

### 	HTML 表单包含*表单元素*

​		指的是不同类型的 input 元素、复选框、单选按钮、提交按钮等

---

### 	`<input>` 元素

​		`*<input>*` 元素是最重要的*表单元素*。

​		`<input>` 元素有很多形态，根据不同的 *type* 属性

---

### 	文本输入

​		*`<input type="text">`* 定义用于*文本输入*的单行输入字段

```html
<form>
First name:<br>
<input type="text" name="firstname">
<br>
Last name:<br>
<input type="text" name="lastname">
</form>
```
![image-20231127215535210](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127215535210.png)

---

### 	单选按钮输入

​		`*<input type="radio">*` 定义*单选按钮*

```
<form>
<input type="radio" name="sex" value="male" checked>Male
<br>
<input type="radio" name="sex" value="female">Female
</form> 
```

![image-20231127215636016](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127215636016.png)

---

### 	提交按钮

​		*`<input type="submit">`* 定义用于向*表单处理程序*（form-handler）*提交*表单的按钮

```
<form action="action_page.php">
First name:<br>
<input type="text" name="firstname" value="Mickey">
<br>
Last name:<br>
<input type="text" name="lastname" value="Mouse">
<br><br>
<input type="submit" value="Submit">
</form> 
```

![image-20231127215729393](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127215729393.png)

---

### 	Action 属性

​			action 属性*定义在提交表单时执行的动作。

​			向服务器提交表单的通常做法是使用提交按钮。

​			通常，表单会被提交到 web 服务器上的网页

---

### Method 属性

​		*method 属性*规定在提交表单时所用的 HTTP 方法（*GET* 或 *POST*）：

```
<form action="action_page.php" method="GET">
```

​		或：

```
<form action="action_page.php" method="POST">
```

---

### 何时使用 GET？

​	您能够使用 GET（默认方法）：

​	如果表单提交是被动的（比如搜索引擎查询），并且没有敏感信息。

​	当您使用 GET 时，表单数据在页面地址栏中是可见的：

```
action_page.php?firstname=Mickey&lastname=Mouse
```

---

### 何时使用 POST？

​	您应该使用 POST：

​	如果表单正在更新数据，或者包含敏感信息（例如密码）。

​	POST 的安全性更好，因为在页面地址栏中被提交的数据是不可见的

---

### Name 属性

​	如果要正确地被提交，每个输入字段必须设置一个 name 属性。

​	本例只会提交 "Last name" 输入字段：

---

### 用 `<fieldset>` 组合表单数据

​	*`<fieldset>`* 元素组合表单中的相关数据

*`	<legend>`* 元素为 `<fieldset>` 元素定义标题

```
<form action="action_page.php">
<fieldset>
<legend>Personal information:</legend>
First name:<br>
<input type="text" name="firstname" value="Mickey">
<br>
Last name:<br>
<input type="text" name="lastname" value="Mouse">
<br><br>
<input type="submit" value="Submit"></fieldset>
</form> 
```

![image-20231127220030994](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127220030994.png)

---

---

---

## 表单属性

​	**介绍 HTML `<form>` 元素的不同属性**

### 	Action 属性

​		`action` 属性定义提交表单时要执行的操作。

​		通常，当用户单击“提交”按钮时，表单数据将发送到服务器上的文件中

​		**提示：**如果省略 action 属性，则将 action 设置为当前页面

---

### 	Target 属性

​		`target` 属性规定提交表单后在何处显示响应。

​		`target` 属性可设置以下值之一：

| 值        | 描述                           |
| :-------- | :----------------------------- |
| _blank    | 响应显示在新窗口或选项卡中。   |
| _self     | 响应显示在当前窗口中。         |
| _parent   | 响应显示在父框架中。           |
| _top      | 响应显示在窗口的整个 body 中。 |
| framename | 响应显示在命名的 iframe 中。   |

​		默认值为 `_self`，这意味着响应将在当前窗口中打开

---

### 	Method 属性

​		method 属性指定提交表单数据时要使用的 HTTP 方法。

​		表单数据可以作为 URL 变量（使用 `method="get"`）或作为 HTTP post 事务（使用 `method="post"`）发送。

​		提交表单数据时，默认的 HTTP 方法是 GET。

​		此例在提交表单数据时使用 GET 方法：

```
<form action="/action_page.php" method="get">
```

---

### 	关于 GET 的注意事项：

- 以名称/值对的形式将表单数据追加到 URL
- 永远不要使用 GET 发送敏感数据！（提交的表单数据在 URL 中可见！）
- URL 的长度受到限制（2048 个字符）
- 对于用户希望将结果添加为书签的表单提交很有用
- GET 适用于非安全数据，例如 Google 中的查询字符串

### 	关于 POST 的注意事项：

- 将表单数据附加在 HTTP 请求的正文中（不在 URL 中显示提交的表单数据）
- POST 没有大小限制，可用于发送大量数据。
- 带有 POST 的表单提交无法添加书签

​		**提示：**如果表单数据包含敏感信息或个人信息，请务必使用 POST！

---

### 	Autocomplete 属性

​		`autocomplete` 属性规定表单是否应打开自动完成功能。

​		启用自动完成功能后，浏览器会根据用户之前输入的值自动填写值。

​		启用自动填写的表单：

```
<form action="/action_page.php" autocomplete="on">
```

---

### 	Novalidate 属性

​			`novalidate` 属性是一个布尔属性。

​			如果已设置，它规定提交时不应验证表单数据。

​			未设置 novalidate 属性的表单：

```
<form action="/action_page.php" novalidate>
```

---

### 	所有 `<form>` 属性的列表

| 属性                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [accept-charset](https://www.w3school.com.cn/tags/att_form_accept-charset.asp) | 规定用于表单提交的字符编码。                                 |
| [action](https://www.w3school.com.cn/tags/att_form_action.asp) | 规定提交表单时将表单数据发送到何处。                         |
| [autocomplete](https://www.w3school.com.cn/tags/att_form_autocomplete.asp) | 规定表单是否应打开自动完成（填写）功能。                     |
| [enctype](https://www.w3school.com.cn/tags/att_form_enctype.asp) | 规定将表单数据提交到服务器时应如何编码（仅供 method="post"）。 |
| [method](https://www.w3school.com.cn/tags/att_form_method.asp) | 规定发送表单数据时要使用的 HTTP 方法。                       |
| [name](https://www.w3school.com.cn/tags/att_form_name.asp)   | 规定表单名称。                                               |
| [novalidate](https://www.w3school.com.cn/tags/att_form_novalidate.asp) | 规定提交时不应验证表单。                                     |
| [rel](https://www.w3school.com.cn/tags/att_form_rel.asp)     | 规定链接资源和当前文档之间的关系。                           |
| [target](https://www.w3school.com.cn/tags/att_form_target.asp) | 规定提交表单后在何处显示接收到的响应。                       |

---

---

---

## 表单元素

### 	`<input>` 元素

​		最重要的表单元素是 `*<input>*` 元素。

​		`<input>` 元素根据不同的 *type* 属性，可以变化为多种形态

---

### 	`<select>` 元素（下拉列表）

​		`*<select>*` 元素定义*下拉列表*：

```
<select name="cars">
<option value="volvo">Volvo</option>
<option value="saab">Saab</option>
<option value="fiat">Fiat</option>
<option value="audi">Audi</option>
</select>
```

![image-20231127220706556](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127220706556.png)

---

### 	`*<option>*` 元素定义待选择的选项。

​		列表通常会把首个选项显示为被选选项。

​		您能够通过添加 selected 属性来定义预定义选项。

```
<option value="fiat" selected>Fiat</option>
```

![image-20231127220747426](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127220747426.png)

---

### 	`<textarea>` 元素

​		`*<textarea>*` 元素定义多行输入字段（*文本域*）：

```
<textarea name="message" rows="10" cols="30">
The cat was playing in the garden.
</textarea>
```

![image-20231127220833526](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127220833526.png)

---

### 	`<button>` 元素

​		*`<button>`* 元素定义可点击的*按钮*：

```
<button type="button" onclick="alert('Hello World!')">Click Me!</button>
```

![image-20231127220927932](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127220927932.png)

---

### 	HTML5 表单元素

​		HTML5 增加了如下表单元素：

- `<datalist>`
- `<keygen>`
- `<output>`

​			**注释：**默认地，浏览器不会显示未知元素。新元素不会破坏您的页面

---

### 	`<datalist>` 元素

​		*`<datalist>`* 元素为 `<input>` 元素规定预定义选项列表。

​		用户会在他们输入数据时看到预定义选项的下拉列表。

​		`<input>` 元素的 *list* 属性必须引用 `<datalist>` 元素的 *id* 属性。

​		通过 `<datalist>` 设置预定义值的 `<input>` 元素：

```
<form action="action_page.php">
<input list="browsers">
<datalist id="browsers">
   <option value="Internet Explorer">
   <option value="Firefox">
   <option value="Chrome">
   <option value="Opera">
   <option value="Safari">
</datalist> 
</form>
```

![image-20231127221123694](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221123694.png)

---

---

---

## 输入类型

​	**描述 <input> 元素的输入类型**

### 	输入类型：text

​		`*<input type="text">*` 定义供*文本输入*的单行输入字段：

```
<form>
 First name:<br>
<input type="text" name="firstname">
<br>
 Last name:<br>
<input type="text" name="lastname">
</form> 
```

![image-20231127221243615](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221243615.png)

---

### 	输入类型：password

​		*`<input type="password">`* 定义*密码字段*：

```
<form>
 User name:<br>
<input type="text" name="username">
<br>
 User password:<br>
<input type="password" name="psw">
</form> 
```

![image-20231127221358320](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221358320.png)

---

### 	输入类型：submit

​		*`<input type="submit">`* 定义*提交*表单数据至*表单处理程序*的按钮。

​		表单处理程序（form-handler）通常是包含处理输入数据的脚本的服务器页面。

​		在表单的 action 属性中规定表单处理程序（form-handler）：

```
<form action="action_page.php">
First name:<br>
<input type="text" name="firstname" value="Mickey">
<br>
Last name:<br>
<input type="text" name="lastname" value="Mouse">
<br><br>
<input type="submit" value="Submit">
</form> 
```

​		![image-20231127221453963](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221453963.png)

​		如果您省略了提交按钮的 value 属性，那么该按钮将获得默认文本

---

### 	Input Type: radio

​		`<input type="radio">` 定义单选按钮。

​		Radio buttons let a user select ONLY ONE of a limited number of choices:

```
<form>
<input type="radio" name="sex" value="male" checked>Male
<br>
<input type="radio" name="sex" value="female">Female
</form> 
```

![image-20231127221529243](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221529243.png)

---

### 	Input Type: checkbox

​		`<input type="checkbox">` 定义复选框。

​		复选框允许用户在有限数量的选项中选择零个或多个选项。

```
<form>
<input type="checkbox" name="vehicle" value="Bike">I have a bike
<br>
<input type="checkbox" name="vehicle" value="Car">I have a car 
</form> 
```

![image-20231127221607259](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221607259.png)

---

### 	Input Type: button

​		*`<input type="button>`* 定义*按钮*。

```
<input type="button" onclick="alert('Hello World!')" value="Click Me!">
```

---

### 	HTML5 输入类型

​		HTML5 增加了多个新的输入类型：

- color
- date
- datetime
- datetime-local
- email
- month
- number
- range
- search
- tel
- time
- url
- week

​		**注释：**老式 web 浏览器不支持的输入类型，会被视为输入类型 text

---

### 	输入类型：number

​		`*<input type="number">*` 用于应该包含数字值的输入字段。

​		您能够对数字做出限制。

​		根据浏览器支持，限制可应用到输入字段。

```
<form>
  Quantity (between 1 and 5):
  <input type="number" name="quantity" min="1" max="5">
</form>
```

![image-20231127221738046](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221738046.png)

---

### 	输入类型：date

​		*`<input type="date">`* 用于应该包含日期的输入字段。

​		根据浏览器支持，日期选择器会出现输入字段中。

```
<form>
  Birthday:
  <input type="date" name="bday">
</form>
```

![image-20231127221847917](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221847917.png)

---

### 	输入类型：range

​		*`<input type="range">`* 用于应该包含一定范围内的值的输入字段。

​		根据浏览器支持，输入字段能够显示为滑块控件。

```
<form>
  <input type="range" name="points" min="0" max="10">
</form>
```

![image-20231127221926548](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127221926548.png)

---

### 	输入类型：datetime-local

​		*`<input type="datetime-local">`* 允许用户选择日期和时间（无时区）。

​		根据浏览器支持，日期选择器会出现输入字段中。

```
<form>
  Birthday (date and time):
  <input type="datetime-local" name="bdaytime">
</form>
```

![image-20231127222035282](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222035282.png)

---

### 	输入类型：email

​		`*<input type="email">*` 用于应该包含电子邮件地址的输入字段。

​		根据浏览器支持，能够在被提交时自动对电子邮件地址进行验证。

​		某些智能手机会识别 email 类型，并在键盘增加 ".com" 以匹配电子邮件输入。

```
<form>
  E-mail:
  <input type="email" name="email">
</form>
```

![image-20231127222113250](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222113250.png)

---

### 	输入类型：search

​		*`<input type="search">`* 用于搜索字段（搜索字段的表现类似常规文本字段）。

```
<form>
  Search Google:
  <input type="search" name="googlesearch">
</form>
```

![image-20231127222142730](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222142730.png)

---

### 	输入类型：url

​		`*<input type="url">*` 用于应该包含 URL 地址的输入字段。

​		根据浏览器支持，在提交时能够自动验证 url 字段。

​		某些智能手机识别 url 类型，并向键盘添加 ".com" 以匹配 url 输入。

```
<form>
  Add your homepage:
  <input type="url" name="homepage">
</form>
```

![image-20231127222226174](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222226174.png)

---

---

---

## Input 属性

### 	value 属性

​		*value* 属性规定输入字段的初始值：

```
<form action="">
 First name:<br>
<input type="text" name="firstname" value="Bill">
<br>
 Last name:<br>
<input type="text" name="lastname">
</form> 
```

![image-20231127222318643](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222318643.png)

---

### 	readonly 属性

​		*readonly* 属性规定输入字段为只读（不能修改）：

```
<form action="">
 First name:<br>
<input type="text" name="firstname" value="Bill" readonly>
<br>
 Last name:<br>
<input type="text" name="lastname">
</form> 
```

​		readonly 属性不需要值。它等同于 readonly="readonly"。

![image-20231127222403878](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222403878.png)

---

### 	disabled 属性

​		disabled* 属性规定输入字段是禁用的。

​		被禁用的元素是不可用和不可点击的。

​		被禁用的元素不会被提交。

```
<form action="">
 First name:<br>
<input type="text" name="firstname" value="Bill" disabled>
<br>
 Last name:<br>
<input type="text" name="lastname">
</form> 
```

![image-20231127222440927](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222440927.png)

---

### 	size 属性

​		*size* 属性规定输入字段的尺寸（以字符计）：

```
<form action="">
 First name:<br>
<input type="text" name="firstname" value="Bill" size="40">
<br>
 Last name:<br>
<input type="text" name="lastname">
</form> 
```

![image-20231127222514327](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222514327.png)

---

### 	maxlength 属性

* ​	maxlength* 属性规定输入字段允许的最大长度：

```
<form action="">
 First name:<br>
<input type="text" name="firstname" maxlength="10">
<br>
 Last name:<br>
<input type="text" name="lastname">
</form> 
```

​		如设置 maxlength 属性，则输入控件不会接受超过所允许数的字符。

​		该属性不会提供任何反馈。如果需要提醒用户，则必须编写 JavaScript 代码。

​		**注释：**输入限制并非万无一失。JavaScript 提供了很多方法来增加非法输入。如需安全地限制输入，则接受者（服务					 器）必须同时对限制进行检查。

---

### 	HTML5 属性

​		HTML5 为 `<input>` 增加了如下属性：

- autocomplete
- autofocus
- form
- formaction
- formenctype
- formmethod
- formnovalidate
- formtarget
- height 和 width
- list
- min 和 max
- multiple
- pattern (regexp)
- placeholder
- required
- step

​		并为 `<form>` 增加如需属性：

- autocomplete
- novalidate

---

### 	autofocus 属性

​		autofocus 属性是布尔属性。

​		如果设置，则规定当页面加载时 `<input>` 元素应该自动获得焦点。

​		使 "First name" 输入字段在页面加载时自动获得焦点：

```
First name:<input type="text" name="fname" autofocus>
```

---

### 	form 属性

​		form 属性规定 `<input>` 元素**所属的一个或多个表单。**

​		**提示：**如需引用一个以上的表单，请使用空格分隔的表单 id 列表。

​		输入字段位于 HTML 表单之外（但仍属表单）：

---

### 	formaction 属性

​		formaction 属性规定当提交表单时处理该输入控件的文件的 URL。

​		formaction 属性覆盖 <form> 元素的 action 属性。

​		formaction 属性适用于 type="submit" 以及 type="image"。

​		拥有两个两个提交按钮并对于不同动作的 HTML 表单：

```
<form action="action_page.php">
   First name: <input type="text" name="fname"><br>
   Last name: <input type="text" name="lname"><br>
   <input type="submit" value="Submit"><br>
   <input type="submit" formaction="demo_admin.asp"
   value="Submit as admin">
</form> 
```

​	![image-20231127222920545](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127222920545.png)

---

### 	formenctype 属性

​		formenctype 属性规定当把表单数据（form-data）提交至服务器时如何对其进行编码（仅针对 method="post" 的表		单）。

​		formenctype 属性覆盖 <form> 元素的 enctype 属性。

​		formenctype 属性适用于 type="submit" 以及 type="image"。

​		发送默认编码以及编码为 "multipart/form-data"（第二个提交按钮）的表单数据（form-data）：

```
<form action="demo_post_enctype.asp" method="post">
   First name: <input type="text" name="fname"><br>
   <input type="submit" value="Submit">
   <input type="submit" formenctype="multipart/form-data"
   value="Submit as Multipart/form-data">
</form> 
```

![image-20231127223012778](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127223012778.png)

---

### 	formmethod 属性

​		formmethod 属性定义用以向 action URL 发送表单数据（form-data）的 HTTP 方法。

​		formmethod 属性覆盖 <form> 元素的 method 属性。

​		formmethod 属性适用于 type="submit" 以及 type="image"。

​		第二个提交按钮覆盖表单的 HTTP 方法：

```
<form action="action_page.php" method="get">
   First name: <input type="text" name="fname"><br>
   Last name: <input type="text" name="lname"><br>
   <input type="submit" value="Submit">
   <input type="submit" formmethod="post" formaction="demo_post.asp"
   value="Submit using POST">
</form> 
```

![image-20231127223050348](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127223050348.png)

---

### 	formnovalidate 属性

​		novalidate 属性是布尔属性。

​		如果设置，则规定在提交表单时不对 <input> 元素进行验证。

​		formnovalidate 属性覆盖 <form> 元素的 novalidate 属性。

​		formnovalidate 属性可用于 type="submit"。

​		拥有两个提交按钮的表单（验证和不验证）：

```
<form action="action_page.php">
   E-mail: <input type="email" name="userid"><br>
   <input type="submit" value="Submit"><br>
   <input type="submit" formnovalidate value="Submit without validation">
</form> 
```

---

### 	formtarget 属性

​		formtarget 属性规定的名称或关键词指示提交表单后在<u>何处显示接收到的响		应。</u>

​		formtarget 属性会覆盖 <form> 元素的 target 属性。

​		formtarget 属性可与 type="submit" 和 type="image" 使用。

​		这个表单有两个提交按钮，对应不同的目标窗口：

```
<form action="action_page.php">
   First name: <input type="text" name="fname"><br>
   Last name: <input type="text" name="lname"><br>
   <input type="submit" value="Submit as normal">
   <input type="submit" formtarget="_blank"
   value="Submit to a new window">
</form> 
```

---

### 	height 和 width 属性

​		height 和 width 属性规定 <input> 元素的高度和宽度。

​		height 和 width 属性仅用于 <input type="image">。

​		**注释：**请始终规定图像的尺寸。如果浏览器不清楚图像尺寸，则页面会在					图像加载时闪烁。

​		把图像定义为提交按钮，并设置 height 和 width 属性：

```
<input type="image" src="img_submit.gif" alt="Submit" width="48" height="48">
```

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127235856382.png" alt="image-20231127235856382" style="zoom:50%;" />

---

### 	list 属性

​		list 属性引用的 `<datalist>` 元素中包含了 `<input>` 元素的预定义选项。

​		使用 `<datalist>` 设置预定义值的 `<input>` 元素：

```
<input list="browsers">

<datalist id="browsers">
   <option value="Internet Explorer">
   <option value="Firefox">
   <option value="Chrome">
   <option value="Opera">
   <option value="Safari">
</datalist> 
```

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231127235945932.png" alt="image-20231127235945932" style="zoom:50%;" />

---

### 	min 和 max 属性

​		min 和 max 属性规定 `<input>` 元素的最小值和最大值。

​		min 和 max 属性适用于如需输入类型：number、range、date、datetime、		datetime-local、month、time 以及 week。

​		具有最小和最大值的 `<input>` 元素：

```
Enter a date before 1980-01-01:
<input type="date" name="bday" max="1979-12-31">

 Enter a date after 2000-01-01:
<input type="date" name="bday" min="2000-01-02">

 Quantity (between 1 and 5):
<input type="number" name="quantity" min="1" max="5">
```

​		注释:该段代码设置max为5,min为1

---

### 	multiple 属性

​		multiple 属性是布尔属性。

​		如果设置，则规定允许用户在 `<input>` 元素中输入一个以上的值。

​		multiple 属性适用于以下输入类型：email 和 file。

​		接受多个值的文件上传字段：

```
<form action="/example/html5/demo_form.asp" method="get">
选择图片：<input type="file" name="img" multiple="multiple" />
<input type="submit" />
</form>
```

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128181547408.png" alt="image-20231128181547408" style="zoom:67%;" />

---

### 	pattern 属性

​		pattern 属性规定用于检查 `<input>` 元素值的正则表达式。

​		pattern 属性适用于以下输入类型：text、search、url、tel、email、and 			password。

​		**提示：**请使用全局的 title 属性对模式进行描述以帮助用户。

​		**提示：**请在我们的 JavaScript 教程中学习更多有关正则表达式的知识。

​		只能包含三个字母的输入字段（无数字或特殊字符）：

```
Country code: 
<input type="text" name="country_code" pattern="[A-Za-z]{3}" title="Three letter country code">
```

![image-20231128181758471](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128181758471.png)

---

### 	placeholder 属性

​		placeholder 属性规定用以描述输入字段预期值的提示（样本值或有关格式的		简短描述）。

​		该提示会在用户输入值之前显示在输入字段中。

​		placeholder 属性适用于以下输入类型：text、search、url、tel、email 以及 		password。

​		拥有占位符文本的输入字段：

```
<input type="text" name="fname" placeholder="First name">
```

![image-20231128182114275](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128182114275.png)

---

### 	required 属性

​		required 属性是布尔属性。

​		如果设置，则规定在提交表单之前必须填写输入字段。

​		required 属性适用于以下输入类型：text、search、url、tel、email、				password、date pickers、number、checkbox、radio、and file.

​		必填的输入字段：

```
Username: <input type="text" name="usrname" required>
```

![image-20231128183036844](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128183036844.png)

---

### 	step 属性

​		step 属性规定 <input> 元素的合法数字间隔。

​		示例：如果 step="3"，则合法数字应该是 -3、0、3、6、等等。

​		**提示：**step 属性可与 max 以及 min 属性一同使用，来创建合法值的范围。

​		step 属性适用于以下输入类型：number、range、date、datetime、  				datetime-local、month、time 以及 week。

​		拥有具体的合法数字间隔的输入字段：

```
<input type="number" name="points" step="3">
```

![image-20231128183218511](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128183218511.png)

---

---

---

## Input form* 属性

​	**介绍 HTML `<input>` 元素的不同 `form\*` 属性。**

### 	form 属性

​		input 的 `form` 属性规定 `<input>` 元素所属的表单。

​		此属性的值必须等于它所属的 <form> 元素的 id 属性。

​		位于 HTML 表单（但仍是表单的一部分）之外的输入字段：

```
<form action="/action_page.php" id="form1">
  <label for="fname">姓氏：</label>
  <input type="text" id="fname" name="fname"><br><br>
  <input type="submit" value="提交">
</form>

<label for="lname">名字：</label>
<input type="text" id="lname" name="lname" form="form1">
```

---

### 	formaction 属性

​		input 的 `formaction` 属性规定当提交表单时，对输入（数据）进行处理的文件的 URL。

​		**注释：**<u>该属性会覆盖 `<form>` 元素的 `action` 属性</u>。

​		`formaction` 属性适用于以下输入类型：<u>submit 和 image。</u>

​		带有两个提交按钮的 HTML 表单，它们具有不同的操作（action）：

```
<form action="/action_page.php">
  <label for="fname">姓氏：</label>
  <input type="text" id="fname" name="fname"><br><br>
  <label for="lname">名字：</label>
  <input type="text" id="lname" name="lname"><br><br>
  <input type="submit" value="提交">
  <input type="submit" formaction="/action_page2.php" value="以管理员提交">
</form>
```

---

### 	formenctype 属性

​		input 的 `formenctype` 属性指定提交时应如何编码表单数据（仅适用于 method="post" 的表单）。

​		**注释：**此属性将覆盖 `<form>` 元素的 enctype 属性。

​		`formenctype` 属性适用于以下输入类型：submit 和 image。

​		有两个提交按钮的表单。第一个发送使用默认编码的表单数据，第二个发送编码为 "multipart/form-data" 的表单数		据：

```
<form action="/action_page_binary.asp" method="post">
  <label for="fname">First name:</label>
  <input type="text" id="fname" name="fname"><br><br>
  <input type="submit" value="提交">
  <input type="submit" formenctype="multipart/form-data"
  value="以 Multipart/form-data 编码提交">
</form>
```

---

### 	formmethod 属性

​		input 的 `formmethod` 属性定义了将表单数据发送到 action URL 的 HTTP 方法。

​		**注释：**此属性将覆盖 `<form>` 元素的 method 属性。

​		`formmethod` 属性适用于以下输入类型：submit 和 image。

​		表单数据可以作为 URL 变量（method="get"）或作为 HTTP post 事务（method="post"）发送。

---

### 	formtarget 属性

​		input 的 `formtarget` 属性指定一个名称或关键字，该名称或关键字规定在提交表单后在何处显示收到的响应。

​		**注释：**此属性将覆盖 `<form>` 元素的 target 属性。

​		`formtarget` 属性适用于以下输入类型：submit 和 image。

​		有两个提交按钮且有不同目标窗口的表单：

```
<form action="/action_page.php">
  <label for="fname">姓氏：</label>
  <input type="text" id="fname" name="fname"><br><br>
  <label for="lname">名字：</label>
  <input type="text" id="lname" name="lname"><br><br>
  <input type="submit" value="提交">
  <input type="submit" formtarget="_blank" value="提交到新窗口/标签页">
</form>
```

---

### 	formnovalidate 属性

​		input 的 `formnovalidate` 属性规定提交时不应验证 <input> 元素。

​		**注释：**此属性将覆盖 `<form>` 元素的 novalidate 属性。

​		`formnovalidate` 属性适用于以下输入类型：submit。

​		有两个提交按钮的表单（进行和不进行验证）：

```
<form action="/action_page.php">
  <label for="email">Enter your email:</label>
  <input type="email" id="email" name="email"><br><br>
  <input type="submit" value="提交">
  <input type="submit" formnovalidate="formnovalidate"
  value="不进行验证的提交">
</form>
```

---

---

---

# HTML图形

​	**canvas (图形)元素用于在网页上绘制图形**

## 	什么是 Canvas？

​		HTML5 的 canvas 元素使用 JavaScript 在网页上绘制图像。

​		画布是一个矩形区域，您可以控制其每一像素。

​		canvas 拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

---

## 	创建 Canvas 元素

​		向 HTML5 页面添加 canvas 元素。

​		规定元素的 id、宽度和高度：

```
<canvas id="myCanvas" width="200" height="100"></canvas>
```

---

## 	通过 JavaScript 来绘制

​		<u>canvas 元素本身是没有绘图能力的</u>。所有的**绘制工作必须在 JavaScript 内部完成**：

```
<script type="text/javascript">
var c=document.getElementById("myCanvas");
var cxt=c.getContext("2d");
cxt.fillStyle="#FF0000";
cxt.fillRect(0,0,150,75);
</script>
```

​			JavaScript 使用 id 来寻找 canvas 元素：

```
var c=document.getElementById("myCanvas");
```

​		然后，创建 context 对象：

```
var cxt=c.getContext("2d"); 
```

​		getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

​		下面的两行代码绘制一个红色的矩形：

```
cxt.fillStyle="#FF0000";
cxt.fillRect(0,0,150,75); 
```

​		fillStyle 方法将其染成红色，fillRect 方法规定了形状、位置和尺寸。

---

### 	理解坐标

​		上面的 fillRect 方法拥有参数 (0,0,150,75)。

​		意思是：在画布上绘制 150x75 的矩形，从左上角开始 (0,0)。

​		如下图所示，画布的 X 和 Y 坐标用于在画布上对绘画进行定位。

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128214838853.png" alt="image-20231128214838853"  />

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128215323948.png" alt="image-20231128215323948"  />

​			注释：多理解代码看实现方法

---

## 	更多 Canvas 实例

​		下面的在 canvas 元素上进行绘画的更多实例：

#### 	   实例 - 线条

​			通过指定从何处开始，在何处结束，来绘制一条线：

![Canvas 实例：线条](https://www.w3school.com.cn/i/ct_html5_canvas_line.gif)

​		

```html
<script type="text/javascript">

var c=document.getElementById("myCanvas");
var cxt=c.getContext("2d");
cxt.moveTo(10,10);
cxt.lineTo(150,50);
cxt.lineTo(10,50);
cxt.stroke();

</script>
```

​		canvas 元素：

```html
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #c3c3c3;">
Your browser does not support the canvas element.
</canvas>
```

​		**注释：本部分需多理解**

#### 		实例 - 圆形

​			通过规定尺寸、颜色和位置，来绘制一个圆：

![Canvas 实例：圆形](https://www.w3school.com.cn/i/ct_html5_canvas_circle.gif)

​		JavaScript 代码：

```
<script type="text/javascript">

var c=document.getElementById("myCanvas");
var cxt=c.getContext("2d");
cxt.fillStyle="#FF0000";
cxt.beginPath();
cxt.arc(70,18,15,0,Math.PI*2,true);
cxt.closePath();
cxt.fill();

</script>
```

​		canvas 元素：

```
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #c3c3c3;">
Your browser does not support the canvas element.
</canvas>
```

#### 	实例 - 渐变

​		使用您指定的颜色来绘制渐变背景：

![Canvas 实例：渐变](https://www.w3school.com.cn/i/ct_html5_canvas_gradient.gif)

​		JavaScript 代码：

```
<script type="text/javascript">

var c=document.getElementById("myCanvas");
var cxt=c.getContext("2d");
var grd=cxt.createLinearGradient(0,0,175,50);
grd.addColorStop(0,"#FF0000");
grd.addColorStop(1,"#00FF00");
cxt.fillStyle=grd;
cxt.fillRect(0,0,175,50);

</script>
```

​		canvas 元素：

```
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #c3c3c3;">
Your browser does not support the canvas element.
</canvas>
```

#### 	实例 - 图像

​		把一幅图像放置到画布上：

![Canvas 实例：图像](https://www.w3school.com.cn/i/eg_flower.png)

​		JavaScript 代码：

```
<script>
window.onload = function() {
    var canvas = document.getElementById("myCanvas");
    var ctx = canvas.getContext("2d");
    var img = document.getElementById("scream");
   ctx.drawImage(img, 10, 10);
};
</script>
```

​		canvas 元素：	

```
<canvas id="myCanvas" width="244" height="182" style="border:1px solid #d3d3d3;">
Your browser does not support the HTML5 canvas tag.
</canvas>
```

---

---

---

## HTML5 内联 SVG

### 	什么是 SVG？

- SVG 指可伸缩矢量图形 (Scalable Vector Graphics)
- SVG 用于定义用于网络的基于矢量的图形
- SVG 使用 XML 格式定义图形
- SVG 图像在<u>放大或改变尺寸的情况下其图形质量不会有损失</u>
- SVG 是<u>万维网联盟的标准</u>

---

### 	SVG 的优势

​		与其他图像格式相比（比如 JPEG 和 GIF），使用 SVG 的优势在于：

- SVG 图像可通过文本编辑器来创建和修改
- SVG 图像可被搜索、索引、脚本化或压缩
- SVG 是可伸缩的
- SVG 图像可在任何的分辨率下被高质量地打印
- SVG 可在图像质量不下降的情况下被放大

---

### 	把 SVG 直接嵌入 HTML 页面

​		在 HTML5 中，您能够将 SVG 元素直接嵌入 HTML 页面中：

```
<!DOCTYPE html>
<html>
<body>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="190">
  <polygon points="100,10 40,180 190,60 10,60 160,180"
  style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
</svg>

</body>
</html>
```

![image-20231128220217802](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128220217802.png)

---

---

---

## HTML 5 Canvas vs. SVG

​	**Canvas 和 SVG 都允许您在浏览器中创建图形，但是它们在根本上是不同的。**

---

### SVG

​		SVG 是一种使用 XML <u>描述 2D 图形</u>的语言。

​		SVG <u>基于 XML</u>，这意味着 SVG DOM 中的每个元素都是可用的。您可以为某个元素附加 JavaScript 事件处理器。

​		在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够<u>自动重现图形</u>。

---

### 	Canvas

​		Canvas 通过 <u>JavaScript</u> 来<u>绘制 2D 图形</u>。

​		Canvas 是<u>逐像素进行渲染</u>的。

​		在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要		<u>重新绘制</u>，包括任何或许已被图形覆盖的对象。

---

### 	Canvas 与 SVG 的比较

​		下表列出了 canvas 与 SVG 之间的一些不同之处。

#### 		Canvas

- <u>依赖分辨率</u>
- 不支持事件处理器
- <u>弱的文本渲染能力</u>
- <u>能够以 .png 或 .jpg 格式保存结果图像</u>
- 最适合<u>图像密集型的游戏</u>，其中的许多对象会被频繁重绘

#### 		SVG

- <u>不依赖分辨率</u>
- 支持事件处理器
- 最适合带有<u>大型渲染区域的应用程序（比如谷歌地图）</u>
- 复杂度高会<u>减慢渲染速度</u>（任何过度使用 DOM 的应用都不快）
- <u>不适合游戏应用</u>

---

---

---

# HTML 多媒体

​	**Web 上的多媒体指的是音效、音乐、视频和动画。**

​	**现代网络浏览器已支持很多多媒体格式**

## 多媒体

### 	什么是多媒体？

​		多媒体来自多种不同的格式。它可以是您听到或看到的任何内容<u>文字、图片、音乐、音效、录音、电影、动画</u>等		

​		在因特网上，您会经常发现嵌入网页中的多媒体元素，现代浏览器已支持多种多媒体格式。

​		在本教程中，您将了解到不同的多媒体格式，以及如何在您的网页中使用它们。

---

### 	浏览器支持

​		第一款因特网浏览器只支持文本，而且即使是对文本的支持也仅限于单一字体和单一颜色。随后诞生了支持颜色、字		体和文本样式的浏览器，图片支持也被加入。

​		不同的浏览器以不同的方式处理对音效、动画和视频的支持。某些元素能够以内联的方式处理，而某些则需要额外的		插件。

---

### 	多媒体格式

​		多媒体元素（比如视频和音频）存储于媒体文件中。

​		确定媒体类型的最常用的方法是查看文件扩展名。当浏览器得到文件扩展名 .htm 或 .html 时，它会假定该文件是 		HTML 页面。.xml 扩展名指示 XML 文件，而 .css 扩展名指示样式表。图片格式则通过 .gif 或 .jpg 来识别。

​		多媒体元素元素也拥有带有不同扩展名的文件格式，比如 .swf、.wmv、.mp3 以及 .mp4。

---

### 	视频格式

​		MP4 格式是一种新的即将普及的因特网视频格式。HTML5 、Flash 播放器以及优酷等视频网站均支持它。

|   格式    |   文件    | 描述                                                         |
| :-------: | :-------: | :----------------------------------------------------------- |
|    AVI    |   .avi    | AVI (Audio Video Interleave) 格式是由<u>微软</u>开发的。<u>所有运行 Windows 的计算机都支持 AVI 格式</u>。它是因特网上很常见的格式，但非 Windows 计算机并不总是能够播放。 |
|    WMV    |   .wmv    | Windows Media 格式是由<u>微软</u>开发的。Windows Media 在因特网上很常见，但是如果未安装额外的（免费）组件，就无法播放 Windows Media 电影。一些后期的 Windows Media 电影在所有非 Windows 计算机上都无法播放，因为没有合适的播放器。 |
|   MPEG    | .mpg.mpeg | MPEG (Moving Pictures Expert Group) 格式是因特网上最流行的格式。它是跨平台的，得到了所有最流行的浏览器的支持。 |
| QuickTime |   .mov    | QuickTime 格式是由<u>苹果公司</u>开发的。QuickTime 是因特网上常见的格式，但是 QuickTime 电影不能在没有安装额外的（免费）组件的 Windows 计算机上播放。 |
| RealVideo |  .rm.ram  | RealVideo 格式是由 Real Media 针对因特网开发的。该格式允许低带宽条件下（在线视频、网络电视）的视频流。由于是低带宽优先的，质量常会降低。 |
|   Flash   | .swf.flv  | Flash (Shockwave) 格式是由 Macromedia 开发的。Shockwave 格式需要额外的组件来播放。但是该组件会预装到 Firefox 或 IE 之类的浏览器上。 |
|  Mpeg-4   |   .mp4    | Mpeg-4 (with H.264 video compression) 是一种针对因特网的新格式。事实上，YouTube 推荐使用 MP4。YouTube 接收多种格式，然后全部转换为 .flv 或 .mp4 以供分发。越来越多的视频发布者转到 MP4，将其作为 Flash 播放器和 HTML5 的因特网共享格式。 |

---

### 	声音格式

|   格式    |   文件    | 描述                                                         |
| :-------: | :-------: | :----------------------------------------------------------- |
|   MIDI    | .mid.midi | MIDI (Musical Instrument Digital Interface) 是一种针对电子音乐设备（比如合成器和声卡）的格式。MIDI 文件不含有声音，但包含可被电子产品（比如声卡）播放的数字音乐指令。[点击这里播放 The Beatles](https://www.w3school.com.cn/i/beatles.mid)。因为 <u>**MIDI 格式仅包含指令，所以 MIDI 文件极其小巧**</u>。上面的例子只有 <u>23k 的大小，但却能播放将近 5 分钟</u>。MIDI 得到了广泛的平台上的大量软件的支持。大多数流行的网络浏览器都支持 MIDI。 |
| RealAudio |  .rm.ram  | RealAudio 格式是由 Real Media 针对因特网开发的。该格式也支持视频。该格式允许低带宽条件下的音频流（在线音乐、网络音乐）。由于是<u>低带宽优先的，质量常会降低</u>。 |
|   Wave    |   .wav    | Wave (waveform) 格式是由 IBM 和微软开发的。所有运行 Windows 的计算机和所有网络浏览器（除了 Google Chrome）都支持它。 |
|    WMA    |   .wma    | WMA 格式 (Windows Media Audio)，质量优于 MP3，兼容大多数播放器，除了 iPod。WMA 文件可作为连续的数据流来传输，这使它对于网络电台或在线音乐很实用。 |
|    MP3    | .mp3.mpga | MP3 文件实际上是 MPEG 文件的声音部分。MPEG 格式最初是由运动图像专家组开发的。MP3 是其中最受欢迎的针对音乐的声音格式。期待未来的软件系统都支持它。 |

---

### 	使用哪种格式？

​		WAVE 是因特网上最受欢迎的*无压缩*声音格式，所有流行的浏览器都支持它。如果您需要未经压缩的声音（音乐或演		讲），那么您应该使用 WAVE 格式。

​		MP3 是最新的*压缩*录制音乐格式。MP3 这个术语已经成为数字音乐的代名词。如果您的网址从事录制音乐，那么 		MP3 是一个选项。

---

---

---

## 插件

​	**插件（Plug-in）是扩展浏览器标准功能的计算机程序。**

### 	插件

​		插件被设计用于许多不同的目的：

- 运行 Java 小程序
- 运行 ActiveX 控件
- 显示 Flash 电影
- 显示地图
- 扫描病毒
- 验证银行账号

### 		警告！

​		大多数浏览器不再支持 Java Applet 和插件。

​		所有浏览器均不再支持 ActiveX 控件。

​		在现代浏览器中，对 Shockwave Flash 的支持也已关闭。

---

### 	`<object>` 元素

​		所有浏览器均支持 `<object>` 元素。

​		`<object>` 元素定义 HTML 文档中的嵌入式对象。

​		它旨在将插件（例如 Java applet、PDF 阅读器和 Flash 播放器）嵌入网页中，但也可以用于将 HTML 包含在 HTML 		中：

```html
<object width="100%" height="500px" data="snippet.html"></object>
<object data="audi.jpeg"></object>
```

---

### 	`<embed>` 元素

​		所有主要浏览器均支持 `<embed>` 元素。

​		`<embed>` 元素也可定义了 HTML 文档中的嵌入式对象。

​		Web 浏览器长期以来一直支持 <embed> 元素。但是，它不属于 HTML5 之前的 HTML 规范的一部分。

```html
<embed src="audi.jpeg">
```

​		请注意，`<embed>` 元素<u>没有结束标记</u>。它无法包含替代文本。

​		`<embed>` 元素也可用于在 HTML 中包含 HTML：

```html
<embed width="100%" height="500px" src="snippet.html">
```

---

---

---

## 音频

### 	问题，问题，以及解决方法

​		在 HTML 中播放音频并不容易！

​		您需要谙熟大量技巧，以确保您的音频文件在所有浏览器中（Internet Explorer, Chrome, Firefox, Safari, Opera）和		所有硬件上（PC, Mac , iPad, iPhone）都能够播放。

---

### 	使用插件

​		浏览器插件是一种扩展浏览器标准功能的小型计算机程序。

​		插件有很多用途：播放音乐、显示地图、验证银行账号，控制输入等等。

​		可使用 `<object>` 或 `<embed>` 标签来将插件添加到 HTML 页面。

​		这些标签定义资源（通常非 HTML 资源）的容器，根据类型，它们即会由浏览器显示，也会由外部插件显示。

---

### 	使用 `<embed>` 元素

​		`<embed>` 标签定义外部（非 HTML）内容的容器。（这是一个 HTML5 标签，在 HTML4 中是非法的，但是所有浏览		器中都有效）。

​		下面的代码片段能够显示嵌入网页中的 MP3 文件：

```html
<embed height="100" width="100" src="song.mp3" />
```

![image-20231128222107947](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128222107947.png)

#### 问题：

- `<embed>` 标签在 <u>HTML 4 中是无效的</u>。页面无法通过 HTML 4 验证。
- 不同的浏览器对音频格式的支持也不同。
- 如果浏览器不支持该文件格式，没有插件的话就无法播放该音频。
- 如果用户的计算机未安装插件，无法播放音频。
- 如果把该文件转换为其他格式，仍然无法在所有浏览器中播放。

​			**注释：**使用 `<!DOCTYPE html>` (HTML5) 解决验证问题。

---

### 	使用 `<object>` 元素

​		`<object tag>` 标签也可以定义外部（非 HTML）内容的容器。

​		下面的代码片段能够显示嵌入网页中的 MP3 文件：

```html
<object height="100" width="100" data="song.mp3"></object>
```

#### 	问题：

- 不同的浏览器对音频格式的支持也不同。
- 如果浏览器不支持该文件格式，没有插件的话就无法播放该音频。
- 如果用户的计算机未安装插件，无法播放音频。
- 如果把该文件转换为其他格式，仍然无法在所有浏览器中播放。

---

### 	使用 HTML5 `<audio>` 元素

​		`<audio> 元素是一个 HTML5 元素，在 HTML 4 中是非法的，但在所有浏览器中都有效。`

```
<audio controls="controls">
  <source src="song.mp3" type="audio/mp3" />
  <source src="song.ogg" type="audio/ogg" />
Your browser does not support this audio format.
</audio>
```

#### 		问题：

- `<audio>` 标签在 HTML 4 中是无效的。您的页面无法通过 HTML 4 验证。
- 您必须把音频文件转换为不同的格式。
- `<audio> 元素在老式浏览器中不起作用。`

---

### 	最好的 HTML 解决方法

```
<audio controls="controls" height="100" width="100">
  <source src="song.mp3" type="audio/mp3" />
  <source src="song.ogg" type="audio/ogg" />
<embed height="100" width="100" src="song.mp3" />
</audio>
```

![image-20231128222553940](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128222553940.png)

​	上面的例子使用了两个不同的音频格式。HTML5 `<audio>` 元素会尝试以 mp3 或 ogg 来播放音频。如果失败，代码将		回退尝试 `<embed>` 元素。

#### 	问题：

- 您必须把音频转换为不同的格式。

- `<audio>` 元素无法通过 HTML 4 和 XHTML 验证。

- <embed> 元素无法通过 HTML 4 和 XHTML 验证。

- `<embed>` 元素无法回退来显示错误消息。

---

### 	向网站添加音频的最简单方法

​		向网页添加音频的最简单的方法是什么？

​		<u>雅虎的媒体播放器绝对算其中之一。</u>

​		使用雅虎媒体播放器是一个不同的途径。您只需简单地让雅虎来完成歌曲播放的工作就好了。

​		它能播放 mp3 以及一系列其他格式。通过一行简单的代码，您就可以把它添加到网页中，轻松地将 HTML 页面转变		为专业的播放列表。

#### 		**雅虎媒体播放器**

```
<a href="song.mp3">Play Sound</a>
<script type="text/javascript" src="http://mediaplayer.yahoo.com/js">
</script>](https://www.w3school.com.cn/tiy/t.asp?f=eg_html_audio_yahoo)
```

​		使用雅虎播放器是免费的。如需使用它，您需要把这段 JavaScript 插入网页底部：

```
<script type="text/javascript" src="http://mediaplayer.yahoo.com/js"></script>
```

​		然后只需简单地把 MP3 文件链接到您的 HTML 中，JavaScript 会自动地为每首歌创建播放按钮：

```
<a href="song1.mp3">Play Song 1</a>
<a href="song2.mp3">Play Song 2</a>
...
...
...
```

![image-20231128223047048](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128223047048.png)		

​		雅虎媒体播放器为您的用户提供的是一个小型的播放按钮，而不是完整的播放器。不过，当您点击该按钮，会弹出完		整的播放器。

​		请注意，这个播放器始终停靠在窗框底部。只需点击它，就可将其滑出。

#### 	使用超链接

​		如果网页包含指向媒体文件的超链接，大多数浏览器会使用“辅助应用程序”来播放文件。

​		以下代码片段显示指向 mp3 文件的链接。如果用户点击该链接，浏览器会启动“辅助应用程序”来播放该文件：

```
<a href="song.mp3">Play the sound</a>
```

---

### 	内联的声音

​		当您在网页中包含声音，或者<u>作为网页的组成部分</u>时，它被称为内联声音。

​		如果您打算在 web 应用程序中使用内联声音，您需要意识到很多人都觉得内联声音令人恼火。同时请注意，用户可能		已经关闭了浏览器中的内联声音选项。

​		我们最好的建议是只在用户希望听到内联声音的地方包含它们。一个正面的例子是，在用户需要听到录音并点击某个		链接时，会打开页面然后播放录音。

---

---

---

## 视频

​	**在 HTML 中播放视频的方法有很多种。**

```html
<video width="320" height="240" controls="controls">
  <source src="movie.mp4" type="video/mp4" />
  <source src="movie.ogg" type="video/ogg" />
  <source src="movie.webm" type="video/webm" />
  <object data="movie.mp4" width="320" height="240">
    <embed src="movie.swf" width="320" height="240" />
  </object>
</video>
```

---

### 	使用 `<embed>` 标签

​		`<embed>` 标签的作用是在 HTML 页面中嵌入多媒体元素。

​		下面的 HTML 代码显示嵌入网页的 Flash 视频：

```
<embed src="movie.swf" height="200" width="200"/>
```

![image-20231128223452390](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128223452390.png)

#### 问题

- HTML4 无法识别 <embed> 标签。您的页面无法通过验证。
- 如果浏览器不支持 Flash，那么视频将无法播放
- iPad 和 iPhone 不能显示 Flash 视频。
- 如果您将视频转换为其他格式，那么它仍然不能在所有浏览器中播放。

---

### 使用 `<object>` 标签

​		`<object>` 标签的作用是在 HTML 页面中嵌入多媒体元素。

​		下面的 HTML 片段显示嵌入网页的一段 Flash 视频：

```
<object data="movie.swf" height="200" width="200"/>
```

---

​	使用 <video> 标签

​		`<video>` 是 HTML 5 中的新标签。

​		`<video>` 标签的作用是在 HTML 页面中嵌入视频元素。

​		以下 HTML 片段会显示一段嵌入网页的 ogg、mp4 或 webm 格式的视频：

```
<video width="320" height="240" controls="controls">
  <source src="movie.mp4" type="video/mp4" />
  <source src="movie.ogg" type="video/ogg" />
  <source src="movie.webm" type="video/webm" />
Your browser does not support the video tag.
</video>
```

![image-20231128223710706](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231128223710706.png)

---

### 	最好的 HTML 解决方法

#### 		HTML 5 + `<object> + <embed>`

```
<video width="320" height="240" controls="controls">
  <source src="movie.mp4" type="video/mp4" />
  <source src="movie.ogg" type="video/ogg" />
  <source src="movie.webm" type="video/webm" />
  <object data="movie.mp4" width="320" height="240">
    <embed src="movie.swf" width="320" height="240" />
  </object>
</video>
```

---

#### 	使用超链接

​		如果网页包含指向媒体文件的超链接，大多数浏览器会使用“辅助应用程序”来播放文件。

​		以下代码片段显示指向 AVI 文件的链接。如果用户点击该链接，浏览器会启动“辅助应用程序”，比如 Windows Media 		Player 来播放这个 AVI 文件：

```
<a href="movie.swf">Play a video file</a>
```

---

### 	关于内联视频的一段注释

​		当视频被包含在网页中时，它被称为内联视频。

​		如果您打算在 web 应用程序中使用内联视频，您需要意识到很多人都觉得内联视频令人恼火。

​		同时请注意，用户可能已经关闭了浏览器中的内联视频选项。

​		我们最好的建议是只在用户希望看到内联视频的地方包含它们。一个正面的例子是，在用户需要看到视频并点击某个		链接时，会打开页面然后播放视频。

---

---

---

## YouTube 视频

​	 **HTML 中包含视频的最简单的方法是，使用 YouTube。**

### 	YouTube Video Id

​		保存（或播放）视频时，YouTube 会显示一个 id（例如 ih1l6wb7LhU）。

​		您可以使用这个 id，并在 HTML 代码中引用您的视频。

---

### 	在 HTML 中保费 YouTube 视频

​		如需在网页上播放视频，请执行以下操作：

- 将视频上传到 YouTube
- 记下视频 id
- 在您的网页中定义 `<iframe>` 元素
- 让 `src` 属性指向视频的 URL
- 使用 `width` 和 `height` 属性来规定播放器的尺寸
- 向 URL 添加其他参数（参阅下文）

```
<iframe width="420" height="315"
src="https://www.youtube.com/embed/ih1l6wb7LhU">
</iframe>
```

![image-20231129164430879](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129164430879.png)

(需科学上网)

---

### 	YouTube Autoplay + Mute

​		您可以通过在 YouTube URL 上添加 autoplay=1 来让视频在用户访问页面时自		动开始播放。但是，自动开始播放视频会让您的访问者感到烦恼！

​		**注意：**在大多数情况下，Chromium 浏览器都不允许自动播放。但始终允			许静音自动播放。

​		在 `autoplay=1` 之后添加 `mute=1`，可让您的视频自动开始播放（但已静			音）。

#### 	YouTube - Autoplay + Muted

```
<iframe width="420" height="315"
src="https://www.youtube.com/embed/ih1l6wb7LhU?autoplay=1&mute=1">
</iframe>
```

---

### 	YouTube Loop

​		添加 `loop=1` 会让您的视频永远循环。

​		值 0（默认）：视频将播放一次。

​		值 1：视频将循环（永远）。

​		YouTube - Loop

```
<iframe width="420" height="315"
src="https://www.youtube.com/embed/ih1l6wb7LhU?playlist=ih1l6wb7LhU&loop=1">
</iframe>
```

---

### 	YouTube Controls

​		添加 `controls=0` 会使视频播放器不显示控件。

​		值 0：播放器控件不显示。

​		值 1（默认）：播放器控件显示。

​		YouTube - Controls

```
<iframe width="420" height="315"
src="https://www.youtube.com/embed/ih1l6wb7LhU?controls=0">
</iframe>
```

![image-20231129165151257](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129165151257.png)

---

---

---

# HTML5 简介

## 	什么是 HTML5？

​		HTML5 是最新的 HTML 标准。

​		HTML5 是专门为承载丰富的 web 内容而设计的，并且无需额外插件。

​		HTML5 拥有新的语义、图形以及多媒体元素。

​		HTML5 提供的新元素和新的 API 简化了 web 应用程序的搭建。

​		HTML5 是跨平台的，被设计为在不同类型的硬件（PC、平板、手机、电视机		等等）之上运行。

​		**注释：**在下面的章节中，您将学到如何“帮助”老版本的浏览器处理 						HTML5。

---

### 	HTML5 中的新内容？

​		HTML5 的新的文档类型（DOCTYPE）声明非常简单：

```
<!DOCTYPE html>
The new character encoding (charset) declaration is also very simple:

<meta charset="UTF-8">
```

---

### 	HTML5 - 新的属性语法

​	HTML5 标准允许 4 种不同的属性语法。

​	本例演示在 `<input>` 标签中使用的不同语法：

| 类型          | 示例                                              |
| :------------ | :------------------------------------------------ |
| Empty         | `<input type="text" value="Bill Gates" disabled>` |
| Unquoted      | `<input type="text" value=Bill Gates>`            |
| Double-quoted | `<input type="text" value="Bill Gates">`          |
| Single-quoted | `<input type="text" value='Bill Gates'>`          |

在 HTML5 标准中，根据对属性的需求，可能会用到所有 4 种语法。

---

### 	HTML5 - 新特性

​		HTML5 的一些最有趣的新特性：

- 新的语义元素，比如 `<header>, <footer>, <article>`, and `<section>`。
- 新的表单控件，比如数字、日期、时间、日历和滑块。
- 强大的图像支持（借由 `<canvas> 和 <svg>`）
- 强大的多媒体支持（借由 `<video> 和 <audio>`）
- 强大的新 API，比如用本地存储取代 cookie。

---

### 	HTML5 - 被删元素

​		以下 HTML 4.01 元素已从 HTML5 中删除：

- `<acronym>`
- `<applet>`
- `<basefont>`
- `<big>`
- `<center>`
- `<dir>`
- `<font>`
- `<frame>`
- `<frameset>`
- `<noframes>`
- `<strike>`
- `<tt>`

---

---

---

## 	浏览器支持

### 	HTML5 浏览器支持

​		所有现代浏览器都支持 HTML5。

​		此外，所有浏览器，不论新旧，都会自动把未识别元素当做行内元素来处理。

​		正因如此，您可以帮助老式浏览器处理”未知的“ HTML 元素。

​		**注释：**您甚至可以教授石器时代的 IE6 如何处理未知的 HTML 元素。

---

### 	把 HTML5 元素定义为块级元素

​		HTML5 定义了八个新的*语义* HTML 元素。所有都是*块级*元素。

​		您可以把 CSS *display* 属性设置为 *block*，以确保老式浏览器中正确的行为：

```html
header, section, footer, aside, nav, main, article, figure {
    display: block; 
}
```

---

### 	向 HTML 添加新元素

​		您可以通过浏览器 trick 向 HTML 添加任何新元素：

​		本例向 HTML 添加了一个名为 `<myHero>` 的新元素，并为其定义 display 样		式：

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129170754833.png" alt="image-20231129170754833" style="zoom: 67%;" />

---

### 	Internet Explorer 的问题

​		上述方案可用于所有新的 HTML5 元素，但是：

​		**注意：**Internet Explorer 8 以及更早的版本，不允许对未知元素添加样式。

​		幸运的是，Sjoerd Visscher 创造了 "HTML5 Enabling JavaScript", *"the shiv"*：

```
<!--[if lt IE 9]>
  <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
<![endif]-->
```

---

### 	完整的 Shiv 解决方案

![image-20231129170914554](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129170914554.png)

引用 shiv 代码的链接必须位于 `<head>` 元素中，因为 Internet Explorer 需要在读取之前认识所有新元素。

---

### 	HTML5 Skeleton

​		https://www.w3school.com.cn/tiy/t.asp?f=eg_html5_html5_skeleton

​		注释：跳转查看详细代码

---

---

---

## 新元素

### 	新的语义/结构元素

​		HTML5 提供的新元素可以构建更好的文档结构：

|      标签      | 描述                                                   |
| :------------: | :----------------------------------------------------- |
|  `<article>`   | `定义文档内的文章。`                                   |
|   `<aside>`    | `定义页面内容之外的内容。`                             |
|    `<bdi>`     | `定义与其他文本不同的文本方向。`                       |
|  `<details>`   | `定义用户可查看或隐藏的额外细节。`                     |
|   `<dialog>`   | `定义对话框或窗口。`                                   |
| `<figcaption>` | `定义 <figure> 元素的标题。`                           |
|   `<figure>`   | `定义自包含内容，比如图示、图表、照片、代码清单等等。` |
|   `<footer>`   | `定义文档或节的页脚。`                                 |
|   `<header>`   | `定义文档或节的页眉。`                                 |
|    `<main>`    | `定义文档的主内容。`                                   |
|    `<mark>`    | `定义重要或强调的内容。`                               |
|  `<menuitem>`  | `定义用户能够从弹出菜单调用的命令/菜单项目。`          |
|   `<meter>`    | `定义已知范围（尺度）内的标量测量。`                   |
|    `<nav>`     | `定义文档内的导航链接。`                               |
|  `<progress>`  | `定义任务进度。`                                       |
|     `<rp>`     | `定义在不支持 ruby 注释的浏览器中显示什么。`           |
|     `<rt>`     | `定义关于字符的解释/发音（用于东亚字体）。`            |
|    `<ruby>`    | `定义 ruby 注释（用于东亚字体）。`                     |
|  `<section>`   | `定义文档中的节。`                                     |
|  `<summary>`   | `定义 <details> 元素的可见标题。`                      |
|    `<time>`    | `定义日期/时间。`                                      |
|    `<wbr>`     | `定义可能的折行（line-break）。`                       |

---

### 	新的表单元素

|     标签     | 描述                               |
| :----------: | :--------------------------------- |
| `<datalist>` | `定义输入控件的预定义选项。`       |
|  `<keygen>`  | `定义键对生成器字段（用于表单）。` |
|  `<output>`  | `定义计算结果。`                   |

---

### 	新的输入类型

| 新的输入类型   | 新的输入属性     |
| :------------- | :--------------- |
| color          | autocomplete     |
| date           | autofocus        |
| datetime       | form             |
| datetime-local | formfocus        |
| email          | formaction       |
| month          | formentype       |
| range          | formmenthod      |
| search         | formnovalidate   |
| tel            | height and width |
| time           | list             |
| url            | min and max      |
| week           | multiple         |
|                | pattern          |
|                | placeholder      |
|                | required         |
|                | step             |

---

### 	HTML5 - 新的属性语法

​		HTML5 允许四种不同的属性语法。

​		该例演示 `<input>` 标签中使用的不同语法：

| 标签          | 描述                                              |
| :------------ | :------------------------------------------------ |
| Empty         | `<input type="text" value="Bill Gates" disabled>` |
| Unquoted      | `<input type="text" value=Bill>`                  |
| Double-quoted | `<input type="text" value="Bill Gates">`          |
| Single-quoted | `<input type="text" value='Bill Gates'>`          |

​		在 HTML5 中，根据属性所需，可能会使用所有这四种语法。

---

### 	HTML5 图像

|    标签    | 描述                             |
| :--------: | :------------------------------- |
| `<canvas>` | 定义使用 JavaScript 的图像绘制。 |
|  `<svg>`   | 定义使用 SVG 的图像绘制。        |

---

### 	新的媒介元素

| 标签       | 描述                                   |
| :--------- | :------------------------------------- |
| `<audio>`  | `定义声音或音乐内容。`                 |
| `<embed>`  | `定义外部应用程序的容器（比如插件）。` |
| `<source>` | `定义 <video> 和 <audio> 的来源。`     |
| `<track>`  | `定义 <video> 和 <audio> 的轨道。`     |
| `<video>`  | `定义视频或影片内容。`                 |

---

---

---

## 迁移

### 	从 HTML4 迁移至 HTML5

​		本章讲解如何从一张典型的 HTML4 页面迁移至典型的 HTML5。

​		本章演示如何把一张已有的 HTML4 页面转换为 HTML5 页面，在不破坏如何		原始内容和结构的情况下。

​		**注释：**您可以使用相同的技巧从 HTML4 以及 XHTML 迁移至 HTML5。

|     典型的 HTML4     | 典型的 HTML5 |
| :------------------: | :----------: |
| `<div id="header">`  |  `<header>`  |
|  `<div id="menu">`   |   `<nav>`    |
| `<div id="content">` | `<section>`  |
|  `<div id="post">`   | `<article>`  |
| `<div id="footer">`  |  `<footer>`  |

---

### 	更改为 HTML5 Doctype

​		修改文档类型，从 HTML4 doctype：

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
"http://www.w3.org/TR/html4/loose.dtd">
```

​		修改为 HTML5 doctype：

```
<!DOCTYPE html>
```

---

### 	更改为 HTML5 编码

​		修改编码信息，从 HTML4：

```
<meta http-equiv="Content-Type" content="text/html;charset=utf-8">
```

​		改为 HTML5：

```
<meta charset="utf-8">
```

---

### 	添加 shiv

​		所有现代浏览器都支持 HTML5 语义元素。

​		此外，您可以“教授”老式浏览器如何处理“未知元素”。

​		为 Internet Explorer 支持而添加的 shiv：

```html
<!--[if lt IE 9]>
  <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
<![endif]-->
```

---

### 	更改为 HTML5 `<header> 和 <footer>`

​		把 id="header" 和 id="footer" 的 `<div>` 元素：

---

### 	更改为 HTML5 `<nav>`

​		把 id="menu" 的 `<div>` 元素：

---

### 	更改为 HTML5 `<section>`

​		把 id="content" 的 the `<div>` 元素：

---

### 	更改为 HTML5 `<article>`

​		把 class="post" 的所有 `<div>` 元素：

---

### 	典型的 HTML5 页面

​		最后您可以删除 `<head>` 标签。HTML5 中不再需要它们：

---

### 	`<article> <section> 与 <div>` 之间的差异

​		在 HTML5 标准中，`<article> <section> 与 <div>` 之间的差异很小，令		人困惑。

​		在 HTML5 标准中，`<section>` 元素被定位为相关元素的块。

​		`<article>` 元素被定义为相关元素的完整的自包含块。

​		`<div>` 元素被定义为子元素的块。

---

---

---

# HTML API

## 地理定位

​	**HTML5 Geolocation（地理定位）用于定位用户的位置。**

### 	定位用户的位置

​		HTML5 Geolocation API 用于获得用户的地理位置。

​		鉴于该特性可能侵犯用户的隐私，除非用户同意，否则用户位置信息是不可用		的。

---

### 	HTML5 - 使用地理定位

​		请使用 getCurrentPosition() 方法来获得用户的位置。

​		下例是一个简单的地理定位实例，可返回用户位置的经度和纬度。

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129173558831.png" alt="image-20231129173558831" style="zoom: 50%;" />

​		例子解释：

- 检测是否支持地理定位
- 如果支持，则运行 getCurrentPosition() 方法。如果不支持，则向用户显示一段消息。
- 如果getCurrentPosition()运行成功，则向参数showPosition中规定的函数返回一个coordinates对象
- showPosition() 函数获得并显示经度和纬度

---

### 	处理错误和拒绝

​		getCurrentPosition() 方法的第二个参数用于处理错误。它规定当获取用户位		置失败时运行的函数：

```
function showError(error)
  {
  switch(error.code)
    {
    case error.PERMISSION_DENIED:
      x.innerHTML="User denied the request for Geolocation."
      break;
    case error.POSITION_UNAVAILABLE:
      x.innerHTML="Location information is unavailable."
      break;
    case error.TIMEOUT:
      x.innerHTML="The request to get user location timed out."
      break;
    case error.UNKNOWN_ERROR:
      x.innerHTML="An unknown error occurred."
      break;
    }
  }
```

​		错误代码：

- Permission denied - 用户不允许地理定位
- Position unavailable - 无法获取当前位置
- Timeout - 操作超时

---

### 	在地图中显示结果

​		如需在地图中显示结果，您需要访问可使用经纬度的地图服务，比如谷歌地图		或百度地图：

```html
function showPosition(position)
{
var latlon=position.coords.latitude+","+position.coords.longitude;

var img_url="http://maps.googleapis.com/maps/api/staticmap?center="
+latlon+"&zoom=14&size=400x300&sensor=false";

document.getElementById("mapholder").innerHTML="<img src='"+img_url+"' />";
}
```

---

### 	给定位置的信息

​		本页演示的是如何在地图上显示用户的位置。不过，地理定位对于给定位置的		信息同样很有用处。

- 更新本地信息
- 显示用户周围的兴趣点
- 交互式车载导航系统 (GPS)

---

### 	getCurrentPosition() 方法 - 返回数据

​		若成功，则 getCurrentPosition() 方法返回对象。始终会返回 latitude、			longitude 以及 accuracy 属性。如果可用，则会返回其他下面的属性。

|          属性           | 描述                   |
| :---------------------: | :--------------------- |
|     coords.latitude     | 十进制数的纬度         |
|    coords.longitude     | 十进制数的经度         |
|     coords.accuracy     | 位置精度               |
|     coords.altitude     | 海拔，海平面以上以米计 |
| coords.altitudeAccuracy | 位置的海拔精度         |
|     coords.heading      | 方向，从正北开始以度计 |
|      coords.speed       | 速度，以米/每秒计      |
|        timestamp        | 响应的日期/时间        |

---

---

---

## 拖放

​	拖放（Drag ,Drop)是很常见的特性。它指的是您抓取某物并拖入不同的位置。

​	拖放是 HTML5 标准的组成部分：任何元素都是可拖放的。

---

### 	拖放实例

![image-20231129174608543](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129174608543.png)

---

#### **看上去有点复杂，不过让我们研究一下拖放事件的所有不同部分**

---

### 	把元素设置为可拖放

​		首先：为了把一个元素设置为可拖放，请把 draggable 属性设置为 true：

```html
<img draggable="true">
```

---



### 	拖放的内容 - ondragstart 和 setData()

​		然后，规定当元素被拖动时发生的事情。

​		在上面的例子中，ondragstart 属性调用了一个 drag(event) 函数，规定拖动什		么数据。

​		dataTransfer.setData() 方法设置被拖动数据的数据类型和值：

```html
function drag(ev) {
    ev.dataTransfer.setData("text", ev.target.id);
}
```

---

### 	拖到何处 - ondragover

​		ondragover 事件规定被拖动的数据能够被放置到何处。

​		默认地，数据/元素无法被放置到其他元素中。为了实现拖放，我们必须阻止		元素的这种默认的处理方式。

​		这个任务由 ondragover 事件的 event.preventDefault() 方法完成：

```
event.preventDefault()
```

---

### 	进行放置 - ondrop

​		当放开被拖数据时，会发生 drop 事件。

​		在上面的例子中，ondrop 属性调用了一个函数，drop(event)：

```html
function drop(ev) {
    ev.preventDefault();
    var data = ev.dataTransfer.getData("text");
    ev.target.appendChild(document.getElementById(data));
}
```

​		代码解释：

- 调用 preventDefault() 来阻止数据的浏览器默认处理方式（drop 事件的默认行为是以链接形式打开）
- 通过 dataTransfer.getData() 方法获得被拖的数据。该方法将返回在 setData() 方法中设置为相同类型的任何数据
- 被拖数据是被拖元素的 id ("drag1")
- 把被拖元素追加到放置元素中

---

### 	更多实例

​		来回拖放图片

​		如何在两个 `<div>` 元素之间来回拖放图像：

![image-20231129175314411](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129175314411.png)

---

---

---

## 本地存储

​	**HTML 本地存储：优于 cookies。**

### 	什么是 HTML 本地存储？

​		通过本地存储（Local Storage），web 应用程序能够在用户浏览器中对数据进行本地的存储。

​		在 HTML5 之前，应用程序数据只能存储在 cookie 中，包括每个服务器请求。本地存储则更安全，并且可在不影响网站性能的前提下将大量数据存储于本地。

​		与 cookie 不同，存储限制要大得多（至少5MB），并且信息不会被传输到服务器。

​		本地存储经由起源地（origin）（经由域和协议）。所有页面，从起源地，能够存储和访问相同的数据。

---

### 	本地存储对象

​		HTML 本地存储提供了两个在客户端存储数据的对象：

- window.localStorage - 存储没有截止日期的数据
- window.sessionStorage - 针对一个 session 来存储数据（当关闭浏览器标签页时数据会丢失）

​		在使用本地存储时，请检测 localStorage 和 sessionStorage 的浏览器支持：

```
if (typeof(Storage) !== "undefined") {
    // 针对 localStorage/sessionStorage 的代码
} else {
    // 抱歉！不支持 Web Storage ..
}
```

---

### 	localStorage 对象

​		localStorage 对象存储的是没有截止日期的数据。当浏览器被关闭时数据不会		被删除，在下一天、周或年中，都是可用的。

```
// 存储
localStorage.setItem("lastname", "Gates");
// 取回
document.getElementById("result").innerHTML = localStorage.getItem("lastname");
```

#### 	实例解释：

- 创建 localStorage 名称/值对，其中：name="lastname"，value="Gates"
- 取回 "lastname" 的值，并把它插到 id="result" 的元素中

#### 	删除 "lastname" localStorage 项目的语法如下：

```
localStorage.removeItem("lastname");
```

​		下面的例子对用户点击按钮的次数进行计数。在代码中，值字符串被转换为数		值，依次对计数进行递增：

#### 	实例

```
if (localStorage.clickcount) {
    localStorage.clickcount = Number(localStorage.clickcount) + 1;
} else {
    localStorage.clickcount = 1;
}
document.getElementById("result").innerHTML = "您已经点击这个按钮 " +
localStorage.clickcount + " 次。";
```

---

### 	sessionStorage 对象

​		sessionStorage 对象等同 localStorage 对象，不同之处在于只对一个 session 		存储数据。如果用户关闭具体的浏览器标签页，数据也会被删除。

​		下例在当前 session 中对用户点击按钮进行计数：

#### 	实例

```
if (sessionStorage.clickcount) {
    sessionStorage.clickcount = Number(sessionStorage.clickcount) + 1;
} else {
    sessionStorage.clickcount = 1;
}
document.getElementById("result").innerHTML = "在本 session 中，您已经点击这个按钮 " +
sessionStorage.clickcount + " 次。";
```

---

## 应用程序缓存

​		**使用应用程序缓存，通过创建 cache manifest 文件，可轻松创建 web 应    用的离线版本。**

### 	什么是应用程序缓存？

​		HTML5 引入了应用程序缓存（Application Cache），这意味着可对 web 应用		进行缓存，并可在没有因特网连接时进行访问。

​		应用程序缓存为应用带来三个优势：

1. 离线浏览 - 用户可在应用离线时使用它们
2. 速度 - 已缓存资源加载得更快
3. 减少服务器负载 - 浏览器将只从服务器下载更新过或更改过的资源

---

### 	HTML Cache Manifest 实例

​	下例展示了带有 cache manifest 的 HTML 文档（<u>**供离线浏览**</u>）：

#### 		实例

```
<!DOCTYPE HTML>
<html manifest="demo.appcache">
<body>
文档内容 ......
</body>
</html>
```

---

### 	Cache Manifest 基础

​		如需启用应用程序缓存，请在文档的 <html> 标签中包含 manifest 属性：

```
<!DOCTYPE HTML>
<html manifest="demo.appcache">
...
</html>
```

​		每个指定了 manifest 的页面在用户对其访问时都会被缓存。如果未指定 			manifest 属性，则页面不会被缓存（除非在 manifest 文件中直接指定了该		页面）。

​		manifest 文件的建议文件扩展名是：".appcache"。

​		**注意：**manifest 文件需要设置正确的 MIME-type，即 "text/cache-						manifest"。必须在 web 服务器上进行配置。

---

### 	Manifest 文件

​		manifest 文件是简单的文本文件，它告知浏览器被缓存的内容（以及不缓存的		内容）。

​		manifest 文件有三个部分：

- CACHE MANIFEST - 在此标题下列出的文件将在首次下载后进行缓存
- NETWORK - 在此标题下列出的文件需要与服务器的连接，且不会被缓存
- FALLBACK - 在此标题下列出的文件规定当页面无法访问时的回退页面（比如 404 页面)

---

### 	CACHE MANIFEST

​		第一行，CACHE MANIFEST，是必需的：

```
CACHE MANIFEST
/theme.css
/logo.gif
/main.js
```

​		上面的 manifest 文件列出了三个资源：一个 CSS 文件，一个 GIF 图像，以及		一个 JavaScript 文件。当 manifest 文件被加载后，浏览器会从网站的根目录		下载这三个文件。然后，无论用户何时与因特网断开连接，这些资源依然可		用。

---

### 	NETWORK

​		下面的 NETWORK 部分规定文件 "login.php" 永远不会被缓存，且离线时是不		可用的：

```
NETWORK:
login.asp
```

​		可以使用星号来指示所有其他其他资源/文件都需要因特网连接：

```
NETWORK:
*

FALLBACK
```

​		下面的 FALLBACK 部分规定如果无法建立因特网连接，则用 "offline.html" 替		代 /html/ 目录中的所有文件：

```
FALLBACK:
/html/ /offline.html
```

​		**注释：**第一个 URI 是资源，第二个是替补。

---

### 	更新缓存

​		一旦应用被缓存，它就会保持缓存直到发生下列情况：

- 用户清空浏览器缓存
- manifest 文件被修改（参阅下面的提示）
- 由程序来更新应用缓存

---

### 	实例 - 完整的 Cache Manifest 文件

```
CACHE MANIFEST
# 2012-02-21 v1.0.0
/theme.css
/logo.gif
/main.js

NETWORK:
login.asp

FALLBACK:
/html/ /offline.html
```

​		**提示：**以 "#" 开头的是注释行，但也可满足其他用途。应用的缓存只会在			其 manifest 文件改变时被更新。如果您编辑了一幅图像，或者修改了一个 			JavaScript 函数，这些改变都不会被重新缓存。更新注释行中的日期和版本			号是一种使浏览器重新缓存文件的办法。

---

### 	关于应用程序缓存的注意事项

​		请留心缓存的内容。

​		一旦文件被缓存，则浏览器会继续展示已缓存的版本，即使您修改了服务器上		的文件。为了确保浏览器更新缓存，您需要更新 manifest 文件。

​		**注释：**浏览器对缓存数据的容量限制可能不太一样（某些浏览器的限制是每个					站点 5MB）。

---

---

---

## Web Workers

​	**Web worker 是运行在后台的 JavaScript，不会影响页面的性能。**

### 	什么是 Web Worker？

​		当在 HTML 页面中执行脚本时，页面是不可响应的，直到脚本已完成。

​		Web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性		能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web 			worker 运行在后台。

---

### 	HTML Web Workers 实例

​		下面的例子创建了一个简单的 web worker，在后台计数：

​		计数：

​		启动 Worker 停止 Worker

![image-20231129180945506](C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129180945506.png)

---

### 	检测 Web Worker 支持

​		在创建 web worker 之前，请检测用户浏览器是否支持它：

```
if (typeof(Worker) !== "undefined") {
    // 是的！支持 Web worker！
    // 一些代码.....
} else {
    // 抱歉！不支持 Web Worker！
}
```

---

### 	创建 Web Worker 文件

​		现在，让我们在一个外部 JavaScript 文件中创建我们的 web worker。

​		在此处，我们创建了计数脚本。该脚本存储于 "demo_workers.js" 文件中：

```
var i = 0;

function timedCount() {
    i = i + 1;
    postMessage(i);
    setTimeout("timedCount()",500);
}

timedCount();
```

​		以上代码中重要的部分是 postMessage() 方法 - 它用于向 HTML 页面传回一段		消息。

​		**注释:** web worker 通常不用于如此简单的脚本，而是用于更耗费 CPU 资源			的任务。

---

### 	创建 Web Worker 对象

​		现在我们已经有了 web worker 文件，我们需要从 HTML 页面调用它。

​		下面的代码行检测是否存在 worker，如果不存在，- 它会创建一个新的 web 		worker 对象，然后运行 "demo_workers.js" 中的代码：

```
if (typeof(w) == "undefined") {
    w = new Worker("demo_workers.js");
}
```

​		然后我们就可以从 web worker 发生和接收消息了。

​		向 web worker 添加一个 "onmessage" 事件监听器：

```
w.onmessage = function(event){
    document.getElementById("result").innerHTML = event.data;
};
```

​		当 web worker 传送消息时，会执行事件监听器中的代码。来自 web worker 的		数据会存储于 event.data 中。

---

### 	终止 Web Worker

​		当创建 web worker 后，它会继续监听消息（即使在外部脚本完成后）直到其		被终止为止。

​		如需终止 web worker，并释放浏览器/计算机资源，请使用 terminate() 方法：

```
w.terminate();
```

---

### 	复用 Web Worker

​		如果您把 worker 变量设置为 undefined，在其被终止后，可以重复使用该代		码：

```
w = undefined;
```

---

### 	Web Worker 和 DOM

​		由于 web worker 位于外部文件中，它们无法访问下例 JavaScript 对象：

- window 对象
- document 对象
- parent 对象

---

---

---

## Server-Sent 事件

​	**Server-Sent 事件允许网页从服务器获得更新。**

### 	Server-Sent 事件 - One Way Messaging

​		Server-Sent 事件指的是网页自动从服务器获得更新。

​		以前也可能做到这一点，前提是网页不得不询问是否有可用的更新。通过 			Server-Sent 事件，更新能够自动到达。

​		例如：Facebook/Twitter 更新、股价更新、新的博文、赛事结果，等等。

---

### 	接收 Server-Sent 事件通知

​		EventSource 对象用于接收服务器发送事件通知：

```
var source = new EventSource("demo_sse.php");
source.onmessage = function(event) {
    document.getElementById("result").innerHTML += event.data + "<br>";
};
```

​		例子解释：

- 创建一个新的 EventSource 对象，然后规定发送更新的页面的 URL（本例中是 "demo_sse.php"）
- 每当接收到一次更新，就会发生 onmessage 事件
- 当 onmessage 事件发生时，把已接收的数据推入 id 为 "result" 的元素中

---

### 	检测 Server-Sent 事件支持

​		在 TIY 实例中，我们编写了一段额外的代码来检测服务器发送事件的浏览器支		持：

```
if(typeof(EventSource) !== "undefined") {
    // 是的！支持服务器发送事件！
    // 一些代码.....
} else {
    // 抱歉！不支持服务器发送事件！
}
```

---

### 	服务器端代码实例

​		为了使上例运行，您需要能够发送数据更新的服务器（比如 PHP 或 ASP）。

​		服务器端事件流的语法非常简单。请把 "Content-Type" 报头设置为 					"text/event-stream"。现在，您可以开始发送事件流了。

#### 		PHP 中的代码 (demo_sse.php)：

```
<?php
header('Content-Type: text/event-stream');
header('Cache-Control: no-cache');

$time = date('r');
echo "data: The server time is: {$time}\n\n";
flush();
?>
```

#### 		ASP 中的代码 (VB) (demo_sse.asp)：

```
<%
Response.ContentType = "text/event-stream"
Response.Expires = -1
Response.Write("data: The server time is: " & now())
Response.Flush()
%>
```

#### 		代码解释：

- 把报头 "Content-Type" 设置为 "text/event-stream"
- 规定不对页面进行缓存
- 输出要发送的日期（始终以 "data: " 开头）
- 向网页刷新输出数据

---

### 	EventSource 对象

在上例中，我们使用 onmessage 事件来获取消息。不过还可以使用其他事件：

|   事件    | 描述                     |
| :-------: | :----------------------- |
|  onopen   | 当通往服务器的连接被打开 |
| onmessage | 当接收到消息             |
|  onerror  | 当发生错误               |

---

---

---



<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20231129182105223.png" alt="image-20231129182105223" style="zoom:50%;" />





