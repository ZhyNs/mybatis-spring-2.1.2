Mybatis-Spring官方源码中文注释
======================
MyBatis 与 Spring 的集成主要依靠 MyBatis-Spring 模块。这个模块提供了一些类和配置，帮助开发者在 Spring 环境中方便地使用 MyBatis。  

核心思想是通过 Spring 的 IoC 容器管理 MyBatis 的核心组件（如 SqlSessionFactory 和 SqlSession），从而实现无缝集成。  
提供两种方式：基于xml配置、基于注解配置

Mybatis-Spring有两部分内容：
- 项目的mapper.xml扫描
- 帮助Spring管理SqlSessionFactory和SqlSession

mapper类扫描
---------------
入口类：`org.mybatis.spring.config.NamespaceHandler`

mapper.xml文件的扫描有两种方式：注解扫描（常用）、xml配置扫描
- 注解扫描的入口：`org.mybatis.spring.annotation.MapperScannerRegistrar.registerBeanDefinitions()`
- xml配置扫描的入口：`org.mybatis.spring.config.MapperScannerBeanDefinitionParser.parseInternal()`

注意：扫描的xxxMapper类

SqlSessionFactory及SqlSession相关
---------------------
入口类：`org.mybatis.spring.SqlSessionFactoryBean`

在项目中，需要通过SqlSessionFactoryBean手动创建SqlSessionFactory。

注意：mapper.xml文件在这部分扫描。