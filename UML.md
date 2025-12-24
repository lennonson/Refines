[TOC]



| 题型 | 分值                           |
| ---- | ------------------------------ |
| 选择 | 15*2=30                        |
| 判断 | 10*1=10                        |
| 简答 | 5*4=20                         |
| 建模 | 40用例图、类图、状态图、活动图 |

![image-20251223172837865](D:\refines\refines\UML-img\image-20251223172837865.png)

# **五大类**

UML 语言的图形通常分为: 

1. **用例图（Use Case Diagram）**
2. **静态结构图**（如类图、对象图、包图等）
3. **行为图**（如状态图、活动图）
4. **交互图**（如顺序图、协作图）
5. **实现图**（如构件图、部署图）

# 用例图

## 参与者(`actor`角色)

1. 概念：指系统以外的、需要使用系统或与系统交互的外部实体
2. 分类：人、外部设备、外部系统,  时间
3. 参与者是一个集合概念
4. 图形符号
   ![image-20251223084534942](D:\refines\refines\UML-img\image-20251223084534942.png)

## 用例

1. 概念：用例（`use case`）是对一个参与者使用系统的一项功能时所进行的交互过程的一个文字描述序列
2. 是参与者可以感受到的系统服务或功能单元
3. 用例名往往用动宾结构或主谓结构命名
4. ![image-20251223085019624](D:\refines\refines\UML-img\image-20251223085019624.png)
5. 用例是对系统行为的动态描述
6. 用例分析本质上是一种功能分解技术
7. 用例适合描述用户的功能需求
8. 用例描述
   - 事件流
     1. 基本事件流
     2. 扩展事件流

   - 目的: 为不了解用例图的人提供规范

9. 用例粒度
   - 就是用例的规模


## 用例关系

### 参与者之间的关系

1. 泛化关系：一般参与者与特殊参与者之间的关系
2. 泛化关系`把共性的部分抽象出来`
3. 泛化关系用带空心三角形箭头的实线表示，箭头指向父参与者。
   ![image-20251223084803861](D:\refines\refines\UML-img\image-20251223084803861.png)

### 参与者与用例之间的关系

1. 关联关系：起通信的作用，即描述了：一个参与者完成系统的一项功能
2. ![image-20251223084953887](D:\refines\refines\UML-img\image-20251223084953887.png)

### 用例之间的关系

1. 泛化关系、包含关系、扩展关系
2. 包含关系：基本用例的行为必然执行`包含用例`的行为

   - ![image-20251223090424518](D:\refines\refines\UML-img\image-20251223090424518.png)
   - 是比较特殊的依赖关系
   - 包含关系用带箭头的虚线表示，箭头指向包含用例，同时，用`<<include>>`标记附加在虚线旁，作为特殊依赖关系的语义。
3. 扩展关系：基本用例的行为条件执行扩展用例的行为

   - ![image-20251223090700543](D:\refines\refines\UML-img\image-20251223090700543.png)
   - 扩展用例也是特殊的依赖关系
   - 扩展用例用带箭头的虚线表示，箭头指向基本`用例`，加`<<extend>>`标记附加在虚线旁，作为特殊依赖关系的语义

### 系统边界

1. 是指系统与系统之间的界限
2. 系统边界定义了由谁或什么（即参与者）来使用系统，系统能够为参与者提供什么特定服务
3. 绘图
   1. 在用例图中，系统边界用实线方框图形符号表示
   2. 用例绘制在方框里面（即边界里面）
   3. 参与者绘制在方框外面（即边界外面)
   4. ![image-20251223092055324](D:\refines\refines\UML-img\image-20251223092055324.png)

![image-20251223094051362](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20251223094051362.png)

# 类图

1. 包名：包括了包名的类名

   1. e.g `Banking::CheckingAccount`

2. 属性

   1. 语法格式：`[可见性]属性名[:类型]['['多重性[次序]']'][=初始值][{约束特性}]`
   2. 类型：表示该属性的`数据类型`
   3. 多重性：表示该属性值有`一个或多个`（`0..n`  , `1`）
   4. 约束特性：描述了对属性取值的`修改的限制`
   5. 可见性：描述了该属性是否对于其他类`可见`(`public`, `private`,`protected`)
      1. 在 UML 类图中，可见性符号含义是：
         - `+` ：Public（公有）
         - `#` ：Protected（受保护）
         - `-` ：Private（私有）
         - `~` ：Package（包内可见）
   6. 三种预定义的属性可变性
      1. `changeable`
      2. `addOnly`
      3. `frozen`

