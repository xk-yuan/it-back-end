# spring boot starter

>

## 资源

> [官网](https://spring.io/projects/spring-boot/) | [](https://start.spring.io/)

> [在SpringBoot中如何自定义starter](https://zhuanlan.zhihu.com/p/456809064)
>
> [](https://segmentfault.com/a/1190000019687720)

## 简介

![个性化加载配置](https://pic2.zhimg.com/80/v2-3d3ccfc6b11d4aecdc30d4af73a16ffd_1440w.jpg)

### 自定义starter

> platform-starter-autoconfigure 自动配置包

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter</artifactId>
</dependency>

<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-configuration-processor</artifactId>
  <optional>true</optional>
</dependency>
```

编写自动配置包相关业务代码

```java
com
  platform
    auto
      PlatformServiceAutoConfiguration // 自动配置类
    bean
      PlatformProperties               // 自定义属性类
    service
      PlatformService                  // 业务代码
```

```java
@EnableConfigurationProperties

```

- META-INF/spring.factories

> platform-starter 启动器

```xml
<dependency>
  <groupId>platform</groupId>
  <artifactId>platform-starter-autoconfigure</artifactId>
</dependency>
```

