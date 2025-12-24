# 简介

##  `<script>`

​	在HTML中，JavaScript代码必须位于`<script>`与`</script>`之间

##  函数与事件

​	JavaScript函数是一种JavaScript代码块，在调用时执行

​	当发生事件时调用

##  `<head>`或`<body>`中的JavaScript

​	脚本可被放置在HTML页面的`<body>`或`<head>`中

##  外部脚本

​	脚本可放置在外部文件中

​	外部文件 myScript.js

```html
<script src="myScript.js"></script>
```

### 	优势：

- 分离HTML和代码
- 使HTML和JavaScript更易于阅读和维护
- 已缓存的JavaScript文件可加速页面加载

## 外部引用

```html
<script src="https://www.w3school.com.cn/js/myScript1.js"></script>
```

---

# 输出

 JavaScript不提供任何内建的打印或显示函数

##  显示方案

- `window.alert()` 写入警告框
-  `document.write()` 写入 HTML 输出
-  `innerHTML` 写入 HTML 元素
-  `console.log()` 写入浏览器控制台

##  inner HTML

​	如需访问HTML元素，JavaScript可使用 document.getElementById(id)

```html
<p id="demo"></p>
<script>
document.getElementById("demo").innerHTML = 5 + 6;
</script>
```

​	输出：11

##  document.write()

```html
<script>
document.write(5 + 6);
</script>
```

​	输出：11

​	**提示**：在 HTML 文档完全加载后使用 `document.write()` 将*删除所有已有的 HTML*

> document.write() 方法仅用于测试

## window.alert()

​	使用警示框显示数据

```html
<script>
	window.alert(5 + 6);
</script>
```

​	输出：11

## console.log()

​	浏览器中可以使用该方法显示数据

```html
<script>
	console.log(5 + 6);
</script>
```

<img src="C:\Users\HP\AppData\Roaming\Typora\typora-user-images\image-20240122121608596.png" alt="image-20240122121608596"  />



---

# 语句

 **在 HTML 中，JavaScript 语句是由 web 浏览器“执行”的“指令”**

##  语句构成：

​	值、运算符、表达式、关键词和注释

##  语法

1. 每条可执行语句后添加分号`;`
2. 忽略空格
3. 增强可读性，适当的折行
4. 代码块用花括号`{}`
5. 值：混合值和变量值
6. 书写混合值
   1. 数值：有无小数点均可
   2. 字符串：由双引号或单引号包围
7. 注释 `//`
8. 对大小写敏感
9. 标识符：首字符必须是字母，下划线`_`或美元符号`$`
10. JavaScript 程序员倾向于使用以小写字母开头的驼峰大小写
11. 使用 *Unicode* 字符集

##  关键字

- break		终止switch或循环
- continue
- debugger       停止执行JavaScript，并调用调试函数
- do ……while
- for
- function     声明函数
- if……else
- return
- switch     标记需要被执行的语句块，根据不同的情况
- try……catch   对语句块实现错误处理
- var     声明变量

#  变量

​	JavaScript 变量是存储数据值的容器

##   标识符

- 所有 JavaScript *变量*必须以*唯一的名称*的*标识*
- 名称可包含字母、数字、下划线和美元符号
- 名称必须以字母开头
- 名称也可以 `$` 和 `_` 开头（但是在本教程中我们不会这么做）
- 名称对大小写敏感（y 和 Y 是不同的变量）
- 保留字（比如 JavaScript 的关键词）无法用作变量名称
- 对大小写敏感

##   数据类型

​		字符串被包围在双引号或单引号中。数值不用引号

#  赋值

```javascript
var carname
```

##   逗号分隔变量

```javascript
var person = "Bill Gates", carName = "porsche", price = 15000;
```

##   重复声明 JavaScript 变量

```javascript
var carName = "porsche";
var carName;
```

​	carname的值还是"porsche"

# Let

​	提供了块作用域（*Block Scope*）变量（和常量）

​	在这之前，只有**全局作用域**和**函数作用域**

##  块作用域

