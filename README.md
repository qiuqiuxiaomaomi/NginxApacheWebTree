# NginxApacheWebTree
Nginx, Apache等WEB服务器选型比对


###Apache请求模型

![](https://i.imgur.com/FqBlX4A.png)

![](https://i.imgur.com/kbsgswp.png)


###Nginx请求模型

![](https://i.imgur.com/wem5gHy.png)


<pre>
Apache与Nginx的优缺点对比：
      1：Nginx相对于Apache的优点：
           1）轻量级：同样是web服务，比Apache占用更少的内存及资源
           2）抗并发：Nginx处理请求时异步非阻塞的，而apache则是阻塞的，在高并发下nginx
                     保持低资源消耗高性能。
           3）高度模块化的设计，编写模块相对简单。
           5）社区活跃，各种高性能模块快速推出

      2：apache相对于Nginx的优点
           1）rewrite,比Nginx强大
           2）模块超多，基本能想到的都有
           3）少bug，Nginx相对较多，超稳定。

      
      一般来说，需要性能的WEB服务，用Nginx，如果不需要性能只求稳定，那就用Apache。后者的
      各种功能模块实现的比前者要好。epoll网络I/O模型是Nginx处理性能高的根本理由，但是并不
      是所有的情况下epoll大获全胜的，如果本身提供静态服务的就只有寥寥几个文件，apache的
      select模型或许比epoll更高性能。
</pre>

<pre>
      作为WEB服务器，相比Apache，Nginx使用更少的资源，支持更多的并发连接，体现更高的效率
   ，这点使得Nginx尤其受到虚拟主机提供商的欢饮，在高并发的情况下，Nginx是Apache服务器不错
   的替代品，Nginx在美国是做虚拟主机生意的老板们经常选择的软件平台之一，能够支持高达50000
   个并发连接的相应。

      Nginx作为负载均衡服务器:Nginx既可以在内部直接支持Rails, PHP程序对外进行服务，也可
   以作为HTTP代理服务器对外进行服务，Nginx采用C进行编写，不论是系统资源开销还是CPU使用效率
   都比Perlbal要好很多。
</pre>

<pre>
Nginx配置简洁，Apache配置复杂
Nginx静态处理性能比Apache高3倍以上。
Apache对PHP支持比较简单，Nginx需要配合其他后端用
Apache的组件比Nginx多
</pre>

<pre>
最核心的区别是apache的同步多进程模型，一个连接对应一个进程，Nginx是异步的，多个连
接（万级别）可以对应一个进程。

Nginx处理静态文件好，耗费内存少

Nginx处理动态文件请求时鸡肋，一半动态请求要apache去做，Nginx只适合静态和反向
</pre>

<pre>
Nginx优于Apache的主要有两点：
      1）Nginx本身就是一个反向代理服务器
      2）Nginx支持7层负载均衡
</pre>

<pre>
13个适用的Apache rewrite重写

      1：去掉域名中的www标记
      2：去掉www标记，但是保存子域名
</pre>

![](https://i.imgur.com/IFkwBMz.png)

<pre>
建议方案：

      Apache 后台服务器（主要处理php及一些功能请求 如：中文url）

      Nginx  前端服务器（利用它占用系统资源少得优势来处理静态页面大量请求）

      Lighttpd 图片服务器(cpu占用率低，效能好，以及丰富的模块等特点。其静态文件的响应
               能力远高于Apache，可谓Web服务器的后期之秀。)

总体来说，随着nginx功能得完善将使他成为今后web server得主流。
</pre>

<pre>
总结（静态资源）
    Apache：
        优点：
            1)Apache的兼容性和稳定性都是非常强
            2)Apache 的模块比 Nginx/Lighttpd丰富
            3)Apache在处理动态请求比Nginx/Lighttpd更有优势
        缺点：
            属于重量级web服务器（重量级主要是在软件包的大小上比较大，软件的耦合
            度大）在速度、性能不及其他轻量级web服务器，并且消费内存较高。使用传统的
            select模型，比较稳定的Prefork模式为多进程模式，需要经常派生子进程。所以
            消耗的cpu等服务器资源比较大。


    Lighttpd：
        优点：
            1)虚机的配置处理方式比 apache 直观，比Apache轻量
            2)轻量级web服务器，cpu占用低，效能好，模块丰富，对fastcgi支持非常好。
            3)支持高并发，和Nginx差不多，比apache性能高很多。
        缺点：
            稳定性没有Apache和Nginx高，bug相对较多
 

    Nginx：
        优点：
            1)轻量级，比apache 占用更少的内存及资源
            2)抗并发，nginx 处理请求是异步非阻塞的，而apache 则是阻塞型的，在高并发
              下nginx 能保持低资源低消耗高性能
            3)高度模块化的设计，编写模块相对简单
            5)有Lighttpd的性能，且更稳定，没有其内存泄露问题；
            6)处理静态文件，索引文件以及自动索引，打开文件描述符缓冲。
        缺点：
            7)nginx处理动态请求是鸡肋，不如Apache；
</pre>