3. 作用域

   1. 对象作用域
   2. 类作用域
   3. e.g 
      1. <img src="D:\refines\refines\UML-img\image-20251223173950710.png" alt="image-20251223173950710" style="zoom:50%;" />
      2. 画横线的`mcount`属性具有==类作用域==
      3. 画横线的`getCount()`操作具有==类作用域==
      4. `title, getTitle()`具有对象作用域

4. #### 关系

   1. ### 关联关系
   
      - 一个类的实例与另一个类的实例在结构上的`静态联系`
      - 关联关系一旦建立，系统运行与否它都存在
      - 关联用（不）带箭头的`实线`表示。如果带箭头，`箭头指向被依赖的类`
      - 关联可以有方向，可以是`单向`关联或`双向`关联
      - e.g 
   
        <img src="D:\refines\refines\UML-img\image-20251223174513947.png" alt="image-20251223174513947" style="zoom:50%;" /><img src="D:\refines\refines\UML-img\image-20251223174542863.png" alt="image-20251223174542863" style="zoom:50%;" />
   
      - 关联名	
   
        1. 可以给关联加上关联名，来描述关联的作用以便和其他关联关系相区别<img src="D:\refines\refines\UML-img\image-20251223174627064.png" alt="image-20251223174627064" style="zoom:50%;" />
   
      - 关联角色
   
        - 关联关系两端的类的对象在对方的类里的标识称为角色<img src="D:\refines\refines\UML-img\image-20251223174807510.png" alt="image-20251223174807510" style="zoom:50%;" />
   
      - 关联类
   
        1. <img src="D:\refines\refines\UML-img\image-20251223174957367.png" alt="image-20251223174957367" style="zoom: 67%;" />
   
   2. ### 聚合(聚集)关系
   
      - 聚合是一种特殊形式的关联.
   
      - 聚合表示类之间整体与部分的关系。
   
      - 没有相同的生存期
   
      - <img src="D:\refines\refines\UML-img\image-20251223175227173.png" alt="image-20251223175227173" style="zoom:50%;" />
   
   3. ### 组成(组合)关系
   
      - 组成是一种特殊形式的关联。组成表示类之间整体与部分的关系。
      - 与聚合关系的区别是组成关系`有相同的生存期`<img src="D:\refines\refines\UML-img\image-20251223175346216.png" alt="image-20251223175346216" style="zoom:50%;" />
   
   4. ### 依赖关系
   
      - 一个类的结构上的变化会影响到另一个类（代码级）
         <img src="D:\refines\refines\UML-img\image-20251223175507113.png" alt="image-20251223175507113" style="zoom:50%;" />
   
   5. ### 泛化关系
   
      - 一般类与特殊类之间的继承（代码级）<img src="D:\refines\refines\UML-img\image-20251223175535074.png" alt="image-20251223175535074" style="zoom:50%;" />
   
   6. ### 实现关系
   
      <img src="D:\refines\refines\UML-img\image-20251223181849136.png" alt="image-20251223181849136" style="zoom:50%;" />
   
      - 典型用于“类与`接口`”之间。表示一个类实现了接口中定义的规范。

- e.g
  ![image-20251223175659915](D:\refines\refines\UML-img\image-20251223175659915.png)

  ![image-20251223180100500](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20251223180100500.png)

- 实体类(`entity`)

  1. 持久存储,生命周期长于会话生命周期
  2. <img src="D:\refines\refines\UML-img\image-20251223180544593.png" alt="image-20251223180544593" style="zoom: 67%;" />
  3. <img src="../refines/refines/UML-img/image-20251224171740169.png" alt="image-20251224171740169" style="zoom:50%;" />

- 边界类(`boundary`)

  1. 边界类位于系统与外界的`交界处`，
  2. 它是`系统内`的对象和系统外的`参与者`的`联系媒介`。
  3. 外界的消息只有通过`边界类`的对象实例才能`发送给系统`。
  4. <img src="D:\refines\refines\UML-img\image-20251223180651107.png" alt="image-20251223180651107" style="zoom: 67%;" />
  5. <img src="../refines/refines/UML-img/image-20251224171754529.png" alt="image-20251224171754529" style="zoom:50%;" />

- 控制类(`control`)

  1. 控制类是负责其他类工作的类。
  2. <img src="D:\refines\refines\UML-img\image-20251223180727434.png" alt="image-20251223180727434" style="zoom:67%;" />
  3. <img src="../refines/refines/UML-img/image-20251224171808965.png" alt="image-20251224171808965" style="zoom:50%;" />

