# Maven

- Maven是一款用于管理和构建Java项目的工具，是apache旗下的一个开源项目。
- Apache Maven是一个项目管理和构建工具，它基于项目对象模型（POM)的概念，通过一小段描述信息来管理项目的构建。

> `Apache`软件基金会，成立于1999年7月，是目前世界上最大的最受欢迎的`开源软件基金会`，也是一个专门为支持开源项目而生的非盈利性组织。
> 开源项目：https://www.apache.org/index.html#projects-list

## 作用

1. 依赖管理：方便快捷的管理项目依赖的资源 (jar包)

   ```xml
   <dependency>
   <groupId>commons-io</groupId>
   <artifactId>commons-io</artifactId>
   <version>2.11.0</version>
   </dependency>
   ```

2. 项目构建：标准化的跨平台（Linux、Windows、MacOs）的自动化项目构建方式
   ![[image-20250421174627359.png]]

3. 统一项目结构：提供标准、统一的项目结构
   ![[image-20250421174836163.png|400]]
## 介绍

![image-20250421175155186](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250421175155186.png)

仓库：用于存储资源，管理各种jar包。

- 本地仓库：自己计算机上的一个目录。
- 中央仓库：由Maven团队维护的全球唯一的。仓库地址：https://repo1.maven.org/maven2/
- 远程仓库（私服）：一般由公司团队搭建的私有仓库。

![[image-20250421175452717.png|800]]

## 创建Maven项目

- 创建模块，选择New Module，填写模块信息，选择构建工具为Maven，点击create，创建完成
- 编写 HelloWorld，并运行

## Maven坐标

1. 什么是坐标?
   - Maven中的坐标是`资源（jar）的唯一标识`，通过该坐标可以`唯一定位资源位置`。
   - 使用坐标来`定义项目`或`引入项目中需要的依赖`
2. Maven坐标主要组成
   - groupId：定义当前Maven项目隶属`组织名称`（通常是域名反写，例如：com.itheima）
   - artifactId：定义当前Maven`项目名称`（通常是`模块名称`，例如order-service、goods-service）
   - version：定义当前`项目版本号`
     1. SNAPSHOT:  功能不稳定、尚处于开发中的版本，即`快照版本`
     2. RELEASE：功能趋于稳定、当前更新停止，可以用于`发行的版本`

## 导入Maven项目

1.  方式一：`File` -> `Project Structure` -> `Modules `-> `Import Module` -> `选择maven项目的pom.xml`。
2. 方式二：`Maven面板`  -> `+` (Add Maven Projects) -> `选择maven项目的pom.xml`。

## 依赖配置

- 依赖：指当前项目运行所需要的jar包，一个项目中可以引入多个依赖


- 配置:
  - 1．在 pom.xml 中编写`<dependencies>`标签
  - 2.在`<dependencies>`标签中使用`<dependency>`引入坐标
  - 3.定义坐标的`groupId`, `artifactId`, `version`
  - 4.点击刷新按钮，引入最新加入的坐标

> 如果不知道依赖的坐标信息，可以到 https://mvnrepository.com/ 中搜索。

### 排除依赖

- 排除依赖：指主动断开依赖的资源，被排除的资源`无需指定版本`。

  ```xml
  <dependency>
  	<exclusions>
  		<exclusion>
  			<groupId>io.micrometer</groupId>
  			<artifactId>micrometer-observation</artifactId>
  		</exclusion>
  	</exclusions>
  </dependency>
  ```

> 注意事项
>
> - 一旦依赖配置变更了，记得重新加载
> - 引入的依赖本地仓库不存在，记得联网

## 生命周期

- Maven的生命周期就是为了对所有的Maven项目`构建过程`进行`抽象和统一`。

- Maven中有3套相互独立的生命周期:
  1. `clean`：清理工作。
  2. `default`：核心工作，如：编译、测试、打包、安装、部署等。
  3. `site`：生成报告、发布站点等。

![[image-20250421193336618.png|1000]]

![[image-20250421193403973.png]]

> `在同一套生命周期中，当运行后面的阶段时，前面的阶段都会运行。`

