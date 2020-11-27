1. 开发时打印日志

   ```
   mybatis:
     configuration:
       log-impl: org.apache.ibatis.logging.stdout.StdOutImpl
   ```

   

2. 



plugins中interceptor的原理。



1. 注解@Intercepts， 配置文件mybatis-config.xml 中的plugins

   解析mybatis-config.xml 中的plugins， 使用JDK动态代理生成interceptor, 调用Configuration的addInterceptor方法添加。

2. 



注解@Intercepts是如何扫描的呢？



解析配置的过程

![XMLConfigBuilder](../../images/Mybatis-BaseBuilder.png)  



创建Executor的过程

![Plugins](../../images/Mybatis-Plugins-wrap-newExecutor.png)  





添加interceptor的过程。

![addInterceptor](../../images/Mybatis-addInterceptor.png)  





mybatis的入口是sqlSessionFactory。

为了适配Spring, 在mybatis-spring 进行了适配。 SqlSessionFactoryBean。 一般数据源是要配置的