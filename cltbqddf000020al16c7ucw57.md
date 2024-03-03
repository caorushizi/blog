---
title: "前端基础知识体系 跳槽大厂必备"
datePublished: Sun Mar 03 2024 16:32:35 GMT+0000 (Coordinated Universal Time)
cuid: cltbqddf000020al16c7ucw57
slug: 5ymn56uv5z656ga55l6kg5l2t57o7ioi3sanvewkpwoguwhewkhw
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709484835708/2e8def4d-2166-4903-852e-cf5da21b1470.png

---

HTML 和 CSS 原型、作用域、异步 DOM 事件和 Ajax 性能优化 手写各种代码 HTTP 协议

# **HTML 和 CSS**

## **如何理解 HTML 语义化**

* 让人更容易读懂（增加代码的可读性）
    
* 让搜索引擎更容易读懂（SEO）
    

## **块状元素 & 内联元素**

* display:block/table; 有 div h1 h2 table ul ol p 等
    
* display:inline/inline-block 有 span img input button 等
    

## **盒模型宽度的计算**

![image.png](https://static.ziying.site/yuque_img_upload/5680afbf-efc8-3a37-bd28-7230752d8e73.png align="left")

offsetWidth = （内容宽度 + 内边距 + 边框），无外边距 box-sizing: border-box

## **margin 纵向重叠**

![image.png](https://static.ziying.site/yuque_img_upload/aa747b48-2be6-3a72-bd5c-301be15d1da0.png align="left")

相邻元素的 margin-top 和 margin-bottom 会发生重叠 空内容的 p 标签也会发生重叠

## **margin 负值的问题**

margin-top 和 margin-left 负值，元素向上、向左移动 margin-right 负值，右侧元素左移，自身不受影响 margin-bottom 负值，下方元素上移，自身不受影响

## **BFC 理解与应用**

block format context， 块级格式化上下文 一个独立渲染的区域，内部元素的渲染不会影响边界以外的元素

形成 bfc 的常见条件

* float 不是 none
    
* position 是 absolute 或者 fixed
    
* overflow 不是 visible
    
* display 是 flex inline-block
    

常见应用：

* 清除浮动
    

## **实现圣杯布局和双飞翼布局**

三栏布局：中间一栏最先加载和渲染（内容最为重要） 两侧内容固定，中间内容随着宽度自适应 一般用于 PC 网页

* 圣杯布局和技术总结
    

使用 float 布局 两侧使用 margin 负值，以便和中间内容横向重叠 防止中间内容被两侧覆盖，圣杯布局使用 padding，双飞翼布局使用 margin

## **手写 clearfix**

```css
/* 手写clearfix */
.clearfix:after {
    content: "";
    display: table;
    clear: both;
}

.clearfix {
    *zoom: 1; /* 兼容IE低版本 */
}
```

## **flex 布局**

```css
.box {
    width: 200px;
    height: 200px;
    border: 2px solid #ccc;
    border-radius: 10px;
    padding: 20px;

    display: flex;
    justify-content: space-between;
}

.item {
    display: block;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: #666;
}

.item:nth-child(2) {
    align-self: center;
}

.item:nth-child(3) {
    align-self: flex-end;
}
```

## **absolute 和 relative 定位**

relative 依据自身定位 absolute 依据最近一层的元素定位

定位元素： absolute，relative，fixed body

## **居中对齐的实现方式**

* 水平居中
    

inline 元素：text-align ：center block 元素：margin：auto absolute 元素：left：50%；+margin-left：负值

* 垂直居中
    

inline 元素：line-height 的值等于 height 的值 absolute 元素：top50% + margin-top：负值 absolute 元素： transform：translate（-50%，-50%） absolute 元素：top，left，bottom，right = 0 + margin：auto

## **line-height 如何继承**

如果写具体数值，如 30px，则继承该值（比较容易理解） 如果写比例，如 2/1.5，则继承该比例 如果写百分比，如 200%，则继承计算出来的值

## **rem 是什么**

* rem 是一个长度单位，
    
    * px 是绝对长度单位，最常用
        
    * em 相对长度单位，相对于父元素，不常用
        
    * rem，相对长度单位，相对于根元素，常用语响应式布局
        

响应式布局的常用方案 media-query 根据不同的屏幕宽度设置根元素的 font-size rem 基于根元素的相对单位

* rem 弊端，“阶梯”性
    

网页的视口尺寸 window.screen.height // 屏幕高度 window.innerHeight // 网页视口高度 document.body.clientHeight // body 高度

vh 网页视口高度的 1/100 vw 网页视口高度的 1/100 vmax 取两者的最大值，vmin 取两者的最小值

## **CSS3 动画**

# **JS 基础，变量类型和计算**

## **typeof 能判断那些类型**

值类型

![image.png](https://static.ziying.site/yuque_img_upload/21b0c693-4688-337a-aeaa-9831093c38c3.png align="left")

引用类型

![image.png](https://static.ziying.site/yuque_img_upload/574d1e7b-9649-3714-a2a2-e676a204286c.png align="left")

值类型有那些 undefined，string，number，boolean，symbol

引用类型有哪些 object array null function

typeof 运算符

* 识别所有的值类型，
    
* 识别函数
    
* 判断是不是引用类型（不可再细分）
    

## **手写 js 深拷贝**

```javascript
const obj1 = {
    age: 20,
    name: "",
    addresss: {
        city: "beijing",
    },
};

const obj2 = obj1;

function deepClone(obj = {}) {
    if (typeof obj !== "object" || obj == null) {
        return obj;
    }

    let result;
    if (obj instanceof Array) {
        result = [];
    } else {
        result = {};
    }

    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            result[key] = deepClone(obj[key]);
        }
    }

    return result;
}
```

## **类型转换**

* 字符串拼接
    
* \==
    
* if 语句和逻辑运算
    

除了==null，其他地方都用===

0，NaN，""，null，undefined，false，其他均为 truly

# **原型和原型链**

## **原型关系**

每个 class 都有显示原型 prototype 每个实例都有隐式原型**proto** 实例的隐式原型都指向对应 class 的显示原型

![image.png](https://static.ziying.site/yuque_img_upload/7466d3b7-0890-35ed-ac7b-792e959e7d8b.png align="left")

获取属性 name 或者执行方法的时候，现在自身的属性或者方法中寻找，找不到就自动从隐式原型中寻找

## **原型链**

![image.png](https://static.ziying.site/yuque_img_upload/970eb8cd-af1e-37dd-b186-000709a04525.png align="left")

![image.png](https://static.ziying.site/yuque_img_upload/6debd27a-5784-3f97-aef9-be5eb540653b.png align="left")

## **如何判断一个变量是数组**

a instanceof Array

# **作用域和闭包**

## **闭包**

* 函数作为参数，
    
* 函数作为返回值
    

this 是在函数执行的地方决定的

## **手写 bind 函数**

```javascript
Function.prototype.bind1 = function () {
    const args = Array.prototype.slice.call(arguments);
    const t = args.shift();

    const self = this;

    // 返回一个函数
    return function () {
        return self.apply(t, args);
    };
};
```

闭包的应用

* 隐藏数据
    

# **异步**

## **单线程和异步**

js 是单线程语言，只能同时做一件事儿 浏览器和 nodejs 已经支持 js 启动进程，如 Web Worker js 和 DOM 渲染共同使用一个线程，因为 JS 可修改 DOM 的结构

遇到等待，（网络请求，定时任务）不能卡住 需要异步 回调 callback 函数形式

## **异步的应用场景**

网络请求，ajax 图片加载 定时任务 setTimeout

# **异步进阶**

## **event loop**

js 是单线程运行的 异步要基于回调来实现 event loop 就是异步回调的实现原理

## **js 如何执行**

* 从前到后，一行一行执行
    
* 如果某一行执行报错，则停止下面代码的执行
    
* 先把同步代码执行完，再执行异步
    

![image.png](https://static.ziying.site/yuque_img_upload/fb3ee556-bad9-35b2-a64d-87aa835b5d92.png align="left")

* 同步代码，一行一行放在 call stack 执行
    
* 遇到异步，先记录下，等待时机（定时、网络请求等）
    
* 时机到了，就移动到 Callback Queue 中
    
* 如果 Call Stack 为空，（即同步代码执行完）Event Loop 开始工作
    
* 轮询查找 CallBack Queue ，如有则移动到 Call Stack 执行
    
* 然后继续轮询查找
    

## **DOM 事件和 event loop**

* JS 是单线程的
    
* 异步（setTimeout,ajax 等）使用回调，基于 event loop
    
* DOM 事件也使用回调，基于 event loop
    

## **Promise 的三种状态**

pending fulfilled rejected

![image.png](https://static.ziying.site/yuque_img_upload/fc0a1309-90ac-39d1-95aa-909f2f2fd7a8.png align="left")

## **async/await 和 Promise 的关系**

* 执行 async 函数，返回的是 Promise 对象
    
* await 相当于 Promise 的 then
    
* try catch 可不会异常，代替了 Promise 的 catch
    

## **什么是宏任务，什么是微任务**

宏任务：setTimeout，setInterval，Ajax，DOM 事件 微任务：Promise，async await 微任务执行时机比宏任务要早

## **event loop 和 DOM 渲染**

* 再次回归一遍 event loop 的过程
    
* JS 是单线程的，而且和 DOM 渲染公用一个线程
    
* JS 执行的时候，需要留一些事件给 DOM 渲染
    

1. call stack 空闲
    
2. 尝试 DOM 渲染
    
3. 触发 event loop
    

## **微任务和宏任务的区别**

宏任务： DOM 渲染后触发，如 setTimeout 微任务： DOM 渲染前触发，如 Promise

## **微任务和宏任务的根本区别**

微任务是 ES6 语法规定， 宏任务是由浏览器规定

宏任务放在 webapi 的空间中 微任务放在 micro task queue 中

1. call stack 清空
    
2. 执行当前的微任务
    
3. 尝试 DOM 渲染
    
4. 触发 Event Loop
    

## **Promise 的问题**

```javascript
async function async1() {
    console.log("async1 start");
    await async2();
    console.log("async1 end");
}

async function async2() {
    console.log("async2");
}

console.log("script start");

setTimeout(function () {
    console.log("setTimeout");
}, 0);

async1();

new Promise(function (resolve) {
    console.log("promise1");
    resolve();
}).then(function () {
    console.log("promise2");
});

console.log("script end");
```

## **手写 Promise**

```javascript
const PENDING = "pending"; // pending
const FULFILLED = "fulfilled"; // fulfilled
const REJECTED = "rejected"; // rejected

export default class MyPromise {
    constructor(executor) {
        try {
            executor(this.resolve, this.reject);
        } catch (e) {
            this.reject(e);
        }
    }

    // promsie 状态
    status = PENDING;
    // 成功之后的值
    value = undefined;
    // 失败后的原因
    reason = undefined;
    // 成功回调
    successCallback = [];
    // 失败回调
    failCallback = [];

    resolve = (value) => {
        // 如果状态不是等待 阻止程序向下执行
        if (this.status !== PENDING) return;
        // 将状态更改为成功
        this.status = FULFILLED;
        // 保存成功之后的值
        this.value = value;
        // 判断成功回调是否存在 如果存在 调用
        while (this.successCallback.length) this.successCallback.shift()();
    };
    reject = (reason) => {
        // 如果状态不是等待 阻止程序向下执行
        if (this.status !== PENDING) return;
        // 将状态更改为失败
        this.status = REJECTED;
        // 保存失败后的原因
        this.reason = reason;
        // 判断失败回调是否存在 如果存在 调用
        // this.failCallback && this.failCallback(this.reason);
        while (this.failCallback.length) this.failCallback.shift()();
    };

    then(successCallback, failCallback) {
        // 参数可选
        successCallback = successCallback ? successCallback : (value) => value;
        // 参数可选
        failCallback = failCallback
            ? failCallback
            : (reason) => {
                throw reason;
            };
        let promsie2 = new MyPromise((resolve, reject) => {
            // 判断状态
            if (this.status === FULFILLED) {
                setTimeout(() => {
                    try {
                        let x = successCallback(this.value);
                        // 判断 x 的值是普通值还是promise对象
                        // 如果是普通值 直接调用resolve
                        // 如果是promise对象 查看promsie对象返回的结果
                        // 再根据promise对象返回的结果 决定调用resolve 还是调用reject
                        resolvePromise(promsie2, x, resolve, reject);
                    } catch (e) {
                        reject(e);
                    }
                }, 0);
            } else if (this.status === REJECTED) {
                setTimeout(() => {
                    try {
                        let x = failCallback(this.reason);
                        // 判断 x 的值是普通值还是promise对象
                        // 如果是普通值 直接调用resolve
                        // 如果是promise对象 查看promsie对象返回的结果
                        // 再根据promise对象返回的结果 决定调用resolve 还是调用reject
                        resolvePromise(promsie2, x, resolve, reject);
                    } catch (e) {
                        reject(e);
                    }
                }, 0);
            } else {
                // 等待
                // 将成功回调和失败回调存储起来
                this.successCallback.push(() => {
                    setTimeout(() => {
                        try {
                            let x = successCallback(this.value);
                            // 判断 x 的值是普通值还是promise对象
                            // 如果是普通值 直接调用resolve
                            // 如果是promise对象 查看promsie对象返回的结果
                            // 再根据promise对象返回的结果 决定调用resolve 还是调用reject
                            resolvePromise(promsie2, x, resolve, reject);
                        } catch (e) {
                            reject(e);
                        }
                    }, 0);
                });
                this.failCallback.push(() => {
                    setTimeout(() => {
                        try {
                            let x = failCallback(this.reason);
                            // 判断 x 的值是普通值还是promise对象
                            // 如果是普通值 直接调用resolve
                            // 如果是promise对象 查看promsie对象返回的结果
                            // 再根据promise对象返回的结果 决定调用resolve 还是调用reject
                            resolvePromise(promsie2, x, resolve, reject);
                        } catch (e) {
                            reject(e);
                        }
                    }, 0);
                });
            }
        });
        return promsie2;
    }

    finally(callback) {
        return this.then(
            (value) => {
                return MyPromise.resolve(callback()).then(() => value);
            },
            (reason) => {
                return MyPromise.resolve(callback()).then(() => {
                    throw reason;
                });
            }
        );
    }

    catch(failCallback) {
        return this.then(undefined, failCallback);
    }

    static all(array) {
        let result = [];
        let index = 0;
        return new MyPromise((resolve, reject) => {
            function addData(key, value) {
                result[key] = value;
                index++;
                if (index === array.length) {
                    resolve(result);
                }
            }

            for (let i = 0; i < array.length; i++) {
                let current = array[i];
                if (current instanceof MyPromise) {
                    // promise 对象
                    current.then(
                        (value) => addData(i, value),
                        (reason) => reject(reason)
                    );
                } else {
                    // 普通值
                    addData(i, array[i]);
                }
            }
        });
    }

    static resolve(value) {
        if (value instanceof MyPromise) return value;
        return new MyPromise((resolve) => resolve(value));
    }
}

function resolvePromise(promsie2, x, resolve, reject) {
    if (promsie2 === x) {
        return reject(
            new TypeError("Chaining cycle detected for promise #<Promise>")
        );
    }
    if (x instanceof MyPromise) {
        // promise 对象
        // x.then(value => resolve(value), reason => reject(reason));
        x.then(resolve, reject);
    } else {
        // 普通值
        resolve(x);
    }
}
```

# **JS 基础到 JS Web API**

js 基础知识，规定语法（ECMA262 标准） js web api ，网页操作的 API（W3C 标准） 前者是后者的基础，两者结合才能真正实际应用

## **DOM 的本质是什么**

DOM 本质是一棵存在内存中的树

## **获取 DOM 节点**

getElementById getElementsByTagName getElementsByClassName querySelectorAll

## **节点操作**

className nodeName nodeType style.width

getAttribute setAttribute 可以通过 setAttribute 设置 style

property 和 attribute 两种形式的区别

## **DOM 的结构操作**

appendChild 新增移动 parentNode 获取父元素 childNodes [Array.prototype.slice.call](http://Array.prototype.slice.call) removeChild

## **DOM 性能**

* DOM 操作非常“昂贵”，避免频繁的 DOM 操作
    
* 对 DOM 的查询做缓存
    
* 将频繁的操作改为一次性操作 createDocumentFragment
    

# **BOM 操作**

* navigator
    
* screen
    
* location
    
* history
    

## **userAgent**

navigator.userAgent

location.href 整个网址 location.protocol 协议 [location.search](http://location.search) location.hash location.pathname

history.back() history.forward()

# **事件**

div.addEventListener('click', ()=&gt;{})

[e.target](http://e.target) e.preventDefault() e.stopPropagation()

ele.matches

# **Ajax 的核心 API**

XMLHttpRequest

readyState 状态

* 0 未初始化，还没有调用 send 方法
    
* 1 载入，已调用 send 方法，正在发送请求
    
* 2 载入完成，send 方法执行完成，已经接收到全部的响应内容
    
* 3 交互，正在解析响应内容
    
* 4 完成，响应内容解析完成，可以在客户端调用
    

```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "/api", true); // true 是异步的
xhr.onreadystatechange = function () {
    // 这里函数异步执行
    if (xhr.readyState === 4) {
        if (xhr.status === 200) {
            alert(xhr.responseText);
        }
    }
};
xhr.send(null);
```

## **什么是浏览器的同源策略**

* ajax 请求时，浏览器要求当前网页和 server 必须同源（安全）
    
* 同源：协议，域名，端口 三者必须一致
    

加载图片 css js 可无视同源策略

```html
<img src="跨域图片的地址"/>

<link href="跨域的css地址"/>
<script src="跨域的js地址"/>
```

* img 可以统计大点，可以使用第三方统计服务
    
* link script 可以使用 CDN，CDN 一般都是外域
    
* script 可实现 JSONP
    
* 所有的跨域都必须经过 server 端的允许和配合
    
* 未经 server 端允许就实现跨域，说明浏览器有漏洞，危险信号
    

## **实现跨域的常见方案，JSONP 和 CORS**

script 可绕过跨域限制 服务器可以任意动态拼接数据返回 所以，script 就可以后去跨域数据，只要服务端愿意返回

服务端设置 http header

![image.png](https://static.ziying.site/yuque_img_upload/d5d8e9a5-c966-3c81-bd87-63270ca84407.png align="left")

# **JS-Web-API 存储**

描述 cookie localstorage sessionStorage

## **cookie**

本身用于浏览器和 server 通讯 被借用到本地存储 可以使用 document.cookie = '' 开修改

cookie 的缺点

* 存储大小，最大 4KB
    
* http 请求的时候需要发送的服务端，增加请求的数量
    
* 只能使用 document.cookie = '' 来修改，太过于简陋
    

cookie 不设置失效时间的话，关闭当前页面之后就会消失。

localstorage 和 sessionstorage

* HTML5 专门为存储而设计的，最大可存 5M
    
* API 简单易用 setItem,getItem
    
* 不会随着 http 请求被发送出去
    
* localstorage 数据会永久存储，除非代码或手动删除
    
* sessionStorage 数据只存在于当前会话，浏览器关闭则清空
    
* 一般 localstorage 会更多一些
    

# **Http**

## **http 常见状态码有哪些**

分类

* 1XX 服务器收到请求
    
* 2XX 请求成功
    
* 3XX 重定向
    
* 4XX 客户端错误
    
* 5XX 服务端错误
    

常见状态码

* 200 请求成功
    
* 301 永久重定向（配合 location，浏览器自动处理）
    
* 302 临时重定向（配合 location，浏览器自动处理）
    
* 304 资源请求未修改
    
* 404 资源未找到
    
* 403 没有权限
    
* 500 服务器错误
    
* 504 网关超时
    

## **什么是 Restful API**

传统的 methods

* GET 获取服务器数据
    
* POST 向服务器提交数据
    

## **现在的 methods**

get post patch/put delete

Restful API 设计，把每个 URL 当做一个唯一的资源

## **http 常见有哪些 header**

* 常见的 request headers
    
    * Accept 浏览器可接收的数据格式
        
    * Accept-Encoding 浏览器可接收的压缩算法，如 gzip
        
    * Accept-Language 浏览器可以接收的语言，如 zh-CN
        
    * Connection： keep-alive 一次 TCP 连接可以重复使用
        
    * cookie 同域每次请求都会带上 cookie
        
    * Host
        
    * User-Agent 简称 UA，浏览器信息
        
    * Content-Type 发送数据的格式，如 application/json
        
* 常见的 response headers
    
    * Content-Type: 返回数据的格式
        
    * Content-length： 返回数据的大小，多少字节
        
    * Content-Encoding 返回数据的压缩算法 如 gzip
        
    * Set-Cookie
        

缓存相关的 headers

* Cache-Control Expires
    
* Last-Modified If-Modified-Since
    
* Etag If-None-Match
    

## **http 缓存**

强制缓存

![image.png](https://static.ziying.site/yuque_img_upload/bfcc5df5-d7f1-36e8-b65d-19003443991b.png align="left")

Cache-Control

* Response Headers 中
    
* 控制强制缓存的逻辑
    

![image.png](https://static.ziying.site/yuque_img_upload/154c3628-b976-3ffb-ae02-0fec7f8026f0.png align="left")

* max-age
    
* no-cache 不用强制缓存
    
* no-store 不用强制缓存，也不用服务端的缓存
    
* private
    
* public
    

Expires 过时的缓存机制，已经被 cache-control 代替

## **http 协商缓存**

* 服务端缓存策略
    
* 服务端判断客户端资源，是否和服务端资源一样
    
* 一致则返回 304，否则返回 200 和最新资源
    

![image.png](https://static.ziying.site/yuque_img_upload/365c7d11-8694-3af3-b27f-fbf27195d801.png align="left")

资源标识，

* 在 response Headers 中，有两种
    
* Last-Modified 资源最后的修改时间
    
* Etag 资源的唯一标识（一个字符串，类似人类的指纹）
    

Last-Modified（If-Modified-Since）

![image.png](https://static.ziying.site/yuque_img_upload/fbaf7e8b-41b2-3b14-b2a3-2745f69f9268.png align="left")

Etag（If-None-Match）

![image.png](https://static.ziying.site/yuque_img_upload/4413a5b5-233a-39f7-b1b6-84cbcdbd4f39.png align="left")

Last-Modified 和 Etag

* 会有限使用 Etag
    
* Last-Modified 只能精确到秒级
    
* 如果资源被重复生成，而内容不变，则 Etag 更精准
    

![image.png](https://static.ziying.site/yuque_img_upload/542f0cdf-a13f-34c0-8342-14e198bd8b89.png align="left")

* 正常操作：地址栏输入 url，跳转连接，前进后退等
    
* 手动刷新：F5，点击刷新按钮，点击菜单刷新
    
* 强制刷新：ctrl + F5
    

正常操作：强制缓存有效，协商缓存有效 手动刷新：强制缓存失效，协商缓存有效 强制刷新：强制缓存失效，协商缓存失效

## **https**

http 和 https http 是明文传输，敏感信息容易被中间劫持 https = http + 加密，劫持之后也无法解密 现代浏览器一开始强制 https 协议

对称加密： 一个 key 可以负责加密，解密 非对称加密： 一个 key，A 加密之后，只能用 B 来解密 https 同时用到了这两种加密方式

## **https 过程**

https 证书

* 中间人攻击，
    
* 使用第三方证书
    
* 浏览器校验证书
    

![image.png](https://static.ziying.site/yuque_img_upload/1e2a2685-d2fb-36cc-87ec-62f99ff6f187.png align="left")

# **开发环境**

* git
    
* 调试工具
    
* 抓包
    
* webpack babel
    
* linux 常用命令
    

# **运行环境**

## **从输入 URL 到渲染出页面的整个过程**

加载资源的形式

* html 代码
    
* 媒体文件，如图片、视频
    
* javascript css
    

加载资源的过程

* DNS 解析： 域名-&gt;IP 地址
    
* 浏览器根据 IP 地址向服务器发起 http 请求
    
* 服务器处理 Http 请求，并返回给浏览器
    

渲染过程

* 根据 HTML 代码生成 DOM Tree
    
* 根据 CSS 代码生成 CSSOM
    
* 将 DOM Tree 和 CSSOM 整合出 Render Tree
    
* 根据 RenderTree 渲染页面
    
* 遇到 script 标签，则暂停渲染，有限加载并执行 JS 代码，完成再继续
    
* 直至把 Render Tree 渲染完成
    

## **为何把 link 放在 Head 中**

在 DOM 生成完成之前加载，渲染的时候就可以直接按照样式渲染页面

## **为何把 JS 放在 body 最后**

渲染初始化框架之后在解析 js，然后执行 js 逻辑

## **window.onload 和 DOMContentLoaded 有什么区别**

window.onload 页面中的全部资源加载完才会执行，包括图片、视频等 DOMContentLoaded DOM 渲染完即可执行，此时图片视频可能还没有加载完 document

## **前端性能优化有哪些方式**

原则

* 多使用内存、缓存或其他方法
    
* 减少 CPU 计算量，减少网络加载耗时
    
* 空间换时间
    

从何入手

* 让加载更快
    
    * 减少资源体积： 压缩代码 webpack gzip
        
    * 减少访问次数：合并代码，SSR 服务器端缓存渲染，缓存
        
    * 使用更快的网络：CDN
        
* 让渲染更快
    
    * CSS 放在 head 中，JS 放在 body 最下面
        
    * 今早开始执行 JS，用 DOMContentLoaded 触发
        
    * 懒加载（图片懒加载，上滑加载更多）
        
    * 对 DOM 查询进行缓存
        
    * 频繁 DOM 操作，合并到一起插入 DOM
        
    * 节流，防抖
        

资源合并 a.js b.js c.js 合并成一个 abc.js 缓存：

* 静态资源加 hash 后缀，根据文件内容计算 hash
    
* 文件内容不变，则 has 不变，则 url 不变
    
* url 和文件不变，则会自动触发 http 缓存机制，返回 304
    

## **手写防抖**

```javascript
function debounce(fn, delay = 100) {
    let timer = null;

    return function () {
        if (timer) {
            clearTimeout(timer);
        }

        timer = setTimeout(() => {
            fm.apply(this, arguments);
            timer = null;
        }, delay);
    };
}
```

## **节流 throttle**

```javascript
function throttle(fn, delay = 100) {
    let timer = null;

    return function () {
        if (timer) {
            return;
        }

        timer = setTimeout(() => {
            fn.apply(this, arguments);
            timer = null;
        }, delay);
    };
}
```

## **XSS 跨站请求攻击**

* 替换特殊字符，如&lt; 变为 &lt; &gt; 变为&gt;
    
* 前端需要替换，后端也需要替换
    

## **XSRF 攻击**

![image.png](https://static.ziying.site/yuque_img_upload/4cb0d7ff-9f52-3ab2-8df6-1402552d187c.png align="left")

* 使用 post 接口
    
* 增加验证，例如密码，短信验证码，指纹
    

# **面试真题**

## **var let const 区别**

* var 是 es5 语法，let const 是 es6 语法，var 有变量提升
    
* var 和 let 是变量，可修改；const 是常量不可修改
    
* let const 有块级作用域，var 没有
    

## **typeof 能判断那些类型**

* undefined，string，number，boolean，symbol
    
* object （typeof null === 'object'）
    
* function
    

## **列举强制类型转化和隐式类型转换**

* 强制：parseInt parseFloat,toString
    
* 隐式：if，逻辑运算，==，+字符串拼接
    

## **手写深度比较**

```javascript
function isObject() {
    return typeof obj === "object" && obj !== null;
}

function isEqual(obj1, obj2) {
    if (!isObject(obj1) || !isObject(obj2)) {
        return obj1 === obj2;
    }

    if (obj1 === obj2) {
        return true;
    }

    const obj1Keys = Object.keys(obj1);
    const obj2Keys = Object.keys(obj2);

    if (obj1Keys.length === obj2Keys.length) {
        return false;
    }

    for (let key in obj1) {
        const res = isEqual(obj1[key], obj2[key]);
        if (!res) {
            return false;
        }
    }

    return true;
}
```

## **哪些数组方法没有副作用**

concat map slice filter

非纯函数 push pop shift unshift forEach some every reduce

## **函数声明和函数表达式的区别**

* 函数声明： `function fn() {...}`
    
* 函数表达式：`const fn = function () {...}`
    
* 函数声明会在代码执行前进行预加载，而函数表达式不会
    

## **new Object 和 Object.create 的区别**

* {} 等同于 new Object() 原型 Object.prototype
    
* Object.create(null) 没有原型
    
* Object.create({...}) 可以指定原型
    

## **数组打平**

```javascript
function flat(arr) {
    const isDeep = arr.some((item) => item instanceof Array);
    if (!isDeep) {
        return arr;
    }

    const res = [].concat(arr);
    return flat(res);
}
```

## **介绍 RAF requestAnimateFrame**

![image.png](https://static.ziying.site/yuque_img_upload/8980fde7-3b6b-353f-abe5-a7bda69a2243.png align="left")

# **Map 和 Set**

## **有序和无序**

js 中， Object 是无序的，Array 是有序的

有序：操作慢 无序：操作快，但无序 如何结合两者优点呢：二叉树及其变种

## **Map 和 Object 区别**

* API 不同，Map 可以以任意类型作为 key
    
* Map 是有序结构（重要）
    
* Map 操作同样很快
    

![image.png](https://cdn.nlark.com/yuque/0/2021/png/1013391/1634568723057-5a41d5c8-da81-4615-8313-9f65388e2392.png#clientId=uc4948c66-1f61-4&from=paste&height=191&id=XVRpH&margin=%5Bobject%20Object%5D&name=image.png&originHeight=244&originWidth=554&originalType=binary&ratio=1&size=88029&status=done&style=none&taskId=u147fb24d-23ee-42ee-94be-b54e44eefe1&width=433 align="left")

![image.png](https://static.ziying.site/yuque_img_upload/d7fd6b8a-854b-3b05-ba0d-8dc0a1a9198e.png align="left")

## **Set 和 Array 区别**

* API 不同
    
* Set 元素不能重复
    
* Set 是无序结构操作很快
    

![image.png](https://static.ziying.site/yuque_img_upload/3ada9537-1df1-3d75-9b1b-3b422c31e1d7.png align="left")

## **WeakMap 和 WeakSet**

* 弱引用，方式内存泄漏
    
* weakSMap 只能使用对象作为 key，WeakSet 只能用对象作为 value
    
* 没有 forEach 和 size，只能用 add delete has
    

# **DONE**