---
title: "Socket.io"
datePublished: Sun Jan 14 2024 15:56:33 GMT+0000 (Coordinated Universal Time)
cuid: clrdoiahs000708l182zfbyjf
slug: socketio
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709200411018/247f2adf-c27b-4ffc-9cb3-7500ab213d8d.webp

---

翻译自：[https://socket.io/get-started/chat/](https://socket.io/get-started/chat/)

## 开始：聊天应用

这个教程里我们会建立一个聊天应用，[这个教程几乎没有用到Node.js与Socket.io](http://这个教程几乎没有用到Node.js与Socket.io)的基本前置知识，因此它适合于所有知识水平的用户。

### 介绍

---

利用像LAMP（PHP）的通用的网络应用程序堆栈创建一个聊天应用是非常困难的，它涉及了服务器的轮询，跟踪时间戳，因此它就会比websocket慢了很多。

Sockets是很多即时聊天系统的解决方案，它在客户端与服务器之间提供了一个双向交流的渠道。

这意味着服务器可以向客户端推送一些消息，我们的想法是无论何时你写下一些聊天的消息，服务器将获取这些消息，并且将他们推送到所有其他的已连接的客户端。

### 网络框架

---

第一步是设置一个简单的HTML网页，提供表单和消息列表。为此我们将用Node.js的Web框架`express`。确保[Node.js](https://nodejs.org/en/)已经安装在计算机中。

首先我们先新建一个描述我们项目的`package.json`清单文件，我们推荐将它放在一个专用的空目录（我们给它命名为`chat-example`）。

> ```xml
> {
>   "name": "socket-chat-example",
>   "version": "0.0.1",
>   "description": "my first socket.io app",
>   "dependencies": {}
> }
> ```

现在为了更方便的添加我们需要的`dependencies` 依赖关系，我们用`npm install --save`：

> `npm install --save express@4.15.2`

现在`express`已经安装，我们需要新建一个`index.js`文件来设置我们的应用。

> ```xml
> var app = require('express')();
> var http = require('http').Server(app);
> 
> app.get('/', function(req, res){
>   res.send('<h1>Hello world</h1>');
> });
> 
> http.listen(3000, function(){
>   console.log('listening on *:3000');
> });
> ```

这段代码可以解释为以下3部分：

1. 表示初始化`app`作为一个方法处理器,可以供应一个HTTP服务器(见第2行)\\
    
2. 定义了一个路由处理器`/`，当点击我们的网站的主页时就调用这个路由处理器。\\
    
3. 使http服务器监听端口3000。
    

如果你运行`node index.js`你将会看到下面： \[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-c6k0pagq-1603730706921)([https://socket.io/assets/img/chat-1.png](https://socket.io/assets/img/chat-1.png))\]

并且如果你打开浏览器输入地址：[`http://localhost:3000`将看到：](http://localhost:3000将看到：) \[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-hIYX8844-1603730706923)([https://socket.io/assets/img/chat-2.png](https://socket.io/assets/img/chat-2.png))\]

### 提供HTML

---

到目前为止在`index.js`文件中我们称`res.send`并通过它传递一个HTML字符串。如果把整个应用程序的HTML放在这里，我们的代码就会看起来非常混乱。因此,我们将要创建一个`index.html`文件,然后运行它。

然后我们用`sendFile`来重构我们的路由处理器的代码：

> ```xml
> 
> app.get('/', function(req, res){
>     res.sendFile(__dirname + '/index.html');
> });
> ```

然后将下面的内容添加到`index.html`中：

> ```xml
> <!doctype html>
> <html>
>   <head>
>     <title>Socket.IO chat</title>
>     <style>
>       * { margin: 0; padding: 0; box-sizing: border-box; }
>       body { font: 13px Helvetica, Arial; }
>       form { background: #000; padding: 3px; position: fixed; bottom: 0; width: 100%; }
>       form input { border: 0; padding: 10px; width: 90%; margin-right: .5%; }
>       form button { width: 9%; background: rgb(130, 224, 255); border: none; padding: 10px; }
>       #messages { list-style-type: none; margin: 0; padding: 0; }
>       #messages li { padding: 5px 10px; }
>       #messages li:nth-child(odd) { background: #eee; }
>     </style>
>   </head>
>   <body>
>     <ul id="messages"></ul>
>     <form action="">
>       <input id="m" autocomplete="off" /><button>Send</button>
>     </form>
>   </body>
> </html>
> ```

如果你重新运行这个进程（通过ctrl+c结束进程，并且重新运行`node inndex`），然后刷新页面你将会看到这样一个页面：

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-ZfvCHgVh-1603730706924)([https://socket.io/assets/img/chat-3.png](https://socket.io/assets/img/chat-3.png))\]

### 整合Socketio

---

[Socket.io](http://Socket.io)由两部分组成：

* 一个集成（或者在支架上）了Node.js的Http服务器：[`socket.io`](http://socket.io)
    
* 一个在浏览器端加载客户端的库：[`soket.io`](http://soket.io)`-client`
    

在开发期间,[`socket.io`](http://socket.io)自动为我们提供服务,我们会看到,所以现在我们只需要安装一个模块（module）:

> `npm instals --save` [`socket.io`](http://socket.io)

[运行这句话就会安装socket.io](http://运行这句话就会安装socket.io)模块并将依赖项添加到`package.json`文件中。[现在我们编辑`index.js`来使用socket.io](http://现在我们编辑index.js来使用socket.io)：

> ```xml
> var app = require('express')();
> var http = require('http').Server(app);
> var io = require('socket.io')(http);
> 
> app.get('/', function(req, res){
>   res.sendFile(__dirname + '/index.html');
> });
> 
> io.on('connection', function(socket){
>   console.log('a user connected');
> });
> 
> http.listen(3000, function(){
>   console.log('listening on *:3000');
> });
> ```

注意,我用`http`(http服务器)[对象初始化`socket.io`](http://对象初始化socket.io)的一个新实例。然后监听传入套接字的`connection`事件,并且记录到控制台。

现在在index.html中`</body>`之前添加以下片段：

> ```xml
> <script src="/socket.io/socket.io.js"></script>
> <script>
>   var socket = io();
> </script>
> ```

That’s all it takes to load the [socket.io](http://socket.io)\-client, which exposes a io global, and then connect.

Notice that I’m not specifying any URL when I call io(), since it defaults to trying to connect to the host that serves the page.

If you now reload the server and the website you should see the console print “a user connected”. Try opening several tabs, and you’ll see several messages:

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-SkMbkUtv-1603730706925)([https://socket.io/assets/img/chat-4.png](https://socket.io/assets/img/chat-4.png))\]

Each socket also fires a special disconnect event:

> ```javascript
> io.on('connection', function(socket){
>   console.log('a user connected');
>   socket.on('disconnect', function(){
>     console.log('user disconnected');
>   });
> });
> ```

Then if you refresh a tab several times you can see it in action:

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-4VptPAO3-1603730706925)([https://socket.io/assets/img/chat-5.png](https://socket.io/assets/img/chat-5.png))\]

### Emitting events

---

The main idea behind [Socket.IO](http://Socket.IO) is that you can send and receive any events you want, with any data you want. Any objects that can be encoded as JSON will do, and binary data is supported too.

Let’s make it so that when the user types in a message, the server gets it as a chat message event. The scripts section in index.html should now look as follows:

> ```xml
> <script src="/socket.io/socket.io.js"></script>
> <script src="https://code.jquery.com/jquery-1.11.1.js"></script>
> <script>
>   $(function () {
>     var socket = io();
>     $('form').submit(function(){
>       socket.emit('chat message', $('#m').val());
>       $('#m').val('');
>       return false;
>     });
>   });
> </script>
> ```

And in index.js we print out the chat message event:

> ```javascript
> io.on('connection', function(socket){
>   socket.on('chat message', function(msg){
>     console.log('message: ' + msg);
>   });
> });
> ```

The result should be like the following video:

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-ZkQM7NCi-1603730706926)([https://i.cloudup.com/transcoded/zboNrGSsai.mp4](https://i.cloudup.com/transcoded/zboNrGSsai.mp4))\]

### Broadcasting

---

The next goal is for us to emit the event from the server to the rest of the users.

In order to send an event to everyone, [Socket.IO](http://Socket.IO) gives us the io.emit:

> `io.emit('some event', { for: 'everyone' });`

If you want to send a message to everyone except for a certain socket, we have the broadcast flag:

> ```java
> io.on('connection', function(socket){
>   socket.broadcast.emit('hi');
> });
> ```

In this case, for the sake of simplicity we’ll send the message to everyone, including the sender.

> ```javascript
> io.on('connection', function(socket){
>   socket.on('chat message', function(msg){
>     io.emit('chat message', msg);
>   });
> });
> ```

And on the client side when we capture a chat message event we’ll include it in the page. The total client-side JavaScript code now amounts to:

> ```xml
> <script>
>   $(function () {
>     var socket = io();
>     $('form').submit(function(){
>       socket.emit('chat message', $('#m').val());
>       $('#m').val('');
>       return false;
>     });
>     socket.on('chat message', function(msg){
>       $('#messages').append($('<li>').text(msg));
>     });
>   });
> </script>
> ```

And that completes our chat application, in about 20 lines of code! This is what it looks like:

\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-34Kq325Z-1603730706926)([https://i.cloudup.com/transcoded/J4xwRU9DRn.mp4](https://i.cloudup.com/transcoded/J4xwRU9DRn.mp4))\]

### Homework

---

Here are some ideas to improve the application:

* Broadcast a message to connected users when someone connects or disconnects
    
* Add support for nicknames
    
* Don’t send the same message to the user that sent it himself. Instead, append the message directly as soon as he presses enter.
    
* Add “{user} is typing” functionality
    
* Show who’s online
    
* Add private messaging
    
* Share your improvements!
    

### Getting this example

---

You can find it on [GitHub](http://ux.zain-dio.top) here.

> `$ git clone` [`https://github.com/socketio/chat-example.git`](https://github.com/socketio/chat-example.git)