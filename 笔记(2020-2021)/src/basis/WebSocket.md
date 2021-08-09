### WebSocket 实现和应用

#### (1)什么是 WebSocket

WebSocket 是 HTML5 中的协议，支持持久连续，http 协议不支持持久性连接。Http1.0 和 HTTP1.1 都不支持持久性的链接，HTTP1.1 中的 keep-alive，将多个 http 请求合并为 1个

#### (2)WebSocket 是什么样的协议?具体有什么优点?

HTTP 的生命周期通过 Request 来界定，也就是 Request 一个 Response，那么在 Http1.0 协议中，这次 Http 请求就结束了。在 Http1.1 中进行了改进，是的有一个 connection： Keep-alive，也就是说，在一个 Http 连接中，可以发送多个 Request，接收多个 Response。 但是必须记住，在 Http 中一个 Request 只能对应有一个 Response，而且这个 Response 是被动的，不能主动发起。 WebSocket 是基于 Http 协议的，或者说借用了 Http 协议来完成一部分握手，在握手阶段 与 Http 是相同的。我们来看一个 websocket 握手协议的实现，基本是 2 个属性，upgrade， connection。

#### 补充

[MDN WebSocket](https://developer.mozilla.org/zh-CN/docs/Web/API/WebSocket)
[Github Moran96](https://github.com/Moran96/RC-car)

总结：

- 构造函数 `WebSocket()`
- 2种方法: `WebSocket.close([code[, reason]])` `WebSocket.send(data)`
- 4种事件: `close` `error` `message` `open`