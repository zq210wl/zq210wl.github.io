title: 理解HTTP Header
date: 2014-12-30 15:48:06
categories: html
---
* HTTP协议是怎样传输的？
  * HTTP采用请求/响应模型，浏览器端发送请求，服务器给与响应。就整个网络资源传输而言，包括message-header和message-body两部分。
  * http 请求的整个过程
    ![](/imgs/http_request_process.gif)
* http header
  * http header内容的组织形式，大体分为Request和Response两部分。
* Request
  * 当你在流览器位址栏里键入一个url，你的流览器会将类似如下的http请求
        GET /tutorials/other/top-20-mysql-best-practices/ HTTP/1.1 (Request line)
        Host: net.tutsplus.com
        User-Agent: Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.5) Gecko/20091102 Firefox/3.5.5 (.NET CLR 3.5.30729)
        Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
        Accept-Language: en-us,en;q=0.5
        Accept-Encoding: gzip,deflate
        Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
        Keep-Alive: 300
        Connection: keep-alive
        Cookie: PHPSESSID=r2t5uvjq435r4q7ib3vtdjq120
        Pragma: no-cache
        Cache-Control: no-cache
    * 第一行被称为“Request Line” 它描述的是这个请求的基本资讯，剩下的就是HTTP headers了。
* Response
  * 请求完成之后，你的流览器可能会收到如下的HTTP回应：
        HTTP/1.x 200 OK (state line)
        Transfer-Encoding: chunked
        Date: Sat, 28 Nov 2009 04:36:25 GMT
        Server: LiteSpeed
        Connection: close
        X-Powered-By: W3 Total Cache/0.8
        Pragma: public
        Expires: Sat, 28 Nov 2009 05:36:25 GMT
        Etag: "pub1259380237;gz"
        Cache-Control: max-age=3600, public
        Content-Type: text/html; charset=UTF-8
        Last-Modified: Sat, 28 Nov 2009 03:50:37 GMT
        X-Pingback: http://net.tutsplus.com/xmlrpc.php
        Content-Encoding: gzip
        Vary: Accept-Encoding, Cookie, User-Agent
        <!-- ... rest of the html ... -->
    * 第一行被称为“Status Line”，它之后就是http headers，空行完了就开始输出内容了（在这个案例中是一些html输出）。
* HTTP Request结构
  ![](/imgs/http_request_composition.gif)
  * 被称作“first line”的第一行包含三个部分：
    * "method" 表明这是何种类型的请求. 最常见的请求类型有GET,POST和HEAD.
    * "path" 体现的是主机之后的路径. 例如，当你请求“http://net.tutsplus.com/tutorials/other”时, path 就会是"/tutorials/other".
    * "protocol" 包含有“HTTP” 和版本号.
  * 剩下的部分每行都是一个"Name:Value"对(即: MIME信息)。它们包含了各式各样关于请求和你流览器的资讯。
    * 详细信息请参考：
      * http://en.wikipedia.org/wiki/List_of_HTTP_header_fields
    * 这些headers大部分都是可选的。HTTP 请求甚至可以被精简成这样子：
          GET /tutorials/other/top-20-mysql-best-practices/ HTTP/1.1
          Host: net.tutsplus.com
* HTTP Response结构
  ![](/imgs/http_response_composition.gif)
  * 第一个有价值的资讯就是协定。目前伺服器都会使用HTTP/1.x 或者HTTP/1.1。
  * 接下来一个简短的资讯代表状态。代码200意味着我们的请求已经发送成功了，伺服器将会返回给我们所请求的文档，在Header资讯之后。
    * HTTP 状态码
      * 200 用来表示请求成功.
      * 300 来表示重定向.
      * 400 用来表示请求出现问题.
      * 500 用来表示伺服器出现问题.
  * 同样，这些Header资讯也是可选的。