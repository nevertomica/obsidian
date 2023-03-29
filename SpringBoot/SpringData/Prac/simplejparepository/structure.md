##### 主要類別
BaseRepositor: subinterface of CrudRepository
User: Entity
UersRepository: subclass of SimpleJpaRepository, the impl of BaseRepository


##### 實作細節
1. 需要透過 SimpleJpaRepository 的建構子建立子類別的建構子，
 父建構子其一是下方功能 Creates a new [`SimpleJpaRepository`](https://docs.spring.io/spring-data/data-jpa/docs/current/api/org/springframework/data/jpa/repository/support/SimpleJpaRepository.html "class in org.springframework.data.jpa.repository.support") to manage objects of the given domain type.
2. BaseRepository is public, and all methods without access modifiers are public
3. 在寫好註冊檔的情況下, JPA 會根據 @Entity 去建立表

 for 3. 
		 特別注意 `@Table(name = "/`user /`"`) 其中跳脫字元不可省略  \` \` 

下方為 Entity 設定
```
@Entity  
@Setter  
@Table(name = "`user`")  
@NamedQuery(name = "User.findByTheUsersName", query = "from User u where u.username = ?1")  
public class User {  
  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private Long id;  
  
    @Column(nullable = false)  
    private String username;  
  
}
``` 

下方為註冊檔設定
```pom.xml
<dependency>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-data-jpa</artifactId>  
</dependency>

<dependency>  
    <groupId>org.postgresql</groupId>  
    <artifactId>postgresql</artifactId>  
    <scope>runtime</scope>  
</dependency>

<dependency>  
    <groupId>org.postgresql</groupId>  
    <artifactId>postgresql</artifactId>  
    <scope>runtime</scope>  
</dependency>

```


```application.properties
spring.datasource.url=jdbc:postgresql://localhost:5678/mydb
spring.datasource.username=postgres  
spring.datasource.password=postgres  
spring.jpa.show-sql=true  
spring.jpa.properties.hibernate.format_sql=true  

spring.jpa.hibernate.ddl-auto=create 
//create: 創建新的資料覆蓋舊的
//create-drop: session 結束的時候，會刪除表格

//下方兩個會自動判定，不寫也沒關係
spring.datasource.driver-class-name=org.postgresql.Driver
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.PostgreSQLDialect  

```

##### 架構分析
1. Impl CrudRepository 不夠用，需要新增方法的時候，多一層繼承介面。
2. 


[Office_SimpleJpaRepository_Doc](https://docs.spring.io/spring-data/data-jpa/docs/current/api/org/springframework/data/jpa/repository/support/SimpleJpaRepository.html)


###### Notice:
1. SimpleJpaRepository is a class not an interface
2. No constructor can be inheritted, but can construct through super class 
