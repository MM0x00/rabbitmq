# rabbitmq 在线实验环境

## 软件简介

软件基本信息，License，所属的类别，作用，特点等。

RabbitMQ是实现高级消息队列协议（AMQP）的开源消息代理软件（有时称为面向消息的中间件）。RabbitMQ服务器以Erlang编程语言编写，并且基于开放电信平台框架，用于集群和故障转移。与代理接口的客户端库可用于所有主要的编程语言。

所属类别是：服务器软件

特点：

MQ是消费-生产者模型的一个典型的代表，一端往消息队列中不断写入消息，而另一端则可以读取或者订阅队列中的消息。MQ和JMS类似，但不同的是JMS是SUN JAVA消息中间件服务的一个标准和API定义，而MQ则是遵循了AMQP协议的具体实现和产品。

## 软件官网

https://en.wikipedia.org/wiki/RabbitMQ

## Dockerfile 使用方法


运行守护进程
要注意的一个关于RabbitMQ的重要事情之一是它根据所谓的“节点名称”存储数据，该节点名称默认为主机名。这对Docker的使用意味着我们应该为每个守护进程指定-h/ --hostname显式，这样我们就不会得到一个随机的主机名并且可以跟踪我们的数据：
```
$ docker run -d --hostname my-rabbit --name some-rabbit rabbitmq:3
```
如果你给了一分钟，那么docker logs some-rabbit你会在输出中看到一个类似于：
```
=INFO REPORT==== 6-Jul-2015::20:47:02 ===
node           : rabbit@my-rabbit
home dir       : /var/lib/rabbitmq
config file(s) : /etc/rabbitmq/rabbitmq.config
cookie hash    : UoNOcDhfxW9uoZ92wh6BjA==
log            : tty
sasl log       : tty
database dir   : /var/lib/rabbitmq/mnesia/rabbit@my-rabbit
```
注意database dir那里，特别是它的“节点名称”附加到文件存储的末尾。/var/lib/rabbitmq默认情况下，此映像使所有卷成为全部。

## 资源链接

- https://en.wikipedia.org/wiki/RabbitMQ
- https://hub.docker.com/_/rabbitmq/
