分享第一期：

# spring boot + dubbo框架


## 目的
   方便大家学习Spring boot+dubbo的入门指引。

## 简介
### 1.   什么是Spring boot
####  <1>. 前置背景

​    Spring的组件代码是轻量级的，但它的配置却是重量级的。一开始， Spring用XML配置，而且是很多XML配置。 Spring 2.5引入了基于注解的组件扫描，这消除了大量针对应用程序自身组件的显式XML配置。 Spring 3.0引入了基于Java的配置，这是一种类型安全的可重构配置方式，可以代替XML。尽管如此，我们依旧没能逃脱配置的魔爪。开启某些Spring特性时，比如事务管理和SpringMVC，还是需要用XML或Java进行显式配置。启用第三方库时也需要显式配置，比如基于Thymeleaf的Web视图。配置Servlet和过滤器（比如Spring的DispatcherServlet）同样需要在web.xml或Servlet初始化代码里进行显式配置。组件扫描减少了配置量， Java配置让它看上去简洁不少，但Spring还是需要不少配置。

**平时如果我们需要搭建一个spring web项目的时候需要怎么做呢？**

1）配置web.xml，加载spring和spring mvc

2）配置数据库连接、配置spring事务

3）配置加载配置文件的读取，开启注解

4）配置日志文件

...

配置完成之后部署tomcat 调试

...

现在非常流行微服务，如果我每拓展一个项目功能，我都需要重新这样折腾一遍!

但是如果使用spring boot呢？

很简单，我仅仅只需要非常少的几个配置就可以迅速方便的搭建起来一套web项目或者是构建一个微服务！



####  <2>. Spring boot精要

#####    四个核心 ：

- 自动配置：针对很多Spring应用程序常见的应用功能， Spring Boot能自动提供相关配置 
- 起步依赖：告诉Spring Boot需要什么功能，它就能引入需要的库 
- 命令行界面：这是Spring Boot的可选特性，借此你只需写代码就能完成完整的应用程序，
  无需传统项目构建 
- Actuator：让你能够深入运行中的Spring Boot应用程序，有兴趣可以深入一探究竟

##### Spring-boot-starter（Spring boot其中一个模块组件）

starter启动器是一组方便的依赖关系描述符，可以将其包含在应用程序中，可以获得所需的所有Spring和相关技术的一站式服务，而无需搜索示例代码并复制粘贴的依赖描述符。例如，如果想开始使用Spring和JPA进行数据库访问，只需在项目中包含spring-boot-starter-data-jpa依赖项就可以开始使用了。

##### [Spring boot 安装（网上有很多，书中也有教程）](https://blog.csdn.net/lxh18682851338/article/details/78559146)

##### 总结：

Spring Boot为Spring应用程序的开发提供了一种新方式，框架本身带来的阻力很小。自动配置消除了传统Spring应用程序里的很多样板配置； Spring Boot起步依赖让你能通过库所提供的功能而非名称与版本号来指定构建依赖； Spring Boot CLI将Spring Boot的无阻碍开发模型提升到了一个崭新的高度。（本段摘自书《Spring boot 实战》） --用我的话来理解，就是spring boot其实不是什么新的框架，它默认配置了很多框架的使用方式，就像maven整合了所有的jar包，spring boot整合了所有的框架（不知道这样比喻是否合适）



### 2.什么是Dubbo

### <1>.背景

**早期单体架构：**

- 复杂性逐渐变高
- 技术债务逐渐上升
- 部署速度逐渐变慢
- 阻碍技术创新
- 无法按需伸缩	

**微服务、分布式：**

- 易于开发和维护
- 启动较快
- 局部修改容易部署
- 技术栈不受限
- 按需伸缩

**为什么是Dubbo？**

互联网的发展，网站应用的规模不断扩大，常规的垂直应用架构已无法应对，分布式服务架构以及流动计算架构势在必行，Dubbo是一个分布式服务框架，在这种情况下诞生的。现在核心业务抽取出来，作为独立的服务，使前端应用能更快速和稳定的响应。

Dubbo是Alibaba开源的分布式服务框架，它最大的特点是按照分层的方式来架构，使用这种方式可以使各个层之间解耦合（或者最大限度地松耦合）。从服务模型的角度来看，Dubbo采用的是一种非常简单的模型，要么是提供方提供服务，要么是消费方消费服务，所以基于这一点可以抽象出服务提供方（Provider）和服务消费方（Consumer）两个角色。关于注册中心（Zookeeper）、协议支持、服务监控等内容。

[Dubbo的安装及技术文档和原理实现（官方）](http://dubbo.apache.org/zh-cn/docs/user/quick-start.html)



**Dubbo核心：**

- 远程通讯：提供对多种基于长连接的NIO框架抽象封装，包括多种线程模型，序列化，以及“请求-响应”模式的信息交换方式
- 集群容错：提供基于接口方法的透明远程过程调用，包括多协议支持，以及软负载均衡，失败容错，地址路由，动态配置等集群支持
- 自动发现：基于注册中心目录服务，使服务消费方能动态的查找服务提供方，使地址透明，使服务提供方可以平滑增加或减少机器



### 3.我们项目中的结合spring boot使用情况：

看了pom.xml文件，是[dubbo-spring-boot-starter](https://github.com/apache/incubator-dubbo-spring-boot-project) 源码可见链接。

### 4.深入学习：

​	等待各位补充，敬请期待