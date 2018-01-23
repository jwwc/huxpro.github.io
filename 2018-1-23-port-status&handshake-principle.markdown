---
layout:     post
title:      "端口的状态和握手原则"
subtitle:   ""
date:       2018-1-23 08:00:00
author:     "jwwc
header-img: "img/post-bg-android.jpg"
tags:
    - 网络
---

1:LISTENNING:侦听状态，端口开放等待被连接
2SYN_SENT:请求连接状态，当要访问其他电脑的服务时首先要发个同步信号给该端口，此时状态为SYN_SENT（客户端状态）如果连接成功了就变为ESTABLISHED,此时SYN_SENT状态非常的短暂，但如果发现SYN_SENT非常的多且向不同的机器发出，电脑可能中病毒
3SYN_RCVD(服务器状态)：在收到和发送一个连接请求后，等待服务器端对请求连接确认，当服务器收到客户端发送的同步信号时，将ACK和SYN置1发送给客户端，此时服务器端处于SYN_RCVD，如果连接成功就变为ESTABLISHED,正常情况下SYN_RCVD状态非常短暂
4ESTABLISHED:两台电脑正在传输数据
5 FIN-WAIT-1
等待远程TCP连接中断请求，或者先前的连接中断请求的确认，客户端应用程序调用close,TCP发出FIN请求主动关闭连接，之后进去FIN_WAIT状态
6FIN-WAIT-2
从远程TCP 等待连接中断请求，客户端接到ACK后，进入了FIN_WAIT-2,这是在关闭连接时，客户端和服务器两次握手原则之后的状态，就是半关闭状态，在这个状态下，应用程序可以接收数据，但是不能发送数据
CLOSE-WAIT
服务器端主动关闭连接或者网络异常导致连接关闭，这是客户端状态会改变，这时客户端状态变为CLOSE_WAIT,此时客户端调用close函数，使连接正确关闭
TIME-WAIT
客户端调用close函数，给服务器发送FIN，请求关闭连接，服务器收到FIN后给client返回确认ACK，同时关闭通道，此时不能再从这个连接上读取数据，read（）返回为0，服务器端的TCP状态转化为CLOSE_WAIT状态
<div class="visible-md visible-lg">
    <img src="//jwwc.github.io/img/network.jpg.png" width="350" />
</div>
