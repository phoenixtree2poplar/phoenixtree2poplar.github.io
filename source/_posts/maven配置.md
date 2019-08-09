---
title: maven配置
date: 2018-08-31 10:53:29
tags:
	- maven设置conf
	- setting.xml
---
## 先附上缩减后的源配置文件  setting.xml  在 maven主目录/conf下
```xml
<?xml version="1.0" encoding="UTF-8"?>

<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
          http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <!-- localRepository元素根据个人习惯设置本地仓库下载位置，默认为${user.home}/.m2/repository -->
    <localRepository>D:\mavenjar</localRepository>
    <mirrors>
        <!-- mirror 元素设置镜像，这里设置为阿里镜像,在国内阿里镜像较快 -->
        <mirror>
            <id>alimaven</id>
            <mirrorOf>central</mirrorOf>
            <name>aliyun maven</name>
            <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
        </mirror>
    </mirrors>
</settings>
```
