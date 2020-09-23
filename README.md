* [算法](#算法)
     * [数据结构](#数据结构)
* [网络](#网络)
     * [体系结构](#体系结构)
     * [HTTPS](#https)
* [Java](#java)
     * [面向对象思想](#面向对象思想)
     * [Java基础](#java基础)
     * [Java容器](#java容器)
     * [Java并发多线程](#java并发多线程)
     * [JVM](#jvm)
* [数据库/搜索引擎](#数据库搜索引擎)
     * [Mysql](#mysql)
     * [Redis](#redis)
     * [Elasticsearch](#elasticsearch)
* [操作系统](#操作系统)
     * [Linux](#linux)
  * [工具](#工具)
     * [Git](#git)
     * [Docker](#docker)
        * [容器](#容器)
        * [镜像](#镜像)
     * [Maven](#maven)
* [框架](#框架)
     * [Spring](#spring)
        * [BeanFactory与ApplicationContext区别 ](#beanfactory与applicationcontext区别)
           * [BeanFactory](#beanfactory)
           * [ApplicationContext](#applicationcontext)
        * [生命周期](#生命周期)
           * [创建](#创建)
           * [销毁](#销毁)
        * [Spring事务](#spring事务)
           * [隔离级别](#隔离级别)
           * [传播范围](#传播范围)
              * [支持当前事务的情况：](#支持当前事务的情况)
              * [不支持当前事务的情况：](#不支持当前事务的情况)
              * [其他情况：](#其他情况)
           * [回滚规则](#回滚规则)
           * [超时时间](#超时时间)
           * [只读](#只读)
     * [Spring Cloud](#spring-cloud)
     * [MyBatis](#mybatis)
     * [RPC](#rpc)
        * [流程](#流程)
        * [协议](#协议)
* [消息中间件](#消息中间件)
     * [Kafka](#kafka)
* [系统设计](#系统设计)
     * [JWT](#jwt)
     * [缓存](#缓存)
     * [日志收集](#日志收集)
     * [订单](#订单)
        * [最终一致](#最终一致)
        * [幂等性](#幂等性)
     * [DDD领域驱动模型](#ddd领域驱动模型)
     * [Saas多租户架构](#saas多租户架构)

## 算法
- LRU
- 排序算法
	- 冒泡排序
	- 选择排序
	- 插入排序
	- 希尔排序
	- 快速排序
	- 归并排序
	- 堆排序
- 布隆过滤
	1. 初始一个bitmap数组
	2. 计算hash值 数组对应位置值设为1
- 负载均衡算法
- 分治法

- 动态规划
	- 重叠子问题
	- 最优子结构
	- 状态转移方程 
		- 明确「状态」 -> 定义 dp 数组/函数的含义 -> 明确「选择」-> 明确 base case。

- 贪心算法
- 树遍历
    - 前序
    xxx
    left
    right
    - 中序
    left
    xxx
    right
    - 后序 
    left
    right
    xxx

### 数据结构
- 完全二叉树
	- 树高度差不能大于1，并且1到k-1层节点必须是满的
	- 最底层不一定是满的 ，但是节点要在最左
- 二叉查找树
	- 左节点小于根节点，右节点大于根节点
- 平衡二叉树
	- 二叉查找树极端情况会成为链表，平衡二叉树会在构建的时候做反转  避免高度差大于1
- B树
	- 平衡多路查找树
	- M 阶 B 树表示该树每个节点最多有 M 个子树
	- 每个节点有M-1个数据
- B+树
	- 每个节点数据是子树的数据最大值
	- 叶子节点是一个链表，包含了所有的数据 
- 红黑树
    - 节点是红色或黑色。
    - 根是黑色。
    - 所有叶子都是黑色（叶子是NIL节点）。
    - 每个红色节点必须有两个黑色的子节点。（从每个叶子到根的所有路径上不能有两个连续的红色节点。）
    - 从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点。

- 跳表
   链表加多级索引的结构
## 网络
### 体系结构


- OSI七层协议
- TCP四层协议
- 五层协议
OSI七层与TCP四层的综合，方便学习，实际应用的还是TCP/IP四层协议
应用层  HTTP,FTP,SMTP等
运输层  报文
网络层  包
数据链路层  帧
物理层     比特
### HTTPS
HTTP+TLS

## Java
### 面向对象思想
- 设计模式
     - 单例模式（双重检查锁）
     - 策略模式
     - 观察者模式
     - 装饰器模式
     - 状态模式
      
### Java基础
- 重载和重写
- 接口和抽象类
    - 接口中方法都是pubilc，都是抽象方法（1.8之后又default方法） 
- 继承  封装   多态
- 成员变量与局部变量
    - 成员变量属于类，局部变量属于方法
    - 没有设初始值，成员变量会自动设初始值，局部变量
### Java容器
- ArraryList
    - 扩容 
        - 确保容量(插入的index不能大于size) 
        - 1.原先的1.5倍
        - 2 Arrays.copy(）把原数组整个复制到新数组中
- 线程安全List -> CopyOnWriteArrayList
- LinkedList
- HashMap
- ConcurrentHashMap
    - 1.8 之前分段锁
    - 1.8 数组+链表  读（CAS） 写（Sychronized）
### Java并发多线程
-  线程实现方式
    - 实现Runable接口
    - 实现Callable接口
    - 继承Thread类
    - 线程池创建
- 线程状态
    - 新建  NEW
    - 可运行  RUNABLE
    - 阻塞  BLOCKED
    - 无限期等待  WAITING
    - 限期等待  TIMED_WAITING
    - 死亡   TERMINATED
- 线程池
    - 状态
        - RUNNIGN
        - SHUTDOWN
        - STOP
        - TIDYING
        - TERMINATED
    - 核心参数
        - 阻塞队列 
        - 拒绝策略
        - 核心线程数
        - 最大线程数
        - 最大等待时间
    - execute()执行流程
        - 首先检查线程池状态是否为RUNNING
        - workCount < CorePoolSize 新起线程执行
        - workCount >= CorePookSize & 阻塞队列没满  放入阻塞队列
        - workCount >= CorePollSize & workCount < MaxnumPoolSize & 阻塞队列满了 起新线程执行
        - workCount >= MaxnumPoolSize& 阻塞队列满了 拒绝
    - Worker
    - 运用
        - 多线程调用远程接口，节省时间
        - 处理大的操作
- CAS (ABA问题)
- AQS
- ReentrantLock 重入锁
- Synchronized
- volatile 保证可见性
 ### JVM
 - JMM
   -   程序计数器
   - 本地方法栈
   - 栈
   - 堆
   - 方法区
 - 垃圾回收
    - 对象是否可回收
        - 引用计数法
        - 可达性分析法
    - 垃圾回收算法
        - 复制算法
        - 标记清除法
        - 标记整理法
        - 分代收集法
    - [OOM的几种类型](https://tianmingxing.com/2019/11/17/%E4%BB%8B%E7%BB%8DJVM%E4%B8%ADOOM%E7%9A%848%E7%A7%8D%E7%B1%BB%E5%9E%8B/)
        -  Java heap space
        -  GC overhead limit exceeded
        - Permgen space
        -  Metaspace
        - Unable to create new native thread
        - Out of swap space
        - Requested array size exceeds VM limit
        - Kill process or sacrifice child
 
## 数据库/搜索引擎
### Mysql
- 索引  B+树  B+树和B树的区别
	- 联合索引
- 优化
- 锁   
	- 表锁
	- 行锁
	- 间隙锁
	- 共享锁
	- 排它锁
	- ...
- 事务
    - MVCC 
    - 事务隔离级别 
###  Redis
- 数据类型
	- list
	利用数组实现类似Java的arraylist 
	- string
	- set
	- hash
	类似于Java的HashMap
	- zset 
	跳表
- 淘汰机制
https://github.com/doocs/advanced-java/blob/master/docs/high-concurrency/redis-expiration-policies-and-lru.md
- 布隆过滤
-  过期策略
	随机删除设置过期时间的数据
	随机删除数据
	lru删除设置过期过期时间的数据
	lru删除数据
	设置过期时间
- redis与mysql缓存一致问题
原因：写库删除缓存的时，先删缓存的话，还没来得及写库其他线程就进行读取设置缓存，造成了脏数据
解决方案：
1.延时双删
2.订阅mysql binlog异步更新缓存
- redis集群
哈希槽概念（16384个），通过哈希计算确定数据放在哪个槽中，每个redis节点管理每部分哈希槽的数据
###  Elasticsearch
- 基本概念
    - ES分布式概念 
    - 搜索原理
    - 新增数据原理  
	- 脑裂   
- 倒排索引
- 分页的from，size问题
- 排序 （sort指定）

## 操作系统
###  Linux
- 常用命令
	- ps
	- top
	- jps
	- jstack 

## 工具
###  Git
- 常用命令

###  Docker
#### 容器
#### 镜像


### Maven
- 生命周期

## 框架
###  Spring
#### BeanFactory与ApplicationContext区别 
ApplicationContext实现了BeanFactory
##### BeanFactory
这是一个用来访问 Spring 容器的 root 接口，要访问 Spring 容器，我们将使用 Spring 依赖注入功能，使用 BeanFactory 接口和它的子接口
##### ApplicationContext

ApplicationContext 是 Spring 应用程序中的中央接口，用于向应用程序提供配置信息它继承了 BeanFactory 接口，所以 ApplicationContext 包含 BeanFactory 的所有功能以及更多功能！它的主要功能是支持大型的业务应用的创建
#### 生命周期
- 首先调用构造方法
- 通过Setter方法完成依赖注入
- BeanNameAware.setBeanName() 会被调用，它设置该 bean 在 Bean Factory 中的名称
- 接下来调用 BeanClassLoaderAware.setBeanClassLoader()，为 bean 实例提供类加载器
- 然后BeanFactoryAware.setBeanFactory() 会被调用，为 bean 实例提供其所拥有的 factory

##### 创建
BeanPostProcessor（postProcessBeforeInitialization，postProcessAfterInitialization）

顺序：
- postProcessBeforeInitialization
PAI
- @PostConstruct
- InitializingBean.afterPropertiesSet()
- init-method
- postProcessAfterInitialization
##### 销毁
PDD
@PreDestroy
DisposableBean.destroy()
destroy-method 
- IOC 控制反转
- AOP  动态代理
- Spring Boot自动配置

#### Spring事务
##### 隔离级别
- TransactionDefinition.ISOLATION_DEFAULT:	使用后端数据库默认的隔离级别，Mysql 默认采用的 REPEATABLE_READ隔离级别 Oracle 默认采用的 READ_COMMITTED隔离级别.
- TransactionDefinition.ISOLATION_READ_UNCOMMITTED: 最低的隔离级别，允许读取尚未提交的数据变更，可能会导致脏读、幻读或不可重复读
- TransactionDefinition.ISOLATION_READ_COMMITTED: 	允许读取并发事务已经提交的数据，可以阻止脏读，但是幻读或不可重复读仍有可能发生
- TransactionDefinition.ISOLATION_REPEATABLE_READ: 	对同一字段的多次读取结果都是一致的，除非数据是被本身事务自己所修改，可以阻止脏读和不可重复读，但幻读仍有可能发生。
- TransactionDefinition.ISOLATION_SERIALIZABLE: 	最高的隔离级别，完全服从ACID的隔离级别。所有的事务依次逐个执行，这样事务之间就完全不可能产生干扰，也就是说，该级别可以防止脏读、不可重复读以及幻读。但是这将严重影响程序的性能。通常情况下也不会用到该级别。
##### 传播范围
###### 支持当前事务的情况：

- TransactionDefinition.PROPAGATION_REQUIRED： 如果当前存在事务，则加入该事务；如果当前没有事务，则创建一个新的事务。
- TransactionDefinition.PROPAGATION_SUPPORTS： 如果当前存在事务，则加入该事务；如果当前没有事务，则以非事务的方式继续运行。
- TransactionDefinition.PROPAGATION_MANDATORY： 如果当前存在事务，则加入该事务；如果当前没有事务，则抛出异常。（mandatory：强制性）

###### 不支持当前事务的情况：

- TransactionDefinition.PROPAGATION_REQUIRES_NEW： 创建一个新的事务，如果当前存在事务，则把当前事务挂起。
- TransactionDefinition.PROPAGATION_NOT_SUPPORTED： 以非事务方式运行，如果当前存在事务，则把当前事务挂起。
- TransactionDefinition.PROPAGATION_NEVER： 以非事务方式运行，如果当前存在事务，则抛出异常。

###### 其他情况：

- TransactionDefinition.PROPAGATION_NESTED： 如果当前存在事务，则创建一个事务作为当前事务的嵌套事务来运行；如果当前没有事务，则该取值等价于
- TransactionDefinition.PROPAGATION_REQUIRED。


##### 回滚规则
默认运行时异常才会回滚
##### 超时时间
可设置事务超时时间，超时自动回滚
##### 只读
只读事务可设置为true提高效率

###  Spring Cloud
- Feign
	- http调用 
- Spring Cloud Gateway
	- 负载均衡
	- 限流 
- Eureka
- Hystrix
### MyBatis
- 一级缓存，二级缓存
	- 一级缓存一次会话的SqlSession中 默认开启
	- 二级缓存 每个Mapper  多个SqlSession共享  手动开启

### RPC 
#### 流程
- 建立连接 TCP
- 序列化
- 反序列化

#### 协议



## 消息中间件
###  Kafka
- 入门
- ...

## 系统设计

### JWT
jwt是客户端与服务端加密传输
分为三个部分
头
携带信息  自定义信息
签名

### 缓存
- 缓存那些事[https://tech.meituan.com/2017/03/17/cache-about.html](https://tech.meituan.com/2017/03/17/cache-about.html)
### 日志收集
- kafka收集用户行为日志
https://www.cnblogs.com/163yun/p/9578250.html
### 订单
#### 最终一致

#### 幂等性

### DDD领域驱动模型

### Saas多租户架构
