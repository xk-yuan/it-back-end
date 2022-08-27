# Project Engineering Tools

> 项目工程化工具, 项目依赖管理

> maven

> gradle & groovy

## maven

### 资源

> [官网](https://maven.apache.org/)

> [Releases](https://maven.apache.org/download.cgi)

> [仓库](https://mvnrepository.com/)

### 安装

```
[下载]

  ：http://maven.apache.org/download.cgi

  ：http://mirror.bit.edu.cn/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.zip

[配置]

  ：MAVEN_HOME=E:\Maven\apache-maven-3.5.0

  ：PATH=...;%MAVEN_HOME%\bin;

  ：MAVEN_OPT=-Xms128m -Xmx512m

[检验]

  ：mvn -v

Apache Maven 3.6.1 (d66c9c0b3152b2e69ee9bac180bb8fcc8e6af555; 2019-04-05T03:00:29+08:00)
Maven home: C:\Tools\apache-maven-3.6.1\bin\..
Java version: 1.8.0_211, vendor: Oracle Corporation, runtime: C:\Tools\Java\jre1.8.0_211
Default locale: zh_CN, platform encoding: GBK
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"

[配置]

  ：localRepository=D:\cache\localRepository  # 配置本地安装仓库

```