​	通过 `var` 关键词声明的变量没有块*作用域*。

​	在块 *{}* 内声明的变量可以从块之外进行访问

```JavaScript
{ 
  var x = 10; 
}
// 此处可以使用 x
```

​	使用 `let` 关键词声明拥有块作用域的变量。

​	在块 *{}* 内声明的变量无法从块外访问

```javascript
{
	let x = 10;
}
//此处不可以使用x
```

## 重新声明变量

​	使用 `let` 关键字重新声明变量可以解决在块中重新声明的问题。

​	在块中重新声明变量不会重新声明块外的变量

```JavaScript
var x = 10;
// 此处 x 为 10
{ 
  let x = 6;
  // 此处 x 为 6
}
// 此处 x 为 10
```

## 循环作用域

```JavaScript
var i = 7;
for (var i = 0; i < 10; i++) {
// 此处，i 为 10
}

let i = 7;
for(let i = 0; i < 10; i++) {
//此处，i 为 7
}
```

##  函数作用域

​	var 和 let 都有函数作用域

##  全局作用域

​	如果在块外声明，var 和 let 都有全局作用域

##  HTML中全局变量

​	使用 JavaScript 的情况下，全局作用域是 JavaScript 环境。

​	在 HTML 中，全局作用域是 window 对象

```javascript
var carname = "porsche" 等价于 window.carname
```

​	注意：let定义的全局变量不属于window对象，即上述情况换成let不成立

##  重新声明

​	var允许任何位置重新声明

​	let只有在不同块中允许重新声明

##  提升

​	var可以在声明前使用变量，会提升到顶端(就是会优先编译var)

​	let则不可以

# Const

​	const定义的值不能修改，所以在定义时就必须要赋值

##  块作用域

```javascript
var x = 10;
// 此处，x 为 10
{ 
  const x = 6;
  // 此处，x 为 6
}
// 此处，x 为 10
```

##  不是真正的常数

​	const定义了对值的常量引用(在块中)

##  const对象属性可以修改

##  const数组可以修改但不能重新赋值

##  其他同let

# 运算符

 数字运算同Java

##  字符串运算符

```js
txt1 = "Bill";
txt2 = "Gates";
txt3 = txt1 + " " + txt2; 
```

txt3 的结果将是(先后顺序有影响)：

```
Bill Gates
```

> 在用于字符串时，"+"被称为级联运算符

##  字符串和数字相加

​	如果您对数字和字符串相加，结果将是字符串

## 特殊运算符

- ===	等值等型
- instanceof     返回 true，如果对象是对象类型的实例
- **   幂(次方)

##  优先级

​	大体同Java

​	当优先级相同时，从左向右

# 数据类型

​	**字符串值，数值，布尔值，数组，对象**

1. 动态类型：变量可用作不同类型
2. 字符串值：被单或双引号包围，字符串内也可以使用
3. 数值，JavaScript只有一种数值，写不写小数点均可
   1. `var y = 123e5//12300000;var y = 123e-5;//0.00123`
   2. 精度：默认精确到15位
4. 数组：`var array[]`
5. 对象：`var class = {};`
6. typeof运算符：返回类型
7. undefined:没有值
8. 空值：与undefined不同，`var car = "";`
9. null：null的数据类型是对象
   1. `null == undefined 正确`
   2. `null === undefined  错误`

##  复杂数据

​	typeof运算符返回：

- function：对象，数组或null
- object：函数

# 函数

##  语法

​	函数名可包含字母、数字、下划线和美元符号

```js
function name(参数 1, 参数 2, 参数 3) {
    要执行的代码
}
```

##   调用

- 当事件发生时（当用户点击按钮时）
- 当 JavaScript 代码调用时
- 自动的（自调用）

​	特殊：`()`运算符调用函数

​			有`()`引用函数结果(就是return的对象)；

​			没有的引用的是函数对象(就是引用整个函数内容)

# 对象

​	与Java相同

##  定义

```js
var person = {属性，方法};
```

##  访问对象属性

