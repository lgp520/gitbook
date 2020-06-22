## cookie与session

web程序中常需要用到会话跟踪技术，所以才有会话的保持。最常用的技术是cookie与session。cookie通过在客户端记录信息确认身份。与cookie相反，session通过在服务端记录信息记录身份。下文先来介绍cookie及session的原理及其区别。

### cookie

cookie的作用：

- 会话状态管理（如用户登录状态、购物车、游戏分数或其它需要记录的信息）
- 个性化设置（如用户自定义设置、主题等）
- 浏览器行为跟踪（如跟踪分析用户行为等

cookie是客户端的解决方案，其具体流程如下：

![image-20200611200827873](/Users/liguopei/Library/Application Support/typora-user-images/image-20200611200827873.png)

1、用户在浏览器访问一个支持cookie的网站，用户会提交包括用户名在内的个人信息到服务器。

2、服务器向客户端返回相应的超文本与上述的个人信息，且存放在header中。

3、客户端接收到服务器传来的信息之后，会将信息统一保存在统一的目录中。

4、客户端再次向服务器请求时，将保存的cookie存放在http请求头，服务器通过分析cookie信息，得到客户端特有的信息。在访问很多网站登陆界面中，常可以看到“请记住我”就是通过cookie的技术实现的。

web程序中使用的是http协议传输数据的，因为http协议数据无状态协议，一旦数据传输完毕，连接就回断开，不会保存上次回话的信息。因此引入cookie技术可以理解为针对http协议的扩展，一定程度上解决了无状态带来的影响。

### session

当客户端请求创建一个session的时候，服务器会先检查这个客户端的请求里是否已包含了一个session标识 - sessionId，

- 如果已包含这个sessionId，则说明以前已经为此客户端创建过session，服务器就按照sessionId把这个session检索出来使用（如果检索不到，可能会新建一个）
- 如果客户端请求不包含sessionId，则为此客户端创建一个session并且生成一个与此session相关联的sessionId

sessionId的值一般是一个既不会重复，又不容易被仿造的字符串，这个sessionId将被在本次响应中返回给客户端保存。保存sessionId的方式大多情况下用的是cookie。

**服务器会创建sessionid返回给客户端，再次请求是，sessionid会存放到Header中，服务器根据sessionid寻找内存中是否存在。**

