先来看http与https的图：

![image-20200612162746469](/Users/liguopei/Library/Application Support/typora-user-images/image-20200612162746469.png)

可见，https是在http原有的基础上在http与tcp层之间增加了一成TLS的认证。补充了http的安全特性。其中，浏览器和服务器在使用TLS建立连接时需要选择一组恰当的加密算法来实现安全通信，这些算法的组合被称为”密码套件“（cipher suite，也叫加密套件）。TLS的密码套件命名非常规范，格式很固定。基本的形式是”密钥交换算法+签名算法+对称加密算法+摘要算法“。例如“ECDHE-RSA-AES256-GCM-SHA384”的意思是“握手时使用 ECDHE 算法进行密钥交换，用 RSA 签名和身份认证，握手后的通信使用 AES 对称算法，密钥长度 256 位，分组模式是 GCM，摘要算法 SHA384 用于消息认证和产生随机数。”

双向认证 SSL 协议的具体通讯过程，服务器和用户双方必须都有证书。由此可见，SSL协议是通过非对称密钥机制保证双方身份认证，并完成建立连接，在实际数据通信时通过对称密钥机制保障数据安全性

<img src="/Users/liguopei/Library/Application Support/typora-user-images/image-20200612190015559.png" alt="image-20200612190015559" style="zoom:50%;" />

非对称加密有两种方式，一种是加密，另外一种是签名。

加密：公钥加密，私钥解密。如ssh账号登陆：

<img src="/Users/liguopei/Library/Application Support/typora-user-images/image-20200612191120406.png" alt="image-20200612191120406" style="zoom:50%;" />

签名：私钥加密（签名），公钥验签（如ssh密钥登陆）

<img src="/Users/liguopei/Library/Application Support/typora-user-images/image-20200612191032277.png" alt="image-20200612191032277" style="zoom:50%;" />



