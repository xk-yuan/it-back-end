# Gradle

>

专注于灵活性和性能的开源构建自动化工具, Gradle构建脚本是使用Groovy或Kotlin DSL 编写的。

## 资源

> [官网](https://gradle.org/)

> [Releases](https://gradle.org/releases/)

> [文档](https://docs.gradle.org/)

> [gradle](https://github.com/gradle/gradle)

> [guides](https://github.com/gradle/guides)

> [Groory DSL](https://docs.gradle.org/current/dsl/index.html)

> [gradle-exemplar](https://github.com/gradle/exemplar)

> [gradle-build-scan-quickstart](https://github.com/gradle/gradle-build-scan-quickstart)


## 配置文件

> settings.gradle
```
用来管理多项目

rootProject.name , 定义项目坐标 name 值

```
> build.gradle
```

apply 定义使用的应用插件
> apply plugin: 'java'
> apply plugin: 'war'

> 外部依赖定义
> dependecies 声明项目依赖 (testCompile 测试编译阶段依赖, testRuntime, runtime, complile)
> dependencies {
>   compile group: 'commons-collections', name: 'commons-collections', version: '3.2'
>   testCompile group: 'junit', name: 'junit', version: '4.11'
> }

> 仓库定义
> repositories 定义Maven仓库
> repositories {
>    mavenCentral(
>       url 'http://maven.aliyun.com/nexus/content/groups/public/'
>    )
>    mavenLocal()
> }
```

### [java 配置](https://www.w3cschool.cn/gradle/5vdr1hug.html)

> apply plugin: 'java'  # JAVA脚本插件, 提供了诸如编译，测试，打包等一些功能
```
> java 标准项目目录
project  
    +build  
    +src/main/java        # 源码目录
    +src/main/resources
    +src/test/java        # 测试源码目录
    +src/test/resources  
```

> 查询任务列表
>
> - gradle tasks
>   - gradle build    # 执行构建
>   - gradle clean    # 清理项目
>   - gradle assemble # 编译并打包 jar 文件，但不会执行单元测试
>   - gradle check    # 编译并测试代码

> 查询所有属性
>
> - gradle propertie s


> 自定义 源码版本 & 项目版本 & MANIFEST.MF & test 添加系统属性 & 发布 jar 包
```
sourceCompatibility = 1.8
version = '1.0.0'
jar {
    manifest {
        attributes 'Implementation-Title': 'Gradle Quickstart', 'Implementation-Version': version
    }
}

test {
    systemProperties 'property': 'value'
}

uploadArchives {
    repositories {
       flatDir {
           dirs 'repos'
       }
    }
}
```

> 更改项目布局
```
sourceSets {
    main {
        java {
            srcDir 'src/java'
        }
        resources {
            srcDir 'src/resources'
        }
    }
}  
```


> 完整实例
```
apply plugin: 'java'
apply plugin: 'eclipse'
sourceCompatibility = 1.5
version = '1.0'
jar {
    manifest {
        attributes 'Implementation-Title': 'Gradle Quickstart', 'Implementation-Version': version
    }
}
repositories {
    mavenCentral()
}
dependencies {
    compile group: 'commons-collections', name: 'commons-collections', version: '3.2'
    testCompile group: 'junit', name: 'junit', version: '4.+'
}
test {
    systemProperties 'property': 'value'
}
uploadArchives {
    repositories {
       flatDir {
           dirs 'repos'
       }
    }
}
```

### spring-boot 配置
> spring-boot 配置案例
```
// buildscript 代码块中脚本优先执行
buildscript {
 
	// ext 用于定义动态属性
	ext {
		springBootVersion = '1.5.2.RELEASE'
	}
			
	// 自定义  Thymeleaf 和 Thymeleaf Layout Dialect 的版本
	ext['thymeleaf.version'] = '3.0.3.RELEASE'
	ext['thymeleaf-layout-dialect.version'] = '2.2.0'
	
	// 自定义  Hibernate 的版本
	ext['hibernate.version'] = '5.2.8.Final'
 
	// 使用了 Maven 的中央仓库（你也可以指定其他仓库）
	repositories {
		//mavenCentral()
		maven {
			url 'http://maven.aliyun.com/nexus/content/groups/public/'
		}
	}
	
	// 依赖关系
	dependencies {
		// classpath 声明说明了在执行其余的脚本时，ClassLoader 可以使用这些依赖项
		classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
	}
}
 
// 使用插件
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
 
// 打包的类型为 jar，并指定了生成的打包的文件名称和版本
jar {
	baseName = 'springboot-test'
	version = '1.0.0'
}
 
// 指定编译 .java 文件的 JDK 版本
sourceCompatibility = 1.8
 
// 默认使用了 Maven 的中央仓库。这里改用自定义的镜像库
repositories {
	//mavenCentral()
	maven {
		url 'http://maven.aliyun.com/nexus/content/groups/public/'
	}
}
 
// 依赖关系
dependencies {
 
	// 该依赖对于编译发行是必须的
	compile('org.springframework.boot:spring-boot-starter-web')
 
	// 添加 Thymeleaf 的依赖
	compile('org.springframework.boot:spring-boot-starter-thymeleaf')
 
	// 添加  Spring Security 依赖
	compile('org.springframework.boot:spring-boot-starter-security')
	
	// 添加 Spring Boot 开发工具依赖
 	//compile("org.springframework.boot:spring-boot-devtools")
 
	// 添加 Spring Data JPA 的依赖
	compile('org.springframework.boot:spring-boot-starter-data-jpa')
	
	// 添加 MySQL连接驱动 的依赖
	compile('mysql:mysql-connector-java:6.0.5')
	
	// 添加   Thymeleaf Spring Security 依赖，与 Thymeleaf 版本一致都是 3.x
	compile('org.thymeleaf.extras:thymeleaf-extras-springsecurity4:3.0.2.RELEASE')
	
	// 添加  Apache Commons Lang 依赖
	compile('org.apache.commons:commons-lang3:3.5')
	
	// 该依赖对于编译测试是必须的，默认包含编译产品依赖和编译时依
	testCompile('org.springframework.boot:spring-boot-starter-test')
}
 
```

### 多项目构建

> 定义一个多项目构建工程需要在根目录创建一个 settings.gradle 配置文件来指明构建包含哪些项目

> 公共配置, 会在根项目上采用配置注入的方式定义一些公共配置。根项目就像一个容器，子项目会迭代访问它的配置并注入到自己的配置中

> settings.gradle
```
include "shared", "api", "services:webservice", "services:shared"

subprojects {
    apply plugin: 'java'
    apply plugin: 'eclipse-wtp'

    repositories {
       mavenCentral()
    }

    dependencies {
        testCompile 'junit:junit:4.11'
    }
    
    version = '1.0.0'
    
    jar {
        manifest.attributes provider: 'gradle'
    }
}
```

> 工程依赖, 同一个构建中可以建立工程依赖，一个工程的 jar 包可以提供给另外一个工程使用
> api/build.gradle
```
dependencies {
    compile project(':shared')
}

// 多项目构建-发布

task dist(type: Zip) {
    dependsOn spiJar
    from 'src/dist'

    into('libs') {
        from spiJar.archivePath
        from configurations.runtime
    }
}

artifacts {
   archives dist
}
```



```
multiproject/
  api/
  services/
    webservice/
  shared/
```
