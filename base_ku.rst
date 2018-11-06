=================
2. 基本库的使用
=================

Python提供了很多强大的类库来帮助我们完成向浏览器发送请求。
例如：urllib、httplib2、requests、treq等。

urllib库的使用
================

urllib是python3内置的HTTP请求库，有了它能够很轻松的给服务器发送请求并处理响应。

在python3中urllib包含如下几个模块：
 1. request ：最基本的HTTP请求模块，可以用来模拟发送请求
 2. error ：异常处理模块，如果出现请求错误，可以捕获这些异常
 3. parse ：工具模块，提供了许多URL处理方法，比如拆分、解析、合并等
 4. robotparser ：识别网站的robots.txt文件，判断哪些网站可以爬，哪些不能爬

request模块
-----------------
