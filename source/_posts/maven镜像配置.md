---
title: maven镜像配置
date: 2016-12-18 16:47:44
categories: 开发工具
tags:
- apache
- maven
---
开始接触maven的时候在国内的网络环境中总是容易让人放弃，这是由于maven的机制，需要从中央库下载许多东西，包括maven自身的插件和项目中需要依赖的库。而恰恰maven的中央库在国内访问时总是会出现各种不稳定或者速度过慢的情况，故使用maven前首要工作就是配置好合适的仓库，以顺利下载各种需要的资源。
<!-- more -->

# 工具
[Apache Maven](http://maven.apache.org)
版本: 3.3.9

# 配置文件
在`settings.xml`配置文件中的`<mirrors>`小节增加需要的镜像地址。

## 配置文件位置
maven可以有两个地方管理`settings.xml`文件：
* global: ${maven.home}/conf/settings.xml
* user: ${user.home}/.m2/settings.xml

两个文件同时存在时会互相合并，并且`user`配置要优先于`global`配置。
> 参考：[Settings Reference](http://maven.apache.org/settings.html)

## 配置内容
```xml
<settings>
  ...
  <mirrors>
    <mirror>
      <id></id>
      <name></name>
      <url></url>
      <mirrorOf></mirrorOf>
    </mirror>
  </mirrors>
  ...
</settings>
```

> 参考：[Using Mirrors for Repositories](http://maven.apache.org/guides/mini/guide-mirror-settings.html)

### 配置项说明

> 参考：[Settings#mirror](http://maven.apache.org/ref/3.3.9/maven-settings/settings.html#mirror)

### 推荐国内镜像仓库
* 阿里云：http://maven.aliyun.com/nexus/content/groups/public/
* 开源中国：http://maven.oschina.net/content/groups/public/

### 配置例
```xml
<mirror>
  <id>alimaven</id>
  <name>aliyun maven</name>
  <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
  <mirrorOf>central</mirrorOf>        
</mirror>
```

