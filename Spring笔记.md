# spring依赖

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.3.16</version>
</dependency>
```

# applicationContext.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <!--
    id 等价于 变量名
    class 等价于要new的对象
    property 等价于对象中的一个属性 value给该属性赋值 ref引用Spring容器中创建好的对象
    -->

</beans>
```





# C/P标签

```xml
xmlns:c="http://www.springframework.org/schema/c"
xmlns:p="http://www.springframework.org/schema/p"
```





# 注解配置

```xml
<?xml version="1.0" encoding="UTF-8"?> <beans xmlns="http://www.springframework.org/schema/beans"    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"    xmlns:context="http://www.springframework.org/schema/context"    xsi:schemaLocation="http://www.springframework.org/schema/beans        https://www.springframework.org/schema/beans/spring-beans.xsd        http://www.springframework.org/schema/context        https://www.springframework.org/schema/context/spring-context.xsd">     
    <context:annotation-config/> 
</beans>
```



# spring-mybatis-config

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
<!--Datasource：使用spring的数据源替换mybatis的配置 使用spring的jdbc-->
    <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
        <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
        <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=false&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
        <property name="username" value="root"/>
        <property name="password" value="QAQm..02r"/>
    </bean>
<!--sqlSessionFactory-->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <property name="dataSource" ref="dataSource"/>
<!--绑定mybatis配置文件-->
        <property name="configLocation" value="classpath:mybatis-config.xml"/>
        <property name="mapperLocations" value="classpath*: com/doromv/mapper/*.xml"/>
    </bean>
<!--等价于sqlSession-->
    <bean id="sqlSessionTemplate" class="org.mybatis.spring.SqlSessionTemplate">
<!--只能用构造器注入，因为它没有set方法-->
        <constructor-arg index="0" ref="sqlSessionFactory"/>
    </bean>
   
</beans>
```



# 动态代理生成代理类

```java
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;

/**
 * @author shkstart
 * @create 2022-02-28-19:40
 */
//用这个类自动生成代理类
public class ProxyInvocationHandler implements InvocationHandler {
    //被代理的接口
    private Object target;

    public void setTarget(Object target) {
        this.target = target;
    }

    //生成得到代理类
    public Object getProxy() {
        return Proxy.newProxyInstance(this.getClass().getClassLoader(), target.getClass().getInterfaces(), this);
    }

    @Override
    //处理代理实例，并返回结果
    public Object invoke(Object o, Method method, Object[] objects) throws Throwable {
        log(method.getName());
        Object invoke = method.invoke(target, objects);
        return invoke;
    }
    public void log(String msg){
        System.out.println("执行了"+msg+"方法");
    }
}
```
