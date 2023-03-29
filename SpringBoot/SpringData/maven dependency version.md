maven pom.xml dependency 必須填寫 version ，以下 spring-boot-starter-data-jpa 之所以可以不需要version，是因為 org.springframework 已經透過 dependency manager 把 version 做統一整合了。

```
<dependencies> 	 
	 <dependency>  
	    <groupId>org.springframework.boot</groupId>  
	    <artifactId>spring-boot-starter-data-jpa</artifactId>  
	 </dependency>
 </dependencies>
```