- 类图层次

  1. 概念层
     - 概念层：描述应用领域中的概念，一般这些概念和类有很自然的联系，但没有映射关系，很少考虑或不考虑实现问题，只是一个类名
  2. 说明层
     - 说明层：描述软件的接口部分，而不是实现部分有类名、属性名和方法名
  3. 实现层
     - 实现层：才真正考虑类的实现问题，提供了类的实现细节，对类的属性和方法都有详细说明
  4. 按图表构成元素
     1. 类图的三个层次为
        1. 对象层: 对象层的作用是识别系统中反映问题域和系统责任的对象（或抽象为类）。
        2. 特征层: 作用是定义类的属性和方法
        3. 关系层

# 对象图

![image-20251223180952618](D:\refines\refines\UML-img\image-20251223180952618.png)

![image-20251223181017439](D:\refines\refines\UML-img\image-20251223181017439.png)

1. 概念: 
   1. 对象图（`object diagram`）描述的是参与交互的各个对象在交互过程中某一时刻的状态。
   2. 它是系统在某一个特定时间点上的静态结构，
   3. 是类图的实例和快照即类图中的各个类在某一个时间点上的实例及其关联关系的静态写照。
2. 区分
   1. ![image-20251223181134438](D:\refines\refines\UML-img\image-20251223181134438.png)



# 活动图

## 概念

​		活动图描述对象的一个活动到另一个活动的控制流，活动的序列，工作的流程和并发的处理行为等。一个控制流关联的两个活动可以是一个对象的，也可以是多个对象的。用泳道进行说明。

## 活动

​		表示的是某流程中的任务的执行，它可以表示某算法过程中语句的执行

## 分支![image-20251223191524413](D:\refines\refines\UML-img\image-20251223191524413.png)

## 汇合

![image-20251223191553831](D:\refines\refines\UML-img\image-20251223191553831.png)

## 泳道

​		泳道（`swimlane`）是活动图中的区域划分，根据每个活动的职责对所有活动进行划分，每个泳道代表`一个责任区`。

![image-20251223192237218](D:\refines\refines\UML-img\image-20251223192237218.png)

## 对象流

​		对象流是一种特殊的控制流，表示活动和对象之间的关系。

## 对具体业务建模

![image-20251223192342521](D:\refines\refines\UML-img\image-20251223192342521.png)

![image-20251223192353302](D:\refines\refines\UML-img\image-20251223192353302.png)

## 对具体操作建模

<img src="D:\refines\refines\UML-img\image-20251223192419080.png" alt="image-20251223192419080" style="zoom:67%;" />

# 状态图

## 概念

​		状态图—描述一个对象的生命周期内的状态及状态变迁，以及引起状态变迁的事件和对象在状态中的动作等。

![image-20251223190300517](D:\refines\refines\UML-img\image-20251223190300517.png)

![image-20251223190347412](D:\refines\refines\UML-img\image-20251223190347412.png)

## 初态

1. 初态代表状态图的起始位置，它是状态，在UML中，用`实心圆`表示
   ![image-20251223190805184](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20251223190805184.png)

## 终态

1. 终态是一个状态图的终点，在UML中，用含有`实心圆`的`圆圈`表示
   ![image-20251223190811465](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20251223190811465.png)

## 中间状态

其余状态都是中间状态，中间状态包括3个区域：

1. 名字域
2. 变量域(可选)
3. 内部转移域(可选)

## 事件

1. 变化事件
   - <img src="D:\refines\refines\UML-img\image-20251223191137134.png" alt="image-20251223191137134" style="zoom:50%;" />
2. 时间事件
   - <img src="D:\refines\refines\UML-img\image-20251223191211345.png" alt="image-20251223191211345" style="zoom:50%;" />
3. 信号事件
   - ![image-20251223191310104](D:\refines\refines\UML-img\image-20251223191310104.png)
   - 上图中,`实线`代表转移,`虚线`代表信号

# 顺序图

顺序图是`交互图`的一种具体形式

1. 参与者(`actor`)
2. 生命线(`lifeline`)
3. 激活(执行条,`activation`)
4. 消息(`message`)
5. 控制结构

![](D:\refines\refines\UML-img\image-20251224114031070.png)

# 协作图

## 多对象

- 多对象**（Multiple Objects）** 是指在同一场景下系统中存在的多个对象实例，它们之间的交互关系可以在 协作图中描述。

## 对象

​		同类图中的对象，是类的实例

## 主动对象

​		主动对象是一组属性和一组方法的`封装体`，其中至少有一个方法不需要接收消息就能`主动执行`（称为主动方法

## 链

​		对象之间的连接关系

## 消息

- 对象间的一次`通信`
- 消息表示为带有`标签的箭头`
- 一个链上可以有多个消息，沿相同或不同的方向传递

## 对象生命周期

​		对象名称之后标以`{new}`约束表示创建对象，标以`{destroy}`约束表示销毁对象

<img src="D:\refines\refines\UML-img\image-20251224123553987.png" alt="image-20251224123553987" style="zoom:67%;" />

