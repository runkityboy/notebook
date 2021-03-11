#### 用生活中的例子举例
- 迎宾：接受请求连接
- 点菜：解析请求内容
- 做菜：业务处理
- 上菜：处理业务处理数据
- 送客：返回数据

其中伙计为线程，饭店为服务器

单线程模式：只有一个伙计处理所有的事情  
多线程模式：多个伙计一起处理  
主从多线程模式：一个或者多个人专门做迎宾

#### 各个socket关心的事件
| client/server | SocketChannel/ServerSocketChannel | OP_ACCEPT | OP_CONNECT | OP_READ | OP_WRITE |
| --- | --- | --- | --- | --- | --- |
| client | SocketChannel | | Y | Y | Y |
| server | SocketChannel | | | Y | Y |
| server | ServerSocketChannel | Y | | | |

#### IO多路复用技术比较
poll | epoll
--- | ---
最大文件句柄1024 | 没有限制，和内存大小有关
IO效率随着FD的增加线性下降 | 只处理活跃的(由于网络的延迟性或者链路空闲，任一时刻活跃的不会很多)
 无 | mmap加速内核和用户空间的消息传递

#### netty为同步非阻塞的IO
同步与异步的区别：数据拷贝阶段是否需要完全由操作系统处理  
阻塞与非阻塞的区别：针对发起IO操作后，是否立刻返回一个标志信息而不让请求线程等待

