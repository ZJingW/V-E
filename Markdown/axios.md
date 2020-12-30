**axios Api**
**--------------------------------------**
axios的两种形式发送http请求
1. axios(config)


2. 另一种是分别通过 axios 对象提供的与 HTTP 方法对应的方法来发起请求，如： axios.get() , axios.post() , axios.delete()

```
axios.get(url)
axios.post(url,data)
axios.delete(url)
axios.update(url)
axios.put(url,data)
```
**----------------------------------------**

- axios(config) 方法接收一个对象，这个对象包含了一些**对请求的配置**， axios 会根据这些配置来发送对应的 HTTP 请求。

最基本的配置项应该包括：
```
1. method 请求的方法（可选值： get , post 等）
2. url 请求的地址 （必须项）
3. data 请求发送的数据（post等请求需要）

```
`默认的请求方法是get所以如果是get请求可以不设置method`

```js
// 发送 GET 请求 默认的方法
axios('/user/12345');
  
```
`请求响应的处理在 then 和 catch 回调中，请求正常会进入 then ，请求异常则会进 catch`
```js
// 发送 POST 请求
axios({
  method: 'post',
  url: '/user/12345',
  data: {
    firstName: 'Fred',
    lastName: 'Flintstone'
  }
}).then(res => {  //返回了一个响应的对象，一个响应的对象的结构在下文进行说明
    consloe.log(res)
}).catch(err => {
    console.log(err)
})

```
其实就是axios(congfig)接受了一个对象，规定了http请求的配置信息。然后axios自动按照axios的配置信息自动的发送了相应的http请求。请求成功就执行then，请求异常就执行catch方法。


**-------------------------------**
```js
// 为给定 ID 的 user 创建请求
axios.get('/user?ID=12345').then(function (response) {
  console.log(response);
}).catch(function (error) {
  console.log(error);
});

```
```js
发送post请求
axios.post('/user', {
  firstName: 'Fred',
  lastName: 'Flintstone'
}).then(function (response) {
  console.log(response);
}).catch(function (error) {
  console.log(error);
});

```
**---------------------------**

**响应的结构**
`通过 axios 发出的请求的响应结果中， axios 会加入一些字段，如下`

```js
{
  // `data` 由服务器提供的响应
  data: {},
  // `status` 来自服务器响应的 HTTP 状态码
  status: 200,
  // `statusText` 来自服务器响应的 HTTP 状态信息
  statusText: 'OK',
  // `headers` 服务器响应的头
  headers: {},
   // `config` 是为请求提供的配置信息
  config: {},
 // 'request'
  // `request` is the request that generated this response
  // It is the last ClientRequest instance in node.js (in redirects)
  // and an XMLHttpRequest instance the browser
  request: {}
}
处。
//一般我们只需要关注data字段就可以！！！！
```

`对于axios的使用只要掌握axios().api的基本使用就好了`