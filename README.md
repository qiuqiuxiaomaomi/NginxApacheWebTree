# NginxApacheWebTree
Nginx, Apache等WEB服务器选型比对


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