```js
object.propertyname;
object["propertyname"]
```

##  访问对象方法

```js
object.methodname();
name = person.fullname();
```

# 事件

- HTML 网页完成加载
- HTML 输入字段被修改
- HTML 按钮被点击

| 事件        | 描述                         |
| :---------- | :--------------------------- |
| onchange    | HTML 元素已被改变            |
| onclick     | 用户点击了 HTML 元素         |
| onmouseover | 用户把鼠标移动到 HTML 元素上 |
| onmouseout  | 用户把鼠标移开 HTML 元素     |
| onkeydown   | 用户按下键盘按键             |
| onload      | 浏览器已经完成页面加载       |

# 字符串

- 长度：`var sln = txt.length;`

- 转义字符

- | 代码 | 结果 | 描述   |
  | :--- | :--- | :----- |
  | \'   | '    | 单引号 |
  | \"   | "    | 双引号 |
  | \\   | \    | 反斜杠 |

- 字符串可以是对象(会拖慢执行速度)

# 字符串方法

##  查找

- `indexOf()`返回字符串中指定文本的首次出现的索引
- `lastIndexOf()`返回最后一次
- 如果未找到，都返回-1

##  检索

​	`search()`返回匹配的位置

> `indexOf() 和 search() 并不相同`

1. search() 方法无法设置第二个开始位置参数。
2. indexOf() 方法无法设置更强大的搜索值（正则表达式）。

##  提取

- slice(*start*, *end*)(正数正着数，负数反着数，省略第二个参数则默认指向未或首)
- substring(*start*, *end*)(无法接受负索引，)
- substr(*start*, *length*)(第二个参数指定长度)

```js
var res = str.substr(7,6);
```

##  替换

​	`replace()`用指定值替换指定值的(首个)匹配(对大小写敏感)

```js
var n = str.replace("Microsoft", "W3School");
var n = str.replace(/MICROSOFT/i, "W3School");	//对大小写不敏感
var n = str.replace(/Microsoft/g, "W3School");	//替换所有匹配
```

##  转换大小写

​	`toUpperCase()`转化为大写

```js
var text1 = "hello";
var text2 = text1.toUpperCase();
```

​	`toLowerCase()`转换为小写

##  连接

​	`contact()`连接两个或多个字符串，代替`+`

```js
var text1 = "Hello";
var text2 = "World";
text3 = text1.concat(" ",text2); //" "是第一个值空格，text2是第二个值
```

> 字符串是不可变的：所有字符串方法都返回新字符串

##  删除空白符

​	`trim()`删除字符串两端的空白

##  提取字符串字符

### 	`charAt()`

​		返回指定下标的字符串

### 	`charCodeAt()`

​		返回指定索引的unicode编码

##  属性访问

​	str[0];

##  转化为数组

​	`split()`

```js
var txt = "a,b,c,d";
txt.split("|");	//用|分割
```

# 字符串模板

##  Back-Tics 语法

​	模板字面量*使用反引号 (``) 而不是引号 ("") 来定义字符串

##  插值

* 模板字面量*提供了一种将变量和表达式插入字符串的简单方法。

​	该方法称为字符串插值（string interpolation）

```js
${...}
```

##  变量替换

```js
let firstName = "Bill";
let lastName = "Gates";
let text = `Welcome ${firstName}, ${lastName}!`;
```

text = "welcome Bill Gates"

##  表达式替换

​	允许字符串中的表达式

```js
let price = 10;
let VAT = 0.25;
let total = `Total: ${(price * (1 + VAT)).toFixed(2)}`;
```

##  HTML 模板

```js
let header = "Templates Literals";
let tags = ["template literals", "javascript", "es6"];
let html = `<h2>${header}</h2><ul>`;
for (const x of tags) {
  html += `<li>${x}</li>`;
}
```

# 数字

​	js数字始终以双浮点存储

​	js加法和级联都使用`+`

​	js每次运算都尝试把字符转化成数字

​	否则再输出字符或NaN

##  NaN(Not a Number)

