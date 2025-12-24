Vue是一款用于构建用户界面的渐进式的JavaScript框架(官方: https://cn.vuejs.org/)
![Pasted image 20250418225715](D:\refines\refines\code\attachments\Pasted image 20250418225715.png)

- 框架：就是一套完整的项目解决方案，用于快速构建项目
- 优点：大大提升前端项目的开发效率
- 缺点：需要理解记忆框架的使用规则(参照官网）
## 快速入门

准备
- 引入Vue模块（官方提供）
- 创建Vue程序的应用实例，控制视图的元素
- 准备元素（div），被Vue控制
```vue
%% 模块化 module %%
<div id="app">
	<h1>{{message}}</h1>
</div>
<script type="module">
	import {createApp} from'https://unpkg.com/vue@3/dist/vue.esm-browser.js';
	createApp({
		data() {
			return {
				message: "Hello Vue"
			}
		}
	}).mount("#app");
</script>
```

数据驱动视图
- 准备数据
- 通过插值表达式渲染页面
## 常用指令

- 指令：HTML标签上带有有V-前缀的特殊属性、不同的指令具有不同的含义，可以实现不同的功能。

![Pasted image 20250418231155](D:\refines\refines\code\attachments\Pasted image 20250418231155.png)

### v-for
- 作用：列表渲染，遍历容器的元素或者对象的属性
- 语法:
```html
  <tr v-for="(item,index） in items" :key="item.id">{{item}}</tr>
```
- 参数说明：
	1. items 为遍历的数组
	2. item为遍历出来的元素
	3. index 为索引l/下标，从o开始；可以省略，省略index语法:v-for="item in items
- key:
	- 作用：给元素添加的唯一标识，便于vue进行列表项的正确排序复用，提升渲染性能
	- 推荐使用id作为key（唯一），不推荐使用index作为key（会变化，不对应)
> - 遍历的数组，必须在data中定义;要想让哪个标签循环展示多次，就在哪个标签上使用用v-for 指令。

### v-bind
- 作用：动态为HTML标签绑定属性值，如设置href，src，style样式等。
- 语法：V-bind:属性名="属性值"
- 简化：：属性名="属性值"
```html
  <img v-bind:src="item.image"width="30px">
  <img :src="item.image"width="30px">
```
> - 动态的为标签的属性绑定值，不能使用插值表达式，得使用v-bind指令。且绑定的数据，必须在data中定义。

### v-if & v-show
- 作用：这两类指令，都是用来控制元素的显示与隐藏的
- v-if
	- 语法：`V-if="表达式"`，表达式值为true，显示；false，隐藏
	- 原理：基于条件判断，来控制创建或移除元素节点京（条件渲染）
	- 场景：要么显示，要么不显示，不频繁切换的场景
- v-show
	- 语法：`V-show="表达式"`，表达式值为true，显示；false，隐藏
	- 原理：基于cSs样式display来控制显示与隐藏
	- 场景：频繁切换显示隐藏的场景

### v-model

- 作用：在表单元素上使用，双向数据绑定。可以方便的获取或设置表单项数据

- 语法：`V-model="变量名"`

  > V-model中绑定的变量，必须在data中定义，

### v-on

- 作用：为html标签绑定事件(添加事件监听）

- 语法:

  - v-on: `事件名="方法名`
  - 简写为`@事件名=".."`

  > methods函数中的this指向Vue实例，可以通过this获取到data中定义的数据。

## Vue生命周期

<img src="https://cn.vuejs.org/assets/lifecycle_zh-CN.W0MNXI0C.png" alt="组件生命周期图示" style="zoom: 50%;" />

- 生命周期的八个阶段：每触发一个生命周期事件，会自动执行一个生命周期方法(钩子)



## 开发流程
![a2d5d301-a1a6-4d7d-9c4a-daa2e979db98](D:\refines\refines\a2d5d301-a1a6-4d7d-9c4a-daa2e979db98.png)

其中`*.vue`是Vue项目中的组件文件，在Vue项目中也称为单文件组件（[SFC](https://cn.vuejs.org/guide/scaling-up/sfc.html)，Single-File Components）。Vue 的单文件组件会将一个组件的逻辑 (JS)，模板 (HTML) 和样式 (CSS) 封装在同一个文件里（`*.vue`）
![ad3eccd6-b65c-430b-860a-3ce3e6c77f9f](D:\refines\refines\ad3eccd6-b65c-430b-860a-3ce3e6c77f9f.png)

## API风格
- Vue的组件有两种不同的风格：**组合式API** 和 **选项式API**

### 组合式API：

​		是Vue3提供的一种基于函数的组件编写方式，通过使用函数来组织和复用组件的逻辑。它提供了一种更灵活、更可组合的方式来编写组件。代码形式如下：

```HTML
<script setup>
import { ref, onMounted } from 'vue';
const count = ref(0); //声明响应式变量

function increment(){ //声明函数
   count.value++;
}

onMounted(() => { //声明钩子函数
  console.log('Vue Mounted....'); 
})
</script>

<template>
   <input type="button" @click="increment"> Api Demo1 Count : {{ count }}
</template>

<style scoped>
   
</style>
```
> - `setup`：是一个标识，告诉Vue需要进行一些处理，让我们可以更简洁的使用组合式API。
> - `ref()`：接收一个内部值，返回一个响应式的ref对象，此对象只有一个指向内部值的属性 value。 
> - `onMounted()`：在组合式API中的钩子方法，注册一个回调函数，在组件挂载完成后执行。

### **选项式API**

​		**选项式API：**可以用包含`多个选项`的对象来描述组件的逻辑，如：`data`，`methods`，`mounted`等。选项定义的属性都会暴露在函数内部的`this`上，它会指向当前的组件实例。

```html
<script>
export default{
   data() {
      return {
         count: 0
      }
   },
   methods: {
      increment: function(){
         this.count++
      }
   },
   mounted() {
      console.log('vue mounted.....');
   }
}
</script>

<template>
  <input type="button" @click="increment">Api Demo1 Count :  {{ count }}
</template>

<style scoped>

</style>
```

> 在Vue中的组合式API使用时，是`没有this对象`的，this对象是`undefined`。 

## 前后端分离开发

<img src="D:\refines\refines\1280X1280.PNG" alt="1280X1280" style="zoom:67%;" />

## VueRouter

- Vue Router：Vue的`官方路由`。 为Vue提供富有表现力、可配置的、方便的路由。
- Vue中的路由，主要定义的是`路径与组件之间的对应关系`。

<img src="D:\refines\refines\18a20ef7-d786-4475-a9b0-e269f275abaa.png" alt="18a20ef7-d786-4475-a9b0-e269f275abaa" style="zoom:67%;" />

- `Vue Router`：路由器类，根据路由请求在路由视图中动态渲染选中的组件
- `<router-link>`：请求链接组件，浏览器会解析成`<a>`
- `<router-view>`：动态视图组件，用来渲染展示与路由路径对应的组件
