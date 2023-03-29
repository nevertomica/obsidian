- 決定DB , 完成 SpringBoot DB configuration
- 建立一個 Entity
- 建立 Spring Boot JPA(**Repository Layer**)
- 建立 Service Layer
- 建立 Controller Layer


chatGPT 提供 JPARepository ， 補齊 OpenAPI 3 之後，將範例改成 SimpleJPARepository 。
OpenAPI 3 遇到的問題就是， Spring Boot 3 pom.xml 和 Spring Boot 2 完全不同。

改成 SimpleJPARepository 遇到的第一個問題是建構子。
第二層遇到的問題是，GPT 的範例，雖有定義 Service層，但在Controller 卻沒有調用。
如果先不看這個問題，也會出現 `Parameter 0 of constructor in com.example.jparepository.UserSimpleJPARepository required a bean of type java.lang.Class' that could not be found. 的例外。

jpa 工作原理
https://blog.csdn.net/andy_zhang2007/article/details/84064862

@Autowired 的幾種方式
https://blog.csdn.net/zhangjingao/article/details/81094529

Spring boot 自動配置
https://blog.csdn.net/andy_zhang2007/category_9291852.html