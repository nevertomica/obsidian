
##### custom 範例

自定義就是透過 @PersistenceContext 去注入 EntityManager 去設計自己的 
crud 。

另一方面也可以去實作介面  CrudRepository<T, ID>  所條列的方法，也可以在實作之餘，
加入自己的方法，方法必須按照一些 JPA 的一些規範 。



---

##### customall


CrudRepository

@NamedQuery 
@Targer(value=TYPE)
TYPE: class, interface, enum

@PersistentContext 注入 EntityManager , 
EntityManager 調用 @Entity, 
Entity 上面有標註 ＠NamedQuery, 
EntityManager createNamedQuery(String name, T)
Query 可以回傳 List<T> or T