```js
	var x = 100 / "Apple";  // x 将是 NaN（Not a Number）
```

​	`isNaN()`判断是不是数

```js
typeof NaN;             // 返回 "number"
```

##  Infinity

​	计算数时超出最大可能数范围时返回的值

- 反复相乘结果过大
- 除以0

```js
typeog Infinity;		//返回"number"
```

##  十六进制

```js
	var x = 0xFF;             // x 将是 255。
```

`toString()`输出为十六，八进制

```js
var myNumber = 128;
myNumber.toString(16);     // 返回 80
myNumber.toString(8);      // 返回 200
```

# Biglnt

 **BigInt 变量用于存储太大而无法用普通 JavaScript 数字表示的大整数值**

-  整数精度：15位 ( 2^53 - 1 ----  -( 2^53 - 1 ) )

##  创建Biglnt

1. 在整数末尾添加n
2. 调用Biglnt()

##  概述

-  数据类型为biglnt
- 运算符与number型相同
- biglnt不能有小数
- 可以写成十六进制，八进制，二进制

##  最大和最小安全整数

- MAX_SAFE_INTEGER
- MIN_SAFE_INTEGER

##  数字方法

- `Nnumber.isInteger()` 	参数是整数则返回true
- `Number.isSafeInterger()`	参数是安全整数则返回true
- `toString()`将数字作为字符串返回
- `toExponential()`返回以指数表示法书写的数字
- `toFixed()`  返回带小鼠位数的数字
- `toPresion()`返回指定长度的数字
- `ValueOf()` 以数字形式返回数字
- 数字方法只能用于Number对象

##  将变量转化为数字

- `Number()`	返回从其参数转换而来的数字(无法转化则返回NaN)
- `parseFloat()`   返回浮点数
- `parseInt()`   返回整数
- 允许有空格，仅返回第一个数字

##  日期上使用Number()方法

​	将日期转换为数字

​	`Date()`返回当前年份第一个以来的毫秒数

``` js
Number(new Date("1970-01-02"))
document.getElementById("demo").innerHTML = Number(x); 
//输出：86400000
```

##  数字属性

- `EPSILON`   1和大于1的最小数之间的差(趋近于零的最小数)
- `MAX_VALUE`   最大数
- `POSITIVE_INFINITY`   无穷大
- `NEGATIVE_INFINITY`  负无穷大

# 数组

##  创建数组

```js
var array-name = [item1, item2, ...];
var cars = new Array("Saab", "Volvo", "BMW");
第一种更简洁
```

##  访问及修改元素

```js
var name = cars[0];
cars[0] = "Opel";
```

##  访问完整数组

```js
var cars = ["Saab", "Volvo", "BMW"];
document.getElementById("demo").innerHTML = cars;
```

##  数组是对象

​	因此，可以在相同数组中存放不同类型的变量

- 数组中保存对象
- 数组中保存函数
- 数组中保存数组

```js
myArray[0] = Date.now;
myArray[1] = myFunction;
myArray[2] = myCars;
```

##  数组和对象的区别

​	数组使用数字索引

​	对象使用命名索引

##  数组函数

- `length`返回长度`document.getElementById("demo").innerHTML = fruits.length;`
- `cars.sort(); `排序
- `Array.foreach()`遍历
- `fruits.push("Lemon"); `添加元素
- `fruits[fruits.length] = "Lemon";`也可以用push
- `Array.isArray()`是数组返回真

# 数组方法

