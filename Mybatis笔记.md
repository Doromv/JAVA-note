# Build 过滤器

 <!--在build中配置resources，来防止我们资源导出失败的问题-->

```xml
 <build>

    <resources>

      <resource>

        <directory>src/main/java</directory>

        <includes>

          <include>**/*.properties</include>

          <include>**/*.xml</include>

        </includes>

        <filtering>false</filtering>

      </resource>



      <resource>

        <directory>src/main/resources</directory>

        <includes>

          <include>**/*.xml</include>

          <include>**/*.properties</include>

        </includes>

        <filtering>false</filtering>

      </resource>

    </resources>

  </build>
```



# Log4j

#将等级为DEBUG的日志信息输出到console和file这两个目的地，console和file的定义在下面的代码
log4j.rootLogger=DEBUG,console,file

#控制台输出的相关设置
log4j.appender.console = org.apache.log4j.ConsoleAppender
log4j.appender.console.Target = System.out
log4j.appender.console.Threshold=DEBUG
log4j.appender.console.layout = org.apache.log4j.PatternLayout
log4j.appender.console.layout.ConversionPattern=[%c]-%m%n

#文件输出的相关设置
log4j.appender.file = org.apache.log4j.RollingFileAppender
log4j.appender.file.File=./log/doromv.log
log4j.appender.file.MaxFileSize=10mb
log4j.appender.file.Threshold=DEBUG
log4j.appender.file.layout=org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern=[%p][%d{yy-MM-dd}][%c]%m%n

#日志输出级别
log4j.logger.org.mybatis=DEBUG
log4j.logger.java.sql=DEBUG
log4j.logger.java.sql.Statement=DEBUG
log4j.logger.java.sql.ResultSet=DEBUG
log4j.logger.java.sql.PreparedStatement=DEBUG



# mybatis-config

```xml
<?xml version="1.0" encoding="UTF-8" ?>

<!DOCTYPE configuration



    PUBLIC "-//mybatis.org//DTD Config 3.0//EN"

   "http://mybatis.org/dtd/mybatis-3-config.dtd">

<configuration>

  <properties resource="db.properties"/>

  <environments default="development">

    <environment id="development">

    <transactionManager type="JDBC"/>

     <dataSource type="POOLED">

       <property name="driver" value="${driver}"/>

      <property name="url" value="${url}"/>

        <property name="username" value="${username}"/>

      <property name="password" value="${password}"/>

      </dataSource>

   </environment>

  </environments>

<!--每一个Mapper.xml都需要在Mybatis核心配置文件中注册！-->

  <mappers>

    <mapper resource="com/doromv/dao/UserMapper.xml"/>

  </mappers>

</configuration>
```



# db.properties

```properties
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/ssmbuild?useSSL=false&useUnicode=true&characterEncoding=utf8
jdbc.username=root
jdbc.password=QAQm..02r
```



# MybatisUtil

```java
public class MybatisUtils {
    private static SqlSessionFactory sqlSessionFactory;
    static {
        try {
            String resource="mybatis-config.xml";
            InputStream inputStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory= new SqlSessionFactoryBuilder().build(inputStream);
        } catch (IOException e) {
            e.printStackTrace();
        }

    }

    public static SqlSession getSqlsession(){
        SqlSession sqlSession = sqlSessionFactory.openSession(true);
        return sqlSession;
    }
}
```



# Mybatis 一对多SQL

```xml
<resultMap id="TeacherMapper" type="Teacher">
    <result property="id" column="tid"/>
    <result property="name" column="tname"/>
    <collection property="students" ofType="Student">
        <result property="id" column="sid"/>
        <result property="name" column="sname"/>
        <result property="tid" column="tid"/>
    </collection>
</resultMap>
<select id="getTeacherAndStudent" resultMap="TeacherMapper">
    select t.id tid,t.name tname,s.id sid,s.name sname from student s,teacher t where s.tid=t.id and t.id=#{tid};
</select>
```



# Mybatis 多对一SQL

```xml
  <resultMap id="StudentMap2" type="Student">
        <result column="sid" property="id"/>
        <result column="sname" property="name"/>
        <association property="teacher" javaType="Teacher">
            <result column="tname" property="name"/>
        </association>
    </resultMap>
    <select id="getStudent2" resultMap="StudentMap2" >
    select s.id sid,s.name sname,t.name tname from student s,teacher t where s.tid=t.id;
</select>
```



# 缓存原理

<img src="C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20220225152700554.png" alt="image-20220225152700554"  />



