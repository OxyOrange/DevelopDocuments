# SOCKET

    socket(套接字)是网络通信的基石，是支持TCP/UDP协议的网络通信的基本单元，包含进行网络通信必须的五种：
    1、连接使用的协议
    2、本地主机的IP地址
    3、本地进程的协议端口
    4、远程主机的IP地址
    5、远程进程的协议端口
    多个TCP连接或多个应用程序进程可能需要通过同一个TCP协议端口传输数据.为了区别不同应用程序进程和连接，计算机操作系统为应用程序与TCP/IP协议交互提供了套接字(Socket)接口。应用层可以和传输层通过Socket接口，区分来自不同应用程序进程或网络连接的通信，实现数据传输的并发服务。

    建立Socket连接至少需要一对套接字，其中一个运行于客户端，称为ClientSocket，另一个运行于服务器端，称为ServerSocket。套接字之间的连接过程分为三个步骤：服务器监听，客户端请求，连接确认。

    Socket可以支持不同的传输层协议（TCP或UDP），当使用TCP协议进行连接时，该Socket连接就是一个TCP连接,UDP连接同理。

    ![](http://cc.cocimg.com/api/uploads/20160601/1464766627371148.jpg)

#### IOS中socket使用的库函数
    在iOS中，OC提供了一套较为简单封装的socket， CFNetwork 和 CFNetServices，其中 CFNetwork 又是基于 CFStream 和 CFSocket。

    1、创建套接字
        Socket(af,type,protocol)//建立地址和套接字的联系
        bind(sockid, local addr, addrlen)//服务器端侦听客户端的请求
        listen( Sockid ,quenlen)//建立服务器/客户端的连接 (面向连接TCP）
    2、客户端请求
        Connect(sockid, destaddr, addrlen)//服务器端等待从编号为Sockid的Socket上接收客户连接请求
        newsockid=accept(Sockid，Clientaddr, paddrlen)//发送/接收数据
    3、面向连接
        send(sockid, buff, bufflen)
        recv()
    4、面向无连接
        sendto(sockid,buff,…,addrlen)
        recvfrom()
    5、释放套接字
        close(socked)
    
    在iOS中以NSStream(流)来发送和接收数据,可以设置流的代理，对流状态的变化做出相应的动作(连接建立，接收到数据，连接关闭）。

    * NSStream：数据流的父类，用于定义抽象特性，例如：打开、关闭代理，NSStream继承自CFStream(CoreFoundation)
    * NSInputStream：NSStream的子类，用于读取输入
    * NSOutputStream：NSSTream的子类，用于写输出。

    客服端使用socket如下：
     ![](https://github.com/zhanghouqi/DevelopDocuments/blob/master/Images/E2536132-C888-4C81-958F-B40A085996FF.png)

    在实际开发中，直接使用基于C的socket显得非常的不方便，有比较简单的方法，比如使用github的开源类库：CocoaAsyncSocket；
    CocoaAsyncSocketshi 是支持TCP和UMP的
    其使用：
    ![](https://github.com/zhanghouqi/DevelopDocuments/blob/master/Images/D473F3CE-5AE1-4B46-9FB2-35E875AC3E1C.png)