1. `toString()`返回逗号分隔的字符串
2. `join()`将所有数组元素结合程一个字符串，需规定分隔符`fruits.join(" * ");` 
3. `pop()`删除最后一个元素，返回该值
4. `push`()在数组末添加一个元素，返回新数组长度
5. `shift()`删除第一个元素
6. `unshift()`在开头插入一个元素，返回新数组长度
7. `delete fruit[0]`清空该元素，会留下空洞
8. `splice()`拼接数组`fruits.splice(2//新元素添加位置, 0//删除元素个数, "Lemon", "Kiwi"//新添加的元素);`
9. `splice()`删除元素`fruit.splice(0, 1);`
10. `concat()`合并数组`var myChildren = myGirls.concat(myBoys);   // 连接 myGirls 和 myBoys`(参数任意数量，也可以是值)
11. `slice()`剪裁数组，一个参数就剪裁剩下该值之后的，两个参数就剪裁剩下两数之间的元素
12. 自动`toString()`如果需要会自动转换为字符串`document.getElementById("demo").innerHTML = fruits;` 
13. `reverse()`反转数组
14. 数字排序
    1. `points.sort(function(a, b){return a - b});`升序排序
    2.  `points.sort(function(a, b){return b - a});` 降序排序
15. `points.sort(function(a, b){return 0.5 - Math.random()}); `随机顺序排序
16. `Math.max.apply(null//查找范围, arr//查找的数组)`查找最大值
17. `Math.min.apply(null, arr)`
18. `forEach(value,index,array)`每个元素调用一次函数`numbers.forEach(myFunction);`
19. `map()` 方法通过对每个数组元素执行函数来创建新数组
20. `filter()` 方法创建一个包含通过测试的数组元素的新数组
21. `reduce(total, value, index, array)` 方法在每个数组元素上运行函数，以生成（减少它）单个值
22. `reduceRight()` 方法在每个数组元素上运行函数，以生成（减少它）单个值
23. `every()` 方法检查所有数组值是否通过测试
24. `some()` 方法检查某些数组值是否通过了测试
25. `indexOf()` 方法在数组中搜索元素值并**返回其位置**`var a = fruits.indexOf("Apple");`
26. `Array.lastIndexOf()` 与 `Array.indexOf()` 类似，但是从数组结尾开始搜索
27. `find()` 方法返回通过测试函数的第一个数组元素的<u>值</u>
28. `findIndex()` 方法返回通过测试函数的第一个数组元素的<u>索引</u>

# 数组const

- 无法重新赋值
- 不定义常量数组。它定义的是对数组的常量引用
- 元素可以重新赋值
- 声明时赋值
- const 块作用域

# 日期

##  new Date()

​	`new Date()` 用当前日期和时间创建新的日期对象(静态的)

​	年、月、日、小时、分钟、秒和毫秒（按此顺序）：

​	`var d = new Date(2018, 11, 24, 10, 33, 30, 0);`

​	注意：从0到11计算月份，一位和两位数年份将被解释为 19xx 年

- new Date(milliseconds)创建一个零时加毫秒的新日期对象
- `new Date(dateString)` 从日期字符串创建一个新的日期对象(不使用也会自动转换)
- `toUTCString()` 方法将日期转换为 UTC 字符串（一种日期显示标准）
- `toDateString()` 方法将日期转换为更易读的格式

# 日期格式

| 类型     | 实例                             |
| :------- | :------------------------------- |
| ISO 日期 | "2018-02-19" （国际标准）        |
| 短日期   | "02/19/2018" 或者 "2018/02/19"   |
| 长日期   | "Feb 19 2018" 或者 "19 Feb 2019" |
| 完整日期 | "Monday February 25 2015"        |

##  默认输出

> ​	Mon Feb 19 2018 06:00:00 GMT+0800 (中国标准时间)

##  JavaScript ISO 日期

```js
var d = new Date("2018-02-19");//完整日期
var d = new Date("02/19/2018");//短日期
var d = new Date("Feb 19 2018");//长日期
```

# 日期获取方法

- `getTime()`返回自107年1月1日以来的毫秒数
- `getFullYear()`以四位数字形式返回日期年份
- `getMonth()`以数字返回月份
- `getDate()`以数字返回日
- `getHours()`以数字返回日期的小时数
- `getMinutes()`以数字返回分钟数
- `getSeconds()`返回秒
- `getMilliseconds()`返回毫秒数

# 日期设置方法

- `setFullyear(2020, 11, 3)`设置年份，该例子设置为2020年11月3日，可以只设置年
- `setMonth()`
- `setDate()`
- 比较日期,直接比较，日期大的大