- 执行指定生命周期的两种方式：

  1. 在idea中，右侧的maven工具栏，选中对应的生命周期，双击执行。
  2. 在命令行中，通过命令执行。

  ```bash
  <maven-project> mvn clean
  <maven-project> mvn compile
  ```

## 常见问题

![image-20250421204831036](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250421204831036.png)



# 测试

## 概述

- 测试：是一种用来促进鉴定软件的`正确性、完整性、安全性和质量`的过程。
- 阶段划分：`单元测试、集成测试、系统测试、验收测试。`
  1. 单元测试
     - 介绍：对软件的`基本组成单位`进行测试，`最小测试单位`。
     - 目的：检验软件`基本组成单位的正确性`。
     - 测试人员：开发人员
  2. 集成测试
     - 介绍：将已分别通过测试的`单元`，按设计要求`组合成系统或子系统`，再进行的测试。
     - 目的：检查`单元之间的协作`是否正确。
     - 测试人员：开发人员
  3. 系统测试
     - 介绍：对已经`集成好的软件系统`进行彻底的测试。
     - 目的：验证软件`系统的正确性`、性能是否满足指定的要求。
     - 测试人员：测试人员
  4. 验收测试
     - 介绍：交付测试，是针对用户需求、业务流程进行的正式的测试。
     - 目的：验证软件系统是否满足验收标准。
     - 测试人员：客户/需求方
- 测试方法：`白盒测试、黑盒测试 及 灰盒测试`
  1. 白盒测试
     - 清楚软件内部结构、代码逻辑。
     - 用于`验证代码`、`逻辑正确性`
  2. 黑盒测试
     - 不清楚软件内部结构、代码逻辑。
     - 用于验证`软件的功能`、`兼容性`等方面。
  3. 灰盒测试
     - 结合了白盒测试和黑盒测试的特点，既关注软件的内部结构又考虑外部表现（功能）

![image-20250421194728077](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250421194728077.png)

## 单元测试

- 单元测试：就是针对最小的功能单元(方法），编写测试代码对其正确性进行测试。
- `JUnit`：最流行的`Java`测试框架之一，提供了一些功能，方便程序进行单元测试（第三方公司提供）。
  1. 测试代码与源代码分开，便于维护
  2. 可根据需要进行自动化测试
  3. 可自动分析测试结果，产出测试报告

### 使用JUnit

- 在`pom.xml`中，引入`JUnit`的依赖。

  ```xml
  <dependency>
  <groupId>org.junit.jupiter</groupId>
  <artifactId>junit-jupiter</artifactId>
  <version>5.9.1</version>
  </dependency>
  ```

- 在`test/java`目录下，创建测试类，并编写对应的测试方法，并在方法上声明`@Test`注解。
  **JUnit单元测试类名命名规范为：XxxxxTest【规范】。JUnit单元测试的方法，必须声明为 public Void【规定】。**

  ```java
  @Test
  public void testGetAge(){
  	Integer agee = newUserService().getAge（"110002200505091218");
  	System.out.prihtln(age);
  }
  ```

- 运行单元测试（测试通过：绿色；测试失败：红色）

#### 断言

- JUnit提供了一些辅助方法，用来帮我们确定被测试的方法是否按照预期的效果正常工作，这种方式称为断言。

![image-20250421202039312](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250421202039312.png)

#### 常见注解

- 在JUnit中还提供了一些注解，还增强其功能，常见的注解有以下几个:

![image-20250421202533081](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250421202533081.png)

![image-20250421202843307](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250421202843307.png)

### 企业测试规范

- 原则：编写测试方法时，要尽可能的覆盖业务方法中所有可能的情况(尤其是边界值）。

### 依赖范围

- 依赖的jar包，默认情况下，可以在任何地方使用。可以通过 <scope>.</scope>设置其作用范围。
- 作用范围:
  1. 主程序范围有效。（main文件夹范围内）
  2. 测试程序范围有效。(test文件夹范围内）
  3. 是否参与打包运行。(package指令范围内）

```xml
<dependency>
	<groupId>org.junit.jupiter</groupId>
	<artifactId>junit-jupiter</artifactId>
	<version>5.9.3</version>
	<scope>test</scope>
</dependency>
```

![[image-20250421204410091.png]]
