再導入 Spring Data Mongo 的問題時候，遇到一個找不到 MongoTemplate 的 Bean ，
這是因為 SpringBootApplication(exclude = MongoConfiguration.class) 阻礙了這個 Bean 的生成 ，那之所以會加上這個 exclude 是因為 Mongo Socket Open Exception,
但只是將問題遮住，造成連不上 Mongo 的主因是 SpringApplication 連不上 Mongo Container (Container 並沒有對外開放 Port ) ，所以application.properties 寫上 mongo.port ，也連不上去。

只要在 docker compose yaml 裡頭寫上 ports ，這樣 application 就能透過 localhost: port 打進去 container ， 連上 MongoDB 。