# 数学

- `Math.PI;`返回3.141592653589793

- `Math.round()`四舍五入整数

- `Math.pow(8,2)`返回64

- `Math.sqrt(x)`返回x的平方根

- `Math.abs()`返回绝对值

- `Math.ceil()`向上取整

- `Math.floor()`向下取整

- `Math.sin(x)`返回x(弧度制)的正弦值

- `Math.max(40,2,-5,6,4,9);`返回最大值

- `Math.random()`返回随机数

- ```js
  Math.E          // 返回欧拉指数（Euler's number）
  Math.PI         // 返回圆周率（PI）
  Math.SQRT2      // 返回 2 的平方根
  Math.SQRT1_2    // 返回 1/2 的平方根
  Math.LN2        // 返回 2 的自然对数
  Math.LN10       // 返回 10 的自然对数
  Math.LOG2E      // 返回以 2 为底的 e 的对数（约等于 1.414）
  Math.LOG10E     // 返回以 10 为底的 e 的对数（约等于 0.434）
  ```

# 随机

​	`Math.random()`总是返回小于1的数

```js
Math.floor(Math.random() * 10);		// 返回 0 至 9 之间的数
```

## 适当的随机函数

```js
function getRndInteger(min, max) {
    return Math.floor(Math.random() * (max - min) ) + min;
}
```

# 逻辑

##  Boolean() 函数

​	您可以使用 `Boolean()` 函数来确定表达式（或变量）是否为真

##  布尔可以是对象

# 语法

- for循环同c++
- if……else同c++
- switch同c++
- while/do……while同c++
- break/continue同c++

##  for in

```js
for (key in object) {//遍历对象
  // code block to be executed
}//key返回下标
```

##  for of

```js
for (variable of iterable) {//遍历可迭代的数据结构
  // code block to be executed
}//variable返回当前值
```

# 类型转换

##  数据类型

- 字符串（string）
- 数字（number）
- 布尔（boolean）
- 对象（object）
- 函数（function）

##  对象类型

- 对象（Object）
- 日期（Date）
- 数组（Array）

##  constructor

```js
"Bill".constructor                 // 返回 "function String()  { [native code] }"
(3.14).constructor                 // 返回 "function Number()  { [native code] }"
```

## 把数值转换为字符串

​	全局方法 `String()` 能够把数字转换为字符串

## 把字符串转换为数值

​	全局方法 `Number()` 可把字符串转换为数字

| parseFloat() | 解析字符串并返回浮点数。 |
| ------------ | ------------------------ |
| parseInt()   | 解析字符串并返回整数。   |

# 位运算符

| 运算符 | 名称         | 描述                                                     |
| :----- | :----------- | :------------------------------------------------------- |
| &      | AND          | 如果两位都是 1 则设置每位为 1                            |
| \|     | OR           | 如果两位之一为 1 则设置每位为 1                          |
| ^      | XOR          | 如果两位只有一位为 1 则设置每位为 1                      |
| ~      | NOT          | 反转所有位                                               |
| <<     | 零填充左位移 | 通过从右推入零向左位移，并使最左边的位脱落。             |
| >>     | 有符号右位移 | 通过从左推入最左位的拷贝来向右位移，并使最右边的位脱落。 |
| >>>    | 零填充右位移 | 通过从左推入零来向右位移，并使最右边的位脱落。           |

| 操作    | 结果 | 等同于       | 结果 |
| :------ | :--- | :----------- | :--- |
| 5 & 1   | 1    | 0101 & 0001  | 0001 |
| 5 \| 1  | 5    | 0101 \| 0001 | 0101 |
| 5 ^ 1   | 4    | 0101 ^ 0001  | 0100 |
| ~ 5     | 10   | ~0101        | 1010 |
| 5 << 1  | 10   | 0101 << 1    | 1010 |
| 5 >> 1  | 2    | 0101 >> 1    | 0010 |
| 5 >>> 1 | 2    | 0101 >>> 1   | 0010 |

