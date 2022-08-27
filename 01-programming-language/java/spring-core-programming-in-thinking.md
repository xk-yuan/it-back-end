# spring-core-programming-in-thinking

> 小马哥讲Spring核心编程思想 @ 小马哥

> spring-5.2.x

## 概述

> 深入剖析源码，掌握核心编程特性

> 通过讲解编程模型、设计思想以及技术规范，站在哲学的高度，分析和猜想 Spring 的实现可能，并结合具体源码实现，不断地进行思维和实战训练，最终达到掌握特性、理解原理，学会学习的终极目的。


## [课程目录](spring-core-programming-in-thinking-contents.md)

## 课程笔记

> 统计 : 共二十章, 245 讲;

### 第一章：Spring Framework总览 (12讲)

#### 1. 概述 & 课程综述

> 支持实现细节
>
> 1. Java 语言特性 : 反射、动态代理、枚举、泛型、注解、ARM、Lambda 语法
>
> 2. 设计思想和模式的实现 : OOP, IoC, DDD, TDD, GoF23
>
> 3. Java API 的封装与简化 : JDBC, 事物 Transaction , Servlet, JPA, JMX, Bean, Validation
>
> 4. JSR 规范的适配与实现
>
> 5. 第三方框架的整合 : MyBatis, Hibernate, Redis

> Spring 在战略上被过分高估, 在战术上却被低估; 战略是指设计思想和协议规范, 在这方面基本没有明显突破, 遵循业界标准执行; 战术上却又巨大优势, 包括API抽象的硬核实力, 模块化设计, 功能的稳定性、可扩展性和可测试性。

> 课程设计思路, 课程内容从 Spring 特性简介入手, 结合官方文档, 通过实战演练加深理解, 在讲解编程模型、设计思想和技术规范的前提下, 站在哲学的告诉思考分析和猜想Spring的实现可能, 并结合源码, 进行思维和实战的训练。达到掌握特性, 理解原理, 学会学习的目标。

> 本课程只专注于 spring framework 核心部分, 对 AOP, EL, 事务, Web 等特性未涉及。

#### 2. 课程内容, Spring 核心特性

> **一、框架的总览**
>
> 1. 特性总览
>
> 2. 版本特性
>
> 3. 模块化设计
>
> 4. 技术整合
>   - a. Java 语言特性运用
>   - b. JDK API 实践
>   - c. Java EE API 整合
>
> 5. 编程模型
>
>   - a. 面向对象编程 : 接口契约, 即面向接口编程
>
>   - b. 面向切面编程 : 动态代理(JDK, ASM, CGLib, AspectJ), 字节码提升
>
>   - c. 面向元编程
>     - 配置元信息
>     - 注解
>     - 属性配置 (placehodler, 外部化配置)
>
>   - d. 面向模块编程
>     - Maven Artifacts / gldle
>     - OSGi BUndles
>     - Java 9 Automatic Modules
>     - Spring @Enable* 注解
>
>   - e. 面向函数编程
>     - Lambda
>     - Reactive (异步非阻塞 WebFlux)
>
> **二、IoC容器**
>
> 1. 重新认识 Ioc
> 2. Spring IoC 容器
> 3. 依赖查找 (Dependency Lookup)
> 4. 依赖注入 (Dependency Injection)
> 5. 依赖来源 (Dependency Sources)
> 6. Spring IoC 容器生命周期
>
> **三、Bean**
>
> 1. Bean 实例
> 2. Bean 作用域   (Scopes)
> 3. Bean 生命周期 (Lifecycle)
>
> **四、元信息**
>
> 1. 注解
> 2. 配置元信息 (Configuration Metadata)
> 3. 外部化配置
>
> **五、基础设施**
>
> 1. 资源管理 (Resources)
> 2. 类型转换
> 3. 数据绑定
> 4. 校验
> 5. 国际化
> 6. 事件
> 7. 泛型处理

#### 3. Spring Framework 总览

> 1. 课程准备
>
> 2. 特性总览
>
> 3. 版本特性
>
> 4. 模块化设计
>
> 5. 对 Java 语言特性运用
>
> 6. 对 JDK API 实践
>
> 7. 对 Java EE API 整合
>
> 8. 编程模型
>
> 9. 核心价值

##### 1. 核心特性、数据存储、Web技术、框架整合与测试

1. 核心特性

> IoC 容器 (Ioc Container)
>
> Spring 事件 (Events)
>
> 资源管理 (Resources)
>
> 国际化 (i18n)
>
> 校验 (Validation)
>
> 数据绑定 (Data Binding)
>
> 类型转换 (Type Conversion)
>
> Spring 表达式 (Spring Express Language)
>
> 面向切面编程 (AOP)

2. 数据存储 (Data Access)

> JDBC
>
> 事务抽象 (Transactions) : 来源于, EJB 在其基础上做了简化工作
>
> DAO 支持 (Dao Support)
>
> O/R 映射 (O/R Mapping)
>
> XML 编列 (XML Marshalling)

3. Web 技术

> a. Web Servlet 技术栈
>
> Spring MVC
>
> WebSocket
>
> SockJS

> b. Web Reactive 技术栈 (Spring 5 引入) (默认 Netty WebServer 底层实现)
>
> Spring WebFlux
>
> WebClient
>
> WebSocket

4. 技术整合 (Integration)

> 远程调用 (Remoting)
>
> Java 消息服务 (JMS)
>
> Java 连接架构 (JCA)
>
> Java 管理扩展 (JMX)
>
> Java 邮件客户端 (Email)
>
> 本地任务 (Tasks)
>
> 本地调度 (Scheduling)
>
> 缓存抽象 (Caching)

5. Spring 测试

> 模拟对象 (Mock Objects)
>
> TestContext 框架
>
> Spring MVC 测试
>
> Web 测试客户端

##### 2. Spring 模块化设计

> 01. spring-aop
>
> 02. spring-aspects
>
> 03. spring-beans
>
> 04. spring-context
>
> 05. spring-context-indexer
>
> 06. spring-context-support
>
> 07. spring-core
>
> 08. spring-expression
>
> 09. spring-instrument
>
> 10. spring-jcl
>
> 11. spring-jdbc
>
> 12. spring-jms
>
> 13. spring-messaging
>
> 14. spring-orm
>
> 15. spring-oxm
>
> 16. spring-r2dbc
>
> 17. spring-test
>
> 18. spring-tx
>
> 19. spring-web
>
> 20. spring-webflux
>
> 21. spring-webmvc
>
> 22. spring-websocket

##### 3. Spring 编程模型

> 1. 面向对象编程
>
>   - 契约接口
>   - 设计模式
>   - 对象继承
>
> 2. 面向切面编程
>
>   - 动态代理
>   - 字节码提升
>
> 3. 面向元编程
>
>   - 注解
>   - 配置
>   - 泛型
>
> 4. 函数驱动
>
>   - 函数接口
>   - Reactive
>
> 5. 模块驱动


### 第二章：重新认识IoC (9讲)

1. IoC 实现

> 依赖查找
>
> 依赖注入

2. 

BeanInfo
Introspector
PropertyEditor -> PropertyEditorSupport
