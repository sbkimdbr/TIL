### Maria Db에서 데이터 받아오기

```java
//my spring.xml ,spring.xml 의 driverclassname 변경
<bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
 		<property name="driverClassName" value="org.mariadb.jdbc.Driver"/>
        <property name="url" value="jdbc:mariadb://192.168.111.111:3306/shopdb"/>
 		<property name="username" value="user1"/>
 		<property name="password" value="111111"/>
 </bean>
/*   "oracle.jdbc.driver.OracleDriver"
  -->"org.mariadb.jdbc.Driver"
    
    "jdbc:oracle:thin:@192.168.111.110:1521:xe" 
 -->"jdbc:mariadb://192.168.111.111:3306/shopdb"*/
```

