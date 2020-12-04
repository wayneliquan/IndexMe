

1. 依赖注入注解

   @Autowired: 按名称注入

   > spring 4.3之后，引入了一个新特性：当构造方法的参数为单个构造参数时，可以不使用@Autowired进行注解。

   @Resource: 按类型注入

2. 

```
@Configuration
@ConditionalOnClass(RedisOperations.class)
@EnableConfigurationProperties(RedisProperties.class)
@Import({ LettuceConnectionConfiguration.class, JedisConnectionConfiguration.class })
```

```java
@ConditionalOnMissingBean(name = "redisTemplate") // 判断在没有redisTemplate这个名字的Bean进行导入
@ConditionalOnClass(xxx.class)
```



```java
@EnableConfigurationProperties(xxx.class) // 启动把使用 @ConfigurationProperties 的类进行了一次注入。
```



```java
@ConfigurationProperties(prefix = "spring.redis") // 使用@EnableConfigurationProperties启动注入或也可以@Component进行注入
```

