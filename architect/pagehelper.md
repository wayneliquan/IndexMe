依赖

```
<dependency>
	<groupId>com.github.pagehelper</groupId>
	<artifactId>pagehelper-spring-boot-starter</artifactId>
	<version>1.2.12</version>
</dependency>
```



配置

```
# 分页插件配置
pagehelper:
  helperDialect: mysql
  supportMethodsArguments: true
```



// mybatis-pagehelper

```
/**
* page: 第几页
* pageSize: 每页显示条数
*/
PageHelper.startPage(page, pageSize);
```

