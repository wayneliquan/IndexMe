<div align='center' ><font size='70'>SpringBoot集成Swagger2</font></div>

[toc]

## 1. 导入依赖

```
<!-- swagger2 配置 -->
<dependency>
	<groupId>io.springfox</groupId>
	<artifactId>springfox-swagger2</artifactId>
	<version>2.4.0</version>
</dependency>
<dependency>
	<groupId>io.springfox</groupId>
	<artifactId>springfox-swagger-ui</artifactId>
	<version>2.4.0</version>
</dependency>
<dependency>
	<groupId>com.github.xiaoymin</groupId>
	<artifactId>swagger-bootstrap-ui</artifactId>
	<version>1.6</version>
</dependency>
```



## 2. 配置

```
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.service.Contact;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

@Configuration
@EnableSwagger2
public class Swagger2 {

//    http://localhost:8080/swagger-ui.html     原路径
//    http://localhost:8080/doc.html     原路径

    // 配置swagger2核心配置 docket
    @Bean
    public Docket createRestApi() {
        return new Docket(DocumentationType.SWAGGER_2)  // 指定api类型为swagger2
                    .apiInfo(apiInfo())  // 用于定义api文档汇总信息
                    .select()
                    .apis(RequestHandlerSelectors.basePackage("xxx.xxx.xxx"))  // 指定controller包
                    .paths(PathSelectors.any())  // 所有controller
                    .build();
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("xxx-title")  // 文档页标题
                .contact(new Contact("xxx-name", "http://xxx.url", "xxx-email"))   // 联系人信息
                .description("xxxxxx")  // 详细信息
                .version("x.y.z")   // 文档版本号
                .termsOfServiceUrl("https://xxxxx") // 网站地址
                .build();
    }

}
```

整合Spring Security

```java
// 配置权限豁免，才能正常访问 localhost:8080/swagger-ui.html
.antMatchers("/swagger-ui.html").permitAll()
.antMatchers("/swagger-resources/**").permitAll()
.antMatchers("/webjars/**").permitAll()
.antMatchers("/v2/api-docs").permitAll()
```



## 3. 编写文档

```
@Api(tags = {"标签1","标签2"})
public class XXXController{
    @ApiOperation(value = "summary", notes = "详细描述", httpMethod = "GET")
    @GetMapping("/xxx/{paramName}")
    public XXX funcname(
        @ApiParam(name = "paramName", value = "paramName对应的参数描述", required = true)
        @PathVariable Integer rootCatId) {

        return XXX;
    }
}
```



```
@ApiModelProperty(hidden = true) 方法不显示
```



