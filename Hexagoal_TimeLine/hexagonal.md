#### 找到六角形架構的第一個範例

注意要替換 mongodb.uri 之中 mongodb atlas 的連結
https://github.com/nevertomica/Hexagonal-Architecture-DDD

公有雲上面的MongoDB 有兩類，一種是由第三方去支援，
另一種則是由 MongoDB 管理。

~~處理 angent 跑設定問題－－

✓ Mongodb atlas  權限問題，改起 Mongodb Container
✗ 串接mongo container
```
缺少 排除MongoAutoConfiguration.class,
還有bean 註冊
```
可能需要改寫repository層的code,  參照 mongo 官方文件來
https://www.mongodb.com/compatibility/spring-boot

###### 下一步方向
要解決例外讓專案跑起來比想像中費時，且已經卡住。
不如再認識六角型架構的精神下，去抽離裡頭的內容，做認知學習。
故改以這個方向為重點。

---

##### 兩面：
application core: 業務邏輯和領域層
adapter

##### 四層：
###### domain-layer
domain-layer:
port : input/output to core, 從 database 進來 domain-layer 就是一種 input
service: 這和 MVC 下面的 service 不太一樣，商業邏輯很單一

###### infrastructure-layer
adaptor: 所有 port 的 implements

###### application-layer
串接的開口，埋在這個地方

###### common-layer
常數, 自定義例外

參考:
https://medium.com/idealo-tech-blog/hexagonal-ports-adapters-architecture-e3617bcf00a0


從範例中學習：
application core 之中的 


---

### 實作

建立一個可以連通mongo的空專案，將 hexagonal 的範例轉移到該空專案。
轉移的中心在 domain, infrastructure 這兩層。


---


