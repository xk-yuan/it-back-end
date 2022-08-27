# spring boot actuator

> 

## 资源


## 简介

Spring Boot 的 Actuator 提供了很多生产级的特性，比如监控和度量Spring Boot 应用程序。Actuator 的这些特性可以通过众多 REST 接口、远程 shell 和 JMX 获得。

> 接口

01. GET   /autoconfig	    提供了一份自动配置报告，记录哪些自动配置条件通过了，哪些没通过; 接口能告诉你为什么会有这个 bean ，或者为什么没有这个 bean。
02. GET	  /configprops	    描述配置属性(包含默认值)如何注入Bean
03. GET	  /beans	        描述应用程序上下文里全部的Bean，以及它们的关系; 它会返回一个 JSON 文档，描述上下文里每个 bean 的情况，包括其 Java 类型以及注入的其它 bean。
04. GET	  /dump	            获取线程活动的快照
05. GET	  /env	            获取全部环境属性
06. GET	  /env/{name}	    根据名称获取特定的环境属性值
07. GET	  /health	        报告应用程序的健康指标，这些值由HealthIndicator的实现类提供
08. GET	  /info	            获取应用程序的定制信息，这些信息由info打头的属性提供
09. GET	  /mappings	        描述全部的URI路径，以及它们和控制器(包含Actuator端点)的映射关系
10. GET	  /metrics	        报告各种应用程序度量信息，比如内存用量和HTTP请求计数
11. GET	  /metrics/{name}	报告指定名称的应用程序度量值
12. POST  /shutdown	        关闭应用程序，要求endpoints.shutdown.enabled设置为true
13. GET	  /trace	        提供基本的HTTP请求跟踪信息(时间戳、HTTP头等)

>

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

### /beans

bean：    Spring 应用程序上下文中的 Bean 名称或 ID。
resource：.class 文件的物理位置，通常是一个 URL，指向构建出的 JAR 文件。这会随着应用程序的构建和运行方式发生变化。
dependencies：当前 Bean 注入的 Bean ID 列表。
scope：   Bean 的作用域（通常是单例，这也是默认作用域）。
type：    Bean 的 Java 类型。

```json
[
    {
        "context": "application",
        "parent": null,
        "beans": [
            {
                "bean": "demoApplication",
                "aliases": [],
                "scope": "singleton",
                "type": "com.example.DemoApplication$$EnhancerBySpringCGLIB$$88686e04",
                "resource": "null",
                "dependencies": []
            },
            {
                "bean": "org.springframework.boot.autoconfigure.internalCachingMetadataReaderFactory",
                "aliases": [],
                "scope": "singleton",
                "type": "org.springframework.core.type.classreading.CachingMetadataReaderFactory",
                "resource": "null",
                "dependencies": []
            }
        ]
    }
]
```

### /autoconfig

```json
{
    "positiveMatches": {
        "AuditAutoConfiguration#auditListener": [
            {
                "condition": "OnBeanCondition",
                "message": "@ConditionalOnMissingBean (types: org.springframework.boot.actuate.audit.listener.AbstractAuditListener; SearchStrategy: all) did not find any beans"
            }
        ],
        "MultipartAutoConfiguration#multipartConfigElement": [
            {
                "condition": "OnBeanCondition",
                "message": "@ConditionalOnMissingBean (types: javax.servlet.MultipartConfigElement; SearchStrategy: all) did not find any beans"
            }
        ]
    },
    "negativeMatches": {
        "AuditAutoConfiguration#authenticationAuditListener": {
            "notMatched": [
                {
                    "condition": "OnClassCondition",
                    "message": "@ConditionalOnClass did not find required class 'org.springframework.security.authentication.event.AbstractAuthenticationEvent'"
                }
            ],
            "matched": []
        },
        "AuditAutoConfiguration#authorizationAuditListener": {
            "notMatched": [
                {
                    "condition": "OnClassCondition",
                    "message": "@ConditionalOnClass did not find required class 'org.springframework.security.access.event.AbstractAuthorizationEvent'"
                }
            ],
            "matched": []
        }
    }
}
```