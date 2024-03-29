+++
title="mybatis-plus"
date= 2019-08-25 16:19:30
tags=["mybatis"]
categories=["mybatis"]
toc=true
+++
## mybatis 依赖添加并写配置
```xml
<plugins>
    <plugin>
        <groupId>org.mybatis.generator</groupId>
        <artifactId>mybatis-generator-maven-plugin</artifactId>
        <version>1.3.7</version>
        <configuration>
            <verbose>true</verbose>
            <overwrite>true</overwrite>
            <configurationFile>src\main\resources\generationConfig.xml</configurationFile>
        </configuration>
        <dependencies>
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>5.1.47</version>
                <!-- 版本过高无法生成 delete updata 方法 -->
            </dependency>
        </dependencies>
    </plugin>
</plugins>
```
## generationConfig.xml 文件
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
        PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">
<generatorConfiguration>
    <!--导入属性配置-->
    <context id="default" targetRuntime="MyBatis3">
        <!--覆盖生成XML文件-->
        <plugin type="org.mybatis.generator.plugins.UnmergeableXmlMappersPlugin"/>
        <!-- optional，旨在创建class时，对注释进行控制 -->
        <commentGenerator>
            <property name="suppressDate" value="true"/>
            <property name="suppressAllComments" value="true"/>
        </commentGenerator>
        <!--jdbc的数据库连接 -->
        <jdbcConnection driverClass="com.mysql.jdbc.Driver"
                        connectionURL="jdbc:mysql://localhost:3306/poplar?
                                serverTimezone=CTT&amp;
                                useUnicode=true&amp;
                                characterEncoding=utf-8&amp;
                                allowMultiQueries=true&amp;
                                useSSL=false"
                        userId="root"
                        password="">
            <!-- 以上数据库账号密码 需修改 -->
        </jdbcConnection>
        <!-- 非必需，类型处理器，在数据库类型和java类型之间的转换控制-->
        <javaTypeResolver>
            <property name="forceBigDecimals" value="false"/>
        </javaTypeResolver>
        <!-- Model模型生成器,用来生成含有主键key的类，记录类 以及查询Example类
            targetPackage     指定生成的model生成所在的包名
            targetProject     指定在该项目下所在的路径 -->
        <javaModelGenerator targetPackage="com.phoenix.dao.entity" targetProject="./src/main/java">
            <!-- 是否允许子包，即targetPackage.schemaName.tableName -->
            <property name="enableSubPackages" value="false"/>
            <!-- 是否对model添加 构造函数 -->
            <property name="constructorBased" value="false"/>
            <!-- 是否对类CHAR类型的列的数据进行trim操作 -->
            <property name="trimStrings" value="true"/>
            <!-- 建立的Model对象是否 不可改变  即生成的Model对象不会有 setter方法，只有构造方法 -->
            <property name="immutable" value="false"/>
        </javaModelGenerator>
        <!--mapper映射文件生成所在的目录 为每一个数据库的表生成对应的SqlMap文件 -->
        <sqlMapGenerator targetPackage="mapper" targetProject="./src/main/resources">
            <property name="enableSubPackages" value="false"/>
        </sqlMapGenerator>
        <javaClientGenerator type="XMLMAPPER" targetPackage="com.phoenix.dao.mapper" targetProject="./src/main/java">
            <!-- enableSubPackages:是否让schema作为包的后缀 -->
            <property name="enableSubPackages" value="true"/>
        </javaClientGenerator>
        <table tableName="t_user" domainObjectName="User"
               enableCountByExample="false"
               enableUpdateByExample="false"
               enableDeleteByExample="false"
               enableSelectByExample="false"
               selectByExampleQueryId="false"/>
        <!--<table tableName="t_user" domainObjectName="User"-->
        <!--       enableCountByExample="true"-->
        <!--       enableUpdateByExample="true"-->
        <!--       enableDeleteByExample="true"-->
        <!--       enableSelectByExample="true"-->
        <!--       selectByExampleQueryId="true">-->
        <!--    <columnOverride column="detail" jdbcType="VARCHAR"/>-->
        <!--    <columnOverride column="sub_images" jdbcType="VARCHAR"/>-->
        <!--</table>-->
    </context>
</generatorConfiguration>
</generatorConfiguration>
```