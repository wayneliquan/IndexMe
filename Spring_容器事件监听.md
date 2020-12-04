Spring 容器事件监听

[toc]

```
ContextClosedEvent  <-- ConfigurableApplicationContext.refresh()
ContextRefreshedEvent <-- ConfigurableApplicationContext.start()  
ContextStartedEvent <-- ConfigurableApplicationContext.stop()
ContextStoppedEvent <-- ConfigurableApplicationContext.close()
```



Demo1: 普通的Spring

```java
public class App {

	public static void main(String[] args) {
		AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext();
		context.addApplicationListener(new ApplicationListener<ContextRefreshedEvent>() {
			@Override
			public void onApplicationEvent(ContextRefreshedEvent event) {
				//...
			}
		});
		context.scan("package name"); //包扫描路劲
		context.refresh(); // 调用这个才会ContextRefreshedEvent
		context.start();
		context.stop(); 
		context.close();
	}
}
```



Demo2: SpringBoot

```java
@Component //加入Spring容器， SrpingBoot启动时会自己注册的。
public class MyApplicationListener implements ApplicationListener<ContextRefreshedEvent> {...}
public class MyApplicationListener2 implements ApplicationListener<ContextStartEvent> {...}


@SpringBootApplication
public class App {
    public static void main(String[] args) {
    	ConfigurableApplicationContext context = SpringApplication.run(App.class, args);
        context.start(); // 这里触发 ContextStartEvent
    }
}
// 注明： 这里的ContextRefreshedEvent 优先于ContextStartEvent。
```



参考：

[ContextClosedEvent 、ContextRefreshedEvent 、ContextStartedEvent 、ContextStoppedEvent 、RequestHandleEvent （spring容器钩子函数)](https://www.cnblogs.com/alex-xyl/p/13432162.html)

