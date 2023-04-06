檢查參數的 Hibernate Validator 會檢查哪些項目

1.  空值檢查：@NotNull、@NotEmpty、@NotBlank 等。
2.  數值檢查：@Min、@Max、@DecimalMin、@DecimalMax、@Digits 等。
3.  字符串檢查：@Size、@Length、@Pattern 等。
4.  日期時間檢查：@Past、@Future、@PastOrPresent、@FutureOrPresent、@DateTimeFormat 等。
5.  其他檢查：@AssertTrue、@AssertFalse、@Email、@URL 等。


需要額外補上兩個注入
1. validator-api (Specification layer)
2. hibernate-validator(Implementation Layer)