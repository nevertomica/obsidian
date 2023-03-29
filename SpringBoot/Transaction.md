[[AOP]]

變更DB 的行為就是一個交易(Transaction)，
就必須要標註 @Transactional 。

Spring 透過管理 AOP 管理 Transaction(變更資料庫的行為)，
凡事要代管的方法就用 @Transactional 標註，如果方法沒有出現例外，
AOP 會commit ，但途中出現意外，AOP 會回滾交易，資料回覆變更之前狀態。



@Transactional(rollbackfor=Exception.class) : 拋出 Exception 
回滾

＠Transactional(readOnly=true):  如果執行讀以外的行為，就會回滾



@Transactional official doc
https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/transaction/annotation/Transactional.html