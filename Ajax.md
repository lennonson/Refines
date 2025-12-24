# Ajax

- 介绍:`Asynchronous JavaScript And XML`, 异步 的JavaScript和XML
- 作用：
  - 数据交换：通过Ajax可以给服务器发送请求，并获取服务器响应的数据。
  - 异步交互：可以在`不重新加载整个页面`的情况下，与服务器交换数据并`更新部分网页`的技术，如：搜索联想、用户名是否用的校验等等。

## Axios

- 介绍：Axios 又对原生的Ajax进行了封装，简化书写，快速开发。

- Axios是一个基于`promise`网络请求库，作用于node.js和浏览器中。它是`isomorphic`的（即同一套代码可以运行在浏览器和node.js
  中)。在服务端它使用原生`node`,`js`,`http`模块，而在客户端（浏览端）则使用`XML`,`Http`,`Requests`。

- 官网: https://www.axios-http.cn/

- 步骤：

  - 引入Axios的js文件（参照官网）
    `<script src="https://unpkg.com/axios/dist/axios.min.js"></script>`
  - 使用Axios发送请求，并获取响应结果

```js
  axios({
  	method:：'GET'
  	url:'https://web-server.itheima.net/emps/list
  }).then((result) => {
  	console.log(result.data);
  }).catch((err) => {
  	alert(err);
  });
  ```

### Axios-请求方式别名

- 为了方便起见，Axios已经为所有支持的请求方法提供了别名

- 格式：`axios.请求方式 (url ［, data [, config]])`

```js
  // GET
  axios.get('https://mock.apifox.cn/m1/3083103-0-default/emps/list').then((result)=>{
  	console.log(result.data) ;
  }).catch((err）=>{
  	console.log(err);
  );
  // POST 推荐
  axios.post('https://mock.apifox.cn/m1/3083103-0-default/emps/update','id=1').then((result) =>{
  	console.log(result.data) ;
  }).catch((err)=>{
  	console.log(err);
  );
```
### async & await

- 可以通过`async`、`await`可以让异步变为同步操作。`async`就是来声明一个`异步`方法，`await`是用来`等待异步`任务执行。

- e.g

  ```js
  methods:{
    async search(){
      //根据用户输入的搜索条件，基于axios发送异步请求（https://web-server.itheima.net/emps/List)到服务端.
  	let result await axios.get('https://web-server.itheima.net/emps/list?	   name=xxx&gender=xxx&job=xxx');
  	this.employees = result.data.data;
    }
  }
  ```

  



