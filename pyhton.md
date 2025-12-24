# 基础语法

##  输出

```py
^表示居中输出
5表示占五格

指定填充字符
print("{:*^5}".format("a"))   # 输出： **a**
print("{:->5}".format("b"))   # 输出： ----b
print("{:_<5}".format("c"))   # 输出： c____

数字格式化
print("{:.2f}".format(3.14159))  # 输出： 3.14
print("{:,}".format(123456789))  # 输出： 123,456,789
print(f"{t / n :.3f}") # 输出：float型 保留三位小数
# 注意冒号后的空格也会输出

格式化百分比
print("{:.1%}".format(0.75))  # 输出： 75.0%

进制转换
print("{:b}".format(10))  # 输出： 1010 (二进制)
print("{:o}".format(10))  # 输出： 12   (八进制)
print("{:x}".format(10))  # 输出： a    (十六进制)
print("{:#x}".format(10)) # 输出： 0xa  (十六进制，带前缀)

大括号转义
print("{{Hello}}".format())  # 输出： {Hello}
```

##  常用方法

### 	反转

```py
number = input()
reversed_number = number[::-1]
print(reversed_number)
"""

[::-1]是一种列表切片操作，用于将列表或字符串中的元素进行反转。
这个表达式实际上是[start_index:end_index:step]

当你使用[::-1]时，
你实际上是省略了start_index和end_index，只提供了一个步长-1

"""
```

### 	数学库

```py
import math
result = math.sqrt(16)  # 结果为 4.0
```

