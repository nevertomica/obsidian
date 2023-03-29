

JDBC 之中要訪問 DB 需要寫連線，移動指標很多模板化的程式碼，
JPA 就是這一部分的介面化，再交由其他廠商去做實作。
常見的JPA 實作，Hibernate, EclipseLink , etc.

JPA 是訪問DB 的介面，存在於 java Entity 和 DB 的那一層 。
![[Pasted image 20230325104630.png]]

簡單來說， JPA 是連接 DB 和 Service 之間的 Bridge 。