# 正则表达式

​	**正则表达式是构成搜索模式的字符序列**

##  语法

```js
/pattern/modifiers;
```

##  search()

```js
var str = "Visit W3School!"; 
var n = str.search("W3School");
document.getElementById("demo").innerHTML = n;
输出：6
var str = "Visit W3School!"; 
var n = str.search(/w3School/i);
document.getElementById("demo").innerHTML = n;
输出：6
```

##  replace()

```js
var str = document.getElementById("demo").innerHTML; 
var txt = str.replace("Microsoft","W3School");//var res = str.replace(/microsoft/i, "W3School"); 
 document.getElementById("demo").innerHTML = txt;
输出：请访问 Microsoft！  替换成   请访问 W3School！
```

## 修饰符

| 修饰符 | 描述                                                     |
| :----: | :------------------------------------------------------- |
|   i    | 执行对大小写不敏感的匹配。                               |
|   g    | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
|   m    | 执行多行匹配。                                           |

## 模式

| 表达式 | 描述                       |
| :----- | :------------------------- |
| [abc]  | 查找方括号之间的任何字符。 |
| [0-9]  | 查找任何从 0 至 9 的数字。 |
| (x\|y) | 查找由 \| 分隔的任何选项。 |

## 使用 test()

​	通过模式来搜索字符串，然后根据结果返回 true 或 false

```js
var patt = /e/;
patt.test("The best things in life are free!"); 
输出：true
```

## 使用 exec()

​	通过指定的模式（pattern）搜索字符串，并返回已找到的文本

# 错误

**`try` 语句使您能够测试代码块中的错误。**

**`catch` 语句允许您处理错误。**

**`throw` 语句允许您创建自定义错误。**

**`finally` 使您能够执行代码，在 try 和 catch 之后，无论结果如何

## Error 对象属性

| 属性    | 描述                             |
| :------ | :------------------------------- |
| name    | 设置或返回错误名                 |
| message | 设置或返回错误消息（一条字符串） |

- 范围错误，`RangeError` 会在您使用了合法值的范围之外的数字时抛出
- 引用错误，假如您使用（引用）了尚未声明的变量，则 `ReferenceError` 会被抛出
- 语法错误，假如您计算带语法错误的代码，会 `SyntaxError` 被抛出
- 类型错误，假如您使用的值不在期望值的范围之内，则 `TypeError` 被抛出
- URI 错误，假如您在 URI 函数中使用非法字符，则 `URIError` 被抛出

# Hoisting

- JavaScript 声明会被提升
- 用 `let` 或 `const` 声明的变量和常量不会被提升
- JavaScript 初始化不会被提升
- 在顶部声明您的变量！

# 严格模式

**`"use strict";` 定义 JavaScript 代码应该以“严格模式”执行**

通过在脚本或函数的开头添加 `"use strict";` 来声明严格模式

# this 关键词

`this` 关键词指的是它**<u>所属的对象</u>**

- 在方法中，`this` 指的是所有者对象。
- 单独的情况下，`this` 指的是全局对象。
- 在函数中，`this` 指的是全局对象。
- 在函数中，严格模式下，`this` 是 undefined。
- 在事件中，`this` 指的是接收事件的元素。

1. 方法中的this：在对象方法中，`this` 指的是此方法的“拥有者”
2. 单独的this，拥有者是全局对象，全局对象是[object window]
3. 事件处理程序中的this：指接受时间的HTML元素
4. 函数中的this：指全局对象，严格模式下是未定义的

# 箭头函数

```js
let myFunction = (a, b) => a * b;
document.getElementById("demo").innerHTML = myFunction(4, 5);
输出：20
```

如果函数只有一个语句，并且该语句返回一个值，则可以去掉括号和 `return` 关键字：

```js
hello = () => "Hello World!";
```

**注释：**这仅在函数只有一条语句时才有效。

# 类

```js
class ClassName {
  constructor() { ... }
}
```

​	**请始终添加名为 `constructor()` 的方法**

##  使用类