<img src="D:\refines\refines\UML-img\image-20251224123727060.png" alt="image-20251224123727060" style="zoom:67%;" />

# 包图

## 关系

1. 依赖关系
   - <img src="D:\refines\refines\UML-img\image-20251224124111681.png" alt="image-20251224124111681" style="zoom:67%;" />
2. 泛化关系
   - <img src="D:\refines\refines\UML-img\image-20251224124133123.png" alt="image-20251224124133123" style="zoom:67%;" />
3. <img src="D:\refines\refines\UML-img\image-20251224124236923.png" alt="image-20251224124236923" style="zoom:67%;" />
4. <img src="D:\refines\refines\UML-img\image-20251224124259133.png" alt="image-20251224124259133" style="zoom:67%;" />

# 组件图

## 组件

- 也称为构件，就是一个实现性文件，是系统中遵从一组接口且提供其实现的物理的、可部署的、可替换的部分。
- 组件内部可以包含很多类
- 可以有以下几种类型：
  1. `部署组件`。运行系统需要配置的组件，如Java虚拟机、XML文件、JAR文件、DLL文件、数据库表等。
  2. `工作产品组件`。可以用来产生部署组件，如源代码文件、数据文件等。
  3. `执行组件`。系统执行后得到的组件，如EJB、动态Web页、exe文件、COM+对象、CORBA对象等。
- <img src="D:\refines\refines\UML-img\image-20251224124536893.png" alt="image-20251224124536893" style="zoom:67%;" />

<img src="D:\refines\refines\UML-img\image-20251224124936183.png" alt="image-20251224124936183" style="zoom:67%;" />

<img src="D:\refines\refines\UML-img\image-20251224125010840.png" alt="image-20251224125010840" style="zoom:67%;" />

# 部署图

> `部署图`是`物理视图`的建模工具

## 结点

​		也称为节点，是存在于运行时的代表计算资源的物理元素。

<img src="D:\refines\refines\UML-img\image-20251224125116102.png" alt="image-20251224125116102" style="zoom: 50%;" />

## 连接

<img src="D:\refines\refines\UML-img\image-20251224125202328.png" alt="image-20251224125202328" style="zoom:50%;" />

- 设备”结点之间采用`RS-232`串行口连接，`<<RS-232>>`就是一个`关联名`。

<img src="D:\refines\refines\UML-img\image-20251224125307539.png" alt="image-20251224125307539" style="zoom:67%;" />





# Patch

1. **`OMT`（Object Modeling Technique，对象建模技术）** 是由 `James Rumbaugh` 提出的

2. **`用例`（Use Case）** 被认为是**`第二代面向对象技术`的重要标志**

3. ![img](../refines/refines/UML-img/wps1.png)

   1. （A）📁 包图（Package)

      - **含义**：UML 的**包（Package）**

      - **作用**：用于对类、接口、用例等模型元素进行**分组和组织**

      - **特征**：像一个“文件夹”，上面有一个小标签

      - ✅ **因此 A 是包图的正确符号**

   2. （B）▭ 类（Class）

      - **含义**：UML 中最基本的 **类**

      - **作用**：表示系统中的类（通常内部会再分为类名 / 属性 / 方法三部分）

      - **特征**：一个简单的矩形（题目中是简化画法）

   3. （C）📦 构件（Component）

      - **含义**：UML 的**构件图元素**

      - **作用**：表示可部署、可复用的软件构件（如 DLL、模块、组件）

      - **特征**：立体长方体，看起来像一个“盒子”

   4. （D）📄 制品（Artifact / 文档）

      - **含义**：UML 中的**制品（Artifact）**

      - **作用**：表示物理存在的文件，如源代码文件、配置文件、文档等

      - **特征**：右上角折角，类似一张纸

4. UML`7种结构图`和`7种行为图`包括

   | 结构图     | 行为图     |
   | ---------- | ---------- |
   | 类图       | 用例图     |
   | 包图       | 活动图     |
   | 组件图     | 顺序图     |
   | 部署图     | 通信图     |
   | 对象图     | 交互概览图 |
   | 复合结构图 | 时间图     |
   | 外廓图     | 状态机图   |

5. UML全称: `Unified modeling language`

6. **4+1 视图模型**包括：

   - **4 个结构视图**：
     - 逻辑视图
     - 开发视图
     - 过程视图
     - 物理视图
   - **+1**：**用例视图**

7. 领域模型类图

   1. 一般产生于**需求分析 / 领域分析阶段**
   2. 领域模型中的类是**概念类**
   3. 领域模型类图描述的是系统的**`静态领域结构`**
   4. 只关注与**业务相关**的属性和操作


