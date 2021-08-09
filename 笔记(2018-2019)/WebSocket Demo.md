### 一、WebSocket 是一种应用层协议

- `WebSocket` 与 `http` 都是属于应用层的协议，且数据传输都是基于 `TCP/IP` 的，所以它们都是可靠协议。

- `WebSocket` 在建立握手连接时，数据是采用 `http` 协议传输的；在建立连接后，才会采用 `WebSocket`协议传输。

- [TCP 协议如何保证可靠传输](https://www.jianshu.com/p/6aac4b2a9fd7)

#### 下列是只建立 `WebSocket` 连接，不进行后续通讯的 `Network`

#### General
```
Request URL: ws://127.0.0.1:5500/index.html/ws
Request Method: GET
Status Code: 101 Switching Protocols
```

#### Response Headers
```c
HTTP/1.1 101 Switching Protocols  // 服务器根据客户端的请求切换协议
Connection: Upgrade
Sec-WebSocket-Accept: v+r2/IUOxl1FVHZstUqfRinPX3k=
Upgrade: websocket  // 服务端已经理解了客户端的需求，并通知客户端采用websocket协议来完成这个请求
// 在发送完这个响应最后的空行后，服务器将会切换到到 Upgrade 消息头中定义协议进行后续通讯，即websocket协议
```

#### Request Headers
```c
GET ws://127.0.0.1:5500/index.html/ws HTTP/1.1  // http协议，发送GET请求
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8
Cache-Control: no-cache
Connection: Upgrade
Host: 127.0.0.1:5500
Origin: http://127.0.0.1:5500
Pragma: no-cache
Sec-WebSocket-Extensions: permessage-deflate; client_max_window_bits
Sec-WebSocket-Key: vOnSp0OUz4cQ+Zn5lFdNbg==
Sec-WebSocket-Version: 13
Upgrade: websocket
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X xx_xx_x) AppleWebKit/xxx.xx (KHTML, like Gecko) Chrome/xx.x.xxxx.xx Safari/537.36
```

> HTTP 101 状态码：
>
> `HTTP 101` 状态码英文名称是 `Switching Protocols`，表示切换协议。服务器根据客户端的请求切换协议。只能切换到更高级的协议，例如，切换到HTTP的新版本协议。
>
> 服务器已经理解了客户端的请求，并将通过 `Upgrade` 消息头通知客户端采用不同的协议来完成这个请求。在发送完这个响应最后的空行后，服务器将会切换到在 `Upgrade`  消息头中定义的那些协议。
>
> 只有在切换新的协议更有好处的时候才应该采取类似措施。例如，切换到新的 `HTTP`  版本比旧版本更有优势，或者切换到一个实时且同步的协议以传送利用此类特性的资源。

### 二、WebSocket 协议

#### 1. 解决痛点

#### 2. 相对于 HTTP 通讯的优/缺点

#### 3. 客户端/服务端对 `WebSocket` 协议的支持情况

[WebSocket 详解教程](https://www.cnblogs.com/jingmoxukong/p/7755643.html#%E8%B5%84%E6%96%99)
[WebSocket 教程](http://www.ruanyifeng.com/blog/2017/05/websocket.html)

### 三、前端 demo

```javascript
// var wsUri = "ws://echo.websocket.org/"
var wsUri = 'ws://172.16.7.17:9988/'

var output
var dataReceive = {}

function init() {
    output = document.getElementById("output")
    testWebSocket();
}

function testWebSocket() {
    websocket = new WebSocket(wsUri)
    websocket.onopen = function (evt) {
        onOpen(evt)
    }
    websocket.onclose = function (evt) {
        onClose(evt)
    }
    websocket.onmessage = function (evt) {
        // onMessage(evt)
    }
    websocket.onerror = function (evt) {
        // onError(evt)
    }
}

function onOpen(evt) {
    writeToScreen("onopen: CONNECTED")
    // let msg = JSON.stringify({
    //     name: 'admin',
    //     password: '123456',
    //     version: '1.0.0'
    // })
    // doSend(msg);
}

function onClose(evt) {
    writeToScreen("onclose: DISCONNECTED");
}

function onMessage(evt) {
    writeToScreen('<span style="color: blue;">onmessage: RESPONSE: ' + evt.data + '</span>');
    dataReceive = JSON.parse(evt.data);
    console.log(dataReceive);
    websocket.close();
}

function onError(evt) {
    writeToScreen('<span style="color: red;">ERROR:</span> ' + evt.data);
}

function doSend(message) {
    writeToScreen("SENT: " + message);
    websocket.send(message);
}

function writeToScreen(message) {
    var pre = document.createElement("p");
    pre.style.wordWrap = "break-word";
    pre.innerHTML = message;
    output.appendChild(pre);
}

window.addEventListener("load", init, false);
```