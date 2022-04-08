# Swagger

## 依赖

```xml
<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger2 -->
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger2</artifactId>
   <version>2.9.2</version>
</dependency>
<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui -->
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger-ui</artifactId>
   <version>2.9.2</version>
</dependency>
```
## 配置swagger信息,并且根据环境来启动swagger

```java
@Configuration
@EnableSwagger2
public class SwaggerConfig {
    //配置了Swagger的Docket的bean实例
    @Bean
    public Docket docket(Environment environment){
        Profiles profiles=Profiles.of("dev","test");//设置要显示的swagger环境
        boolean flag = environment.acceptsProfiles(profiles);//通过environment.acceptsProfiles判断是否处在自己设定的环境当中
        return  new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .enable(flag)//设置swagger是否开启
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.doromv.controller"))//扫描某个包下的内容
                .paths(PathSelectors.ant("/doromv/**"))//过滤某个包下的内容
                .build();
    }
    //配置swagger信息
    private ApiInfo apiInfo(){
        final Contact DEFAULT_CONTACT = new Contact("周锐", "https://space.bilibili.com/103790498", "DoromvQAQ@163.com");
         return new ApiInfo("Doromv的SwaggerAPI文档",
                 "学无止境",
                 "1.0",
                 "https://space.bilibili.com/103790498",
                 DEFAULT_CONTACT,
                 "Apache 2.0",
                 "http://www.apache.org/licenses/LICENSE-2.0",
                 new ArrayList());
    }
}
```

## API文档的分组

```java
@Bean
public Docket docket1(){
    return new Docket(DocumentationType.SWAGGER_2)
            .groupName("R-God");
}
```

## 给各种属性、类、方法、变量加注释
```java
//@Api(注释)
@ApiModel("用户实体类")
public class User {
    @ApiModelProperty("用户名")
    public String username;
    @ApiModelProperty("密码")
    public String password;
}
```

```java
@RestController
public class HelloController {
    @ApiOperation("Hello控制类")
    @GetMapping("/hello")
    public String hello1(@ApiParam("用户名") String username){
        return "hello"+username;
    }
}
```
## 将pojo注册到swagger

```java
@RestController
public class HelloController {
//只要我们的接口中，返回值存在实体类，他就会被扫描到swagger中
@PostMapping("/user")
public User user(){
    return new User();
}
}
```
