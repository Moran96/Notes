## HTTP缓存策略

> target：协商缓存、强缓存、两种缓存特点、设置方式

### 1. 简介

- http缓存只能缓存get请求响应的资源，特指GET请求。

### 2. 过程

- 第一次请求资源时，服务器返回资源，并在 `respone header` 头中回传资源的**缓存参数**
- 第二次请求时，浏览器判断这些请求参数，命中强缓存就直接200;否则就把请求参数加到 `request header` 头中传给服务器，看是否命中协商缓存，命中则返回304，否则服务器会返回新的资源。

> // TODO 此处可以补充一张流程图

### 3. 强缓存&协商缓存

|分类|强缓存|协商缓存|
|--|--|--|
|缓存存放位置|客户端浏览器|客户端浏览器|
|http状态码|200|304|
|特点|不经过服务端；速度最快；不能及时更新|交由服务器判断是否启用缓存|
|header属性|Pragma/Cache-Control/Expires|ETag/If-Not-Match 、Last-Modified/If-Modified-Since|

### 4. 优点

- 减少了冗余的数据传输，节省网络开销。
- 缓解了服务器的压力， 提高了网站的性能
- 加快了网页加载速度，提升用户体验

### 5. 设置方式

- html文件借助meta控制是否缓存：`<meta http-equiv="cache-control" content="no-cache">` `<meta http-equiv="Cache-Control" content="max-age=7200" />` 这里注意IE兼容
- 静态资源的缓存由web服务器进行配置
- 可使用查询字符串+随机数的方式避开强缓存

参考：[简书: HTTP 缓存](https://www.jianshu.com/p/227cee9c8d15)