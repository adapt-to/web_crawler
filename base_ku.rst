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

request模块具体用法
-------------------

urlopen()
+++++++++++++++++

1. urlopen()方法：传入url，获取httpresponse对象。用法如下：
    
    >>> from urllib import request # 导入request模块
    >>> response = request.urlopen('https://www.halihali.tv/')  # 使用urlopen方法
    >>> print(response.read().decode('utf-8'))                  # 注意不要丢掉decode

    这时候就会打印该url的html源代码（这里太多，不展示）。能够得到网页的源代码，从而就可以获取到网站的各种信息。

    >>> from urllib import request
    >>> response = request.urlopen('https://www.halihali.tv/')
    >>> print(type(response))
    <class 'http.client.HTTPResponse'>>>>

    发现返回的是 ``HTTPResponse`` 对象类型，它内部包含了很多属性和方法，可以说得到这个对象后就能够调用对象中的这些方法和属性，
    如上述代码就是调用 ``read()`` 方法返回网页的内容。此外还有很多其他的属性，方法如：
    
    >>> print(response.status) # 返回响应状态码，200表示成功
    200
    >>> print(response.getheaders()) # 返回响应头
    [('Server', 'nginx'), ('Date', 'Sat, 10 Nov 2018 12:29:32 GMT'), ('Content-Type', 'text/html; charset=utf-8'), \
    ('Transfer-Encoding', 'chunked'), ('Connection', 'close'), ('Vary', 'Accept-Encoding'), ('X-Powered-By', 'PHP/7.0.32')]
    >>> print(response.getheader('Server')) # 返回响应头中的Server的值
    nginx
    >>>

    .. note::
    所以利用 ``request`` 模块的 ``urlopen()`` 方法可以完成最基本的网页 **GET请求**。
    利用上述的一些属性和方法我们能够的到响应中的几乎所有信息。

2. 当然urlopen()方法还有更多的用途，下面看urlopen()方法的完整API：

    ``urllib.request.urlopen(url, data=None, [timeout,]*, cafile=None, capath=None, cadefault=False, context=None)``

    该API的参数含义如下：

    * url参数： 发送请求的网址
    * data参数： 附加数据，使用该参数时必须使用 ``bytes()`` 方法将参数转化为 **字节流** 编码格式的内容，即bytes类型。
      还有很重要的一点是，传递该参数后，该请求方式就不再是GET方式，而是POST方式。