```js
let myCar1 = new Car("Ford", 2014);
```

##  Constructor 方法

- 它必须拥有确切名称的“构造函数”
- 创建新对象时自动执行
- 用于初始化对象属性
- 如果未定义构造函数方法，JavaScript 会添加空的构造函数方法

##  方法

```js
class ClassName {
  method_1() { ... }
}
```

# 模块

​	modules模块，允许将代码分解成单独的文件

​	模块是使用 `import` 语句从外部文件导入的

​	模块是使用 `import` 语句从外部文件导入的。

​	模块还依赖于 `<script>` 标签中的 `type="module"`。

##  导出

###  命名导出

​	创建一个名为 person.js 的文件，并在其中填充我们要导出的内容

1. 逐个内联创建

   ```js
   export const name = "Bill";
   export const age = 19;
   ```

   2.在文件底部一次性创建

```js
const name = "Bill";
const age = 19;
export {name, age};
```

##  导入

 1.从命名导出中导入  ,从文件 person.js 导入命名导出：

```js
import { name, age } from "./person.js";
```

 2.从默认导出导入   ,从文件 message.js 导入默认导出：

```js
import message from "./message.js";
```

# JSON

**JSON 是存储和传输数据的格式。**

**JSON 经常在数据从服务器发送到网页时使用**

<u>类似 JavaScript，数组能够包含对象</u>

<u>**JSON 的通常用法是从 web 服务器读取数据，然后在网页中显示数据**</u>

- JSON 指的是 **J**ava**S**cript **O**bject **N**otation
- JSON 是轻量级的<u>**数据交换格式**</u>
- JSON 独立于语言 *****
- JSON 是“自描述的”且易于理解

##  JSON 格式评估为 JavaScript 对象

## 语法规则

- 数据是名称/值对
- 数据由逗号分隔
- 花括号保存对象
- 方括号保存数组

1. json对象，在花括号中书写，能包含多个名称、值对
2. json数组，在方括号中书写，能包含对象
3. json数据，名称需要双引号

# 调试

##  console.log() 方法

​	如果您的浏览器支持调试，那么您可以使用 `console.log()` 在调试窗口中显示 JavaScript 的值

```html
c = a + b;
console.log(c);
```

##  debugger

​	*debugger* 关键词会停止 JavaScript 的执行，并调用（如果有）调试函数

​	这与在调试器中设置断点的功能是一样的

# 样式指南

##  对象规则

​	针对对象定义的通用规则：

- 把开括号与对象名放在同一行
- 在每个属性与其值之间使用冒号加一个空格
- 不要在最后一个属性值对后面写逗号
- 请在新行上写闭括号，不带前导空格
- 请始终以分号结束对象定义

​	**<u>JavaScript 命名不允许使用连字符</u>**

##  JSON.parse()

​	将文本转换为 JavaScript 对象

​	JSON 的一个常见用途是从 Web 服务器接收数据

```js
var obj = JSON.parse('{"name":"Bill", "age":62, "city":"Seatle"}');
```

##  JSON.stringify()

​	将对象转化成字符串

# 实践

- 避免全局变量
- 始终声明局部变量，在顶部声明，初始化
- 不要使用new Object()
- 不用===

# 常见错误

##  字符串换行

​	在字符串中间来换行是不对的：

​	如果必须在字符串中换行，则必须使用反斜杠

```js
var x = "Hello \
World!";
```

##  return 语句进行换行

- return后可以不加分号
- return语句不能换行

##  用逗号来结束定义

- 对象和数组定义中的尾随逗号在 ECMAScript 5 中是合法的
- JSON 不允许尾随逗号

##  Undefined 不是 Null

- 可以通过测试类型是否为 `undefined`，无法测试对象是否为 `null`
- 在测试非 null 之前，必须先测试未定义

> ##  JavaScript *不会*为每个代码块创建新的作用域。

# 性能

##  延迟 JavaScript 加载

​	在 script 标签中使用 `defer="true"`规定了脚本应该在页面完成解析后执行



















