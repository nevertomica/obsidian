Lombok:
@Data: Getter/Setter, RequiredArgConstructor, EquaslAndHashCode
@Builder

@JsonInclude(JsonInclude.Include.NON_NULL)
如果標注在class 上面，那就是全屬性都要按照這個，才能序列化

----

Controller Layer:
@Valid : 採用Hibernate Validator 檢查參數
使用場景: 物件屬性會標示，Hibernate Validator 支援的屬性檢查，
但引入Controller 做為參數，得透過 @Valid 來開啟 Validator 的檢查

[[HibernateValidator]]

@ResponseStatus marks a method or exception class with the status code and reason message that should be returned