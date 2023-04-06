Lombok:
@Data: Getter/Setter, RequiredArgConstructor, EquaslAndHashCode
@Builder

@JsonInclude(JsonInclude.Include.NON_NULL)
如果標注在class 上面，那就是全屬性都要按照這個，才能序列化

----

Controller Layer:
@Valid : 採用Hibernate Validator 檢查